# Creating the Amazon EBS CSI driver IAM role for service accounts<a name="csi-iam-role"></a>

The Amazon EBS CSI plugin requires IAM permissions to make calls to AWS APIs on your behalf\. For more information, see [Set up driver permission](https://github.com/kubernetes-sigs/aws-ebs-csi-driver/tree/master/docs#set-up-driver-permission) on GitHub\.

When the plugin is deployed, it creates and is configured to use a service account that's named `ebs-csi-controller-sa`\. The service account is bound to a Kubernetes `clusterrole` that's assigned the required Kubernetes permissions\.

**Note**  
No matter if you configure the Amazon EBS CSI plugin to use IAM roles for service accounts, the pods have access to the permissions that are assigned to the IAM role\. This is the case except when you block access to IMDS\. For more information, see [Security best practices for Amazon EKS](security-best-practices.md)\.

**Prerequisites**
+ An existing cluster that's version `1.18` or later\.
  + 1\.18 requires eks\.9 or later\.
  + 1\.19 requires eks\.7 or later\.
  + 1\.20 requires eks\.3 or later\.
  + 1\.21 requires eks\.3 or later\.
+ An existing AWS Identity and Access Management \(IAM\) OpenID Connect \(OIDC\) provider for your cluster\. To determine whether you already have one, or to create one, see [Create an IAM OIDC provider for your cluster](enable-iam-roles-for-service-accounts.md)\.

Create an IAM role and attach the required AWS managed policy to it\. You can use `eksctl`, the AWS Management Console, or the AWS CLI\.

------
#### [ eksctl ]

**To create your Amazon EBS CSI plugin IAM role with `eksctl`**

1. Create an IAM role and attach the required AWS managed policy with the following command\. Replace *`my-cluster`* with the name of your cluster\. The command deploys an AWS CloudFormation stack that creates an IAM role, attaches the IAM policy to it, and annotates the existing `ebs-csi-controller-sa` service account with the Amazon Resource Name \(ARN\) of the IAM role\. If your cluster is in the AWS GovCloud \(US\-East\) or AWS GovCloud \(US\-East\) AWS Regions, then replace `arn:aws:` with `arn:aws-us-gov:` before running the following command\. 

   ```
   eksctl create iamserviceaccount \
     --name ebs-csi-controller-sa \
     --namespace kube-system \
     --cluster my-cluster \
     --attach-policy-arn arn:aws:iam::aws:policy/service-role/AmazonEBSCSIDriverPolicy \
     --approve \
     --role-only \
     --role-name AmazonEKS_EBS_CSI_DriverRole
   ```

1. If you use a custom KMS key for encryption on your Amazon EBS volumes, customize the IAM role as needed\. For example, do the following:

   1. Copy and paste the following code into a new `kms-key-for-encryption-on-ebs.json` file\. Replace `custom-key-id` with the custom KMS key ID\.

      ```
      {
        "Version": "2012-10-17",
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "kms:CreateGrant",
              "kms:ListGrants",
              "kms:RevokeGrant"
            ],
            "Resource": ["custom-key-id"],
            "Condition": {
              "Bool": {
                "kms:GrantIsForAWSResource": "true"
              }
            }
          },
          {
            "Effect": "Allow",
            "Action": [
              "kms:Encrypt",
              "kms:Decrypt",
              "kms:ReEncrypt*",
              "kms:GenerateDataKey*",
              "kms:DescribeKey"
            ],
            "Resource": ["custom-key-id"]
          }
        ]
      }
      ```

   1. Create the policy\. You can change `KMS_Key_For_Encryption_On_EBS_Policy` to a different name\. However, if you do, make sure to change it in later steps, too\.

      ```
      aws iam create-policy \
        --policy-name KMS_Key_For_Encryption_On_EBS_Policy \
        --policy-document file://kms-key-for-encryption-on-ebs.json
      ```

   1. Attach the IAM policy to the role\. Replace `111122223333` with your account ID\. If your cluster is in the AWS GovCloud \(US\-East\) or AWS GovCloud \(US\-East\) AWS Regions, then replace `arn:aws:` with `arn:aws-us-gov:` before running the following command\.

      ```
      aws iam attach-role-policy \
        --policy-arn arn:aws:iam::111122223333:policy/KMS_Key_For_Encryption_On_EBS_Policy \
        --role-name AmazonEKS_EBS_CSI_DriverRole
      ```

------
#### [ AWS Management Console ]

**To create your Amazon EBS CSI plugin IAM role with the AWS Management Console**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the left navigation pane, choose **Roles**\.

1. On the **Roles** page, choose **Create role**\.

1. On the **Select trusted entity** page, do the following:

   1. In the **Trusted entity type** section, choose **Web identity**\.

   1. For **Identity provider**, choose the **OpenID Connect provider URL** for your cluster \(as shown under **Overview** in Amazon EKS\)\.

   1. For **Audience**, choose `sts.amazonaws.com`\.

   1. Choose **Next**\.

1. On the **Add permissions** page, do the following:

   1. In the **Filter policies** box, enter `AmazonEBSCSIDriverPolicy`\.

   1. Select the check box to the left of the `AmazonEBSCSIDriverPolicy` returned in the search\.

   1. Choose **Next**\.

1. On the **Name, review, and create** page, do the following:

   1. For **Role name**, enter a unique name for your role, such as ***AmazonEKS\_EBS\_CSI\_DriverRole***\.

   1. Under **Add tags \(Optional\)**, add metadata to the role by attaching tags as key–value pairs\. For more information about using tags in IAM, see [Tagging IAM Entities](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_tags.html) in the *IAM User Guide*

   1. Choose **Create role**\.

1. After the role is created, choose the role in the console to open it for editing\.

1. Choose the **Trust relationships** tab, and then choose **Edit trust policy**\.

1. Find the line that looks similar to the following line:

   ```
   "oidc.eks.region-code.amazonaws.com/id/EXAMPLED539D4633E53DE1B71EXAMPLE:aud": "sts.amazonaws.com"
   ```

   Add a comma to the end of the previous line, and then add the following line after the previous line\. Replace `region-code` with the AWS Region that your cluster is in\. Replace `EXAMPLED539D4633E53DE1B71EXAMPLE` with your cluster's OIDC provider ID\.

   ```
   "oidc.eks.region-code.amazonaws.com/id/EXAMPLED539D4633E53DE1B71EXAMPLE:sub": "system:serviceaccount:kube-system:ebs-csi-controller-sa"
   ```

1. Choose **Update policy** to finish\.

1. If you use a custom KMS key for encryption on your Amazon EBS volumes, customize the IAM role as needed\. For example, do the following:

   1. In the left navigation pane, choose **Policies**\.

   1. On the **Policies** page, choose **Create Policy**\.

   1. On the **Create policy** page, choose the **JSON** tab\.

   1. Copy and paste the following code into the editor, replacing `custom-key-id` with the custom KMS key ID:

      ```
      {
        "Version": "2012-10-17",
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "kms:CreateGrant",
              "kms:ListGrants",
              "kms:RevokeGrant"
            ],
            "Resource": ["custom-key-id"],
            "Condition": {
              "Bool": {
                "kms:GrantIsForAWSResource": "true"
              }
            }
          },
          {
            "Effect": "Allow",
            "Action": [
              "kms:Encrypt",
              "kms:Decrypt",
              "kms:ReEncrypt*",
              "kms:GenerateDataKey*",
              "kms:DescribeKey"
            ],
            "Resource": ["custom-key-id"]
          }
        ]
      }
      ```

   1. Choose **Next: Tags**\.

   1. On the **Add tags \(Optional\)** page, choose **Next: Review**\.

   1. For **Name**, enter a unique name for your policy \(for example, ***KMS\_Key\_For\_Encryption\_On\_EBS\_Policy***\)\.

   1. Choose **Create policy**\.

   1. In the left navigation pane, choose **Roles**\.

   1. Choose the ***AmazonEKS\_EBS\_CSI\_DriverRole*** in the console to open it for editing\.

   1. From the **Add permissions** drop\-down list, choose **Attach policies**\.

   1. In the **Filter policies** box, enter `KMS_Key_For_Encryption_On_EBS_Policy`\.

   1. Select the check box to the left of the `KMS_Key_For_Encryption_On_EBS_Policy` that was returned in the search\.

   1. Choose **Attach policies**\.

------
#### [ AWS CLI ]

**To create your Amazon EBS CSI plugin IAM role with the AWS CLI**

1. View your cluster's OIDC provider URL\. Replace `my-cluster` with your cluster name\. If the output from the command is `None`, review the **Prerequisites**\.

   ```
   aws eks describe-cluster \
     --name my-cluster \
     --query "cluster.identity.oidc.issuer" \
     --output text
   ```

   The example output is as follows\.

   ```
   https://oidc.eks.region-code.amazonaws.com/id/EXAMPLED539D4633E53DE1B71EXAMPLE
   ```

1. Create the IAM role\.

   1. Copy the following contents to a file that's named `aws-ebs-csi-driver-trust-policy.json`\. Replace `111122223333` with your account ID, `region-code` with your AWS Region, and `EXAMPLED539D4633E53DE1B71EXAMPLE` with the value that was returned in the previous step\. If your cluster is in the AWS GovCloud \(US\-East\) or AWS GovCloud \(US\-East\) AWS Regions, then replace `arn:aws:` with `arn:aws-us-gov:`\.

      ```
      {
        "Version": "2012-10-17",
        "Statement": [
          {
            "Effect": "Allow",
            "Principal": {
              "Federated": "arn:aws:iam::111122223333:oidc-provider/oidc.eks.region-code.amazonaws.com/id/EXAMPLED539D4633E53DE1B71EXAMPLE"
            },
            "Action": "sts:AssumeRoleWithWebIdentity",
            "Condition": {
              "StringEquals": {
                "oidc.eks.region-code.amazonaws.com/id/EXAMPLED539D4633E53DE1B71EXAMPLE:aud": "sts.amazonaws.com",
                "oidc.eks.region-code.amazonaws.com/id/EXAMPLED539D4633E53DE1B71EXAMPLE:sub": "system:serviceaccount:kube-system:ebs-csi-controller-sa"
              }
            }
          }
        ]
      }
      ```

   1. Create the role\. You can change `AmazonEKS_EBS_CSI_DriverRole` to a different name\. If you change it, make sure to change it in later steps\.

      ```
      aws iam create-role \
        --role-name AmazonEKS_EBS_CSI_DriverRole \
        --assume-role-policy-document file://"aws-ebs-csi-driver-trust-policy.json"
      ```

1. Attach the required AWS managed policy to the role\. If your cluster is in the AWS GovCloud \(US\-East\) or AWS GovCloud \(US\-East\) AWS Regions, then replace `arn:aws:` with `arn:aws-us-gov:` before running the following command\.

   ```
   aws iam attach-role-policy \
     --policy-arn arn:aws:iam::aws:policy/service-role/AmazonEBSCSIDriverPolicy \
     --role-name AmazonEKS_EBS_CSI_DriverRole
   ```

1. If you use a custom KMS key for encryption on your Amazon EBS volumes, customize the IAM role as needed\. For example, do the following:

   1. Copy and paste the following code into a new `kms-key-for-encryption-on-ebs.json` file\. Replace `custom-key-id` with the custom KMS key ID\.

      ```
      {
        "Version": "2012-10-17",
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "kms:CreateGrant",
              "kms:ListGrants",
              "kms:RevokeGrant"
            ],
            "Resource": ["custom-key-id"],
            "Condition": {
              "Bool": {
                "kms:GrantIsForAWSResource": "true"
              }
            }
          },
          {
            "Effect": "Allow",
            "Action": [
              "kms:Encrypt",
              "kms:Decrypt",
              "kms:ReEncrypt*",
              "kms:GenerateDataKey*",
              "kms:DescribeKey"
            ],
            "Resource": ["custom-key-id"]
          }
        ]
      }
      ```

   1. Create the policy\. You can change `KMS_Key_For_Encryption_On_EBS_Policy` to a different name\. However, if you do, make sure to change it in later steps, too\.

      ```
      aws iam create-policy \
        --policy-name KMS_Key_For_Encryption_On_EBS_Policy \
        --policy-document file://kms-key-for-encryption-on-ebs.json
      ```

   1. Attach the IAM policy to the role\. Replace `111122223333` with your account ID\. If your cluster is in the AWS GovCloud \(US\-East\) or AWS GovCloud \(US\-East\) AWS Regions, then replace `arn:aws:` with `arn:aws-us-gov:` before running the following command\.

      ```
      aws iam attach-role-policy \
        --policy-arn arn:aws:iam::111122223333:policy/KMS_Key_For_Encryption_On_EBS_Policy \
        --role-name AmazonEKS_EBS_CSI_DriverRole
      ```

------