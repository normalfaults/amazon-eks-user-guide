# Observability in Amazon EKS<a name="eks-observe"></a>

You can observe your data in Amazon EKS using many available monitoring or logging tools\. With a Fargate log router configured, your Amazon EKS log data can be streamed to AWS services or to partner tools to for data analysis\. These AWS services are available in the AWS Management Console\. You can monitor your Amazon EKS resources using Amazon CloudWatch\. This topic describes the available functions and formats in Amazon EKS\. There are many services available in the AWS Management Console that provide data for troubleshooting your Amazon EKS issues\. For an overview of these services, see [AWS Management Console documentation](https://docs.aws.amazon.com/latest/gsg/learn-whats-new.html)\.

You can view cluster health and details by selecting your cluster's name after selecting **Clusters** in the left navigation pane of the Amazon EKS console\. To view details about any existing Kubernetes resources that are deployed to your cluster, see [View Kubernetes resources](view-kubernetes-resources.md)\.

Monitoring is an important part of maintaining the reliability, availability, and performance of Amazon EKS and your AWS solutions\. We recommend that you collect monitoring data from all of the parts of your AWS solution\. That way, you can more easily debug a multi\-point failure if one occurs\. Before you start monitoring Amazon EKS, make sure that a monitoring plan that addresses the following questions\.
+ What are your goals? Do you need real\-time notifications if your clusters scale dramatically?
+ What resources need to be observed?
+ How frequently do you need to observe these resources? Does your company want to respond quickly to risks?
+ What tools do you intend to use? If you already run Fargate as part of your launch, then you can use the built\-in [log router](https://docs.aws.amazon.com/eks/latest/userguide/fargate-logging.html)\.
+ Who you do intend to perform the monitoring tasks?
+ Whom do you want notifications to be sent to when something goes wrong?

## Logging and monitoring in Amazon EKS<a name="logging-monitoring"></a>

Amazon EKS provides built\-in tools for logging and monitoring\. You can choose your logging level which starts at the control plane\. Control plane logging records all API calls to your clusters, audit information capturing what users performed what actions to your clusters, as well as role\-based logs\.

Amazon EKS control plane logging provides audit and diagnostic logs directly from the Amazon EKS control plane to CloudWatch Logs in your account\. These logs make it easy for you to secure and run your clusters\. You can select the exact log types you need, and logs are sent as log streams to a group for each Amazon EKS cluster in CloudWatch\. For more information, see [Amazon EKS Control Plane Logging](control-plane-logs.md) and [Amazon CloudWatch logging](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html)\.

**Note**  
When you check the Amazon EKS authenticator logs in Amazon CloudWatch, the entries are displayed that contain text similar to the following example text\.  

```
level=info msg="mapping IAM role" groups="[]" role="arn:aws:iam::<111122223333:>role/<XXXXXXXXXXXXXXXXXX>-NodeManagerRole-<XXXXXXXX>" username="eks:node-manager"
```
Entries that contain this text are expected\. The `username` is an Amazon EKS internal service role that performs specific operations for managed node groups and Fargate\.  
For low\-level, customizable logging, then [Kubernetes logging](https://kubernetes.io/docs/concepts/cluster-administration/logging/) is available\.

Amazon EKS is integrated with AWS CloudTrail, a service that provides a record of actions taken by a user, role, or an AWS service in Amazon EKS\. CloudTrail captures all API calls for Amazon EKS as events\. The calls captured include calls from the Amazon EKS console and code calls to the Amazon EKS API operations\. For more information, see [Logging Amazon EKS API calls with AWS CloudTrail](logging-using-cloudtrail.md)\.

The Kubernetes API server exposes a number of metrics that are useful for monitoring and analysis\. For more information, see [Control plane metrics with Prometheus](prometheus.md)\.

To configure Fluent Bit for custom Amazon CloudWatch logs, see [Set up Fluent Bit as a DaemonSet to send logs to Amazon CloudWatch Logs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Container-Insights-setup-logs-FluentBit.html) in the Amazon CloudWatch user guide\.

## Amazon EKS logging and monitoring tools<a name="eks_monitor_tools"></a>

Amazon Web Services provides various tools that you can use to monitor Amazon EKS\. You can configure some tools to set up automatic monitoring, but some require manual calls\. We recommend that you automate monitoring tasks as much as your environment and existing toolset allows\.


**Logging**  

| Areas | Tool | Logs | Setup | 
| --- | --- | --- | --- | 
| Applications | [Amazon CloudWatch Container Insights](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/cloudwatch-container-insights.html) |  It collects, aggregates, and summarizes metrics and logs from your containerized applications and microservices\.  |  [Setup procedure](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/deploy-container-insights-ECS-cluster.html) To set up Amazon CloudWatch Container Insights logging for ADOT, use [this procedure](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Container-Insights-EKS-otel.html)\.  | 
| Containers | [AWS Fargate](https://docs.aws.amazon.com/eks/latest/userguide/fargate-logging.html) |  It provides compute capacity for containers, including resource usage\.  |  [Setup procedure](https://docs.aws.amazon.com/eks/latest/userguide/fargate-getting-started.html)  | 
|  Control plane  |  [Prometheus](https://docs.aws.amazon.com/eks/latest/userguide/prometheus.html)  |  CloudWatch Logs ingestion, archive storage, and data scanning rates apply to enabled control plane logs\.  | [Setup procedure](https://prometheus.io/) | 
| Control plane | [AWS CloudTrail](https://docs.aws.amazon.com/eks/latest/userguide/logging-using-cloudtrail.html) | It logs API calls by a user, role, or service\. | [Setup procedure](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail.html) | 
|  Multiple areas  | Fargate log router |  It streams logs to AWS services or partner tools\. Uses [AWS for Fluent Bit](https://github.com/aws/aws-for-fluent-bit)\. Logs can be streamed to other AWS services or partner tools\.  | [Setup procedure](https://docs.aws.amazon.com/eks/latest/userguide/fargate-logging.html) | 


**Monitoring**  

| Areas | Tool | Logs | Setup | 
| --- | --- | --- | --- | 
|  Applications  | [Amazon CloudWatch Container Insights](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/cloudwatch-container-insights.html) |  Amazon CloudWatch Container Insights collects, aggregates, and summarizes metrics and logs from your containerized applications and microservices\.  |  [Setup procedure for the AWS Management Console](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/deploy-container-insights-ECS-cluster.html)  | 
| Applications | [AWS Distro for OpenTelemetry \(ADOT\)](https://aws-otel.github.io/docs/introduction) |  It collects and sends correlated metrics, trace data, and metadata to AWS monitoring services or partners\. It can be set up through Amazon CloudWatch Container Insights\.  |  [Setup procedure](https://docs.aws.amazon.com/eks/latest/userguide/opentelemetry.html)  | 
| Applications | [Amazon DevOps Guru](https://aws.amazon.com/about-aws/whats-new/2021/11/amazon-devops-guru-coverage-amazon-eks-metrics-cluster/) | It detects node\-level operational performance and availability\. | Enable [Amazon CloudWatch Container Insights](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/deploy-container-insights-EKS.html) | 
| Applications | [AWS X\-Ray](https://docs.aws.amazon.com/xray/latest/devguide/aws-xray.html) |  It receives trace data about your application\. This trace data includes ingoing and outgoing requests and metadata about the requests\. For Amazon EKS, the implementation requires the OpenTelemetry add\-on\.  | [Setup procedure](https://docs.aws.amazon.com/xray/latest/devguide/xray-instrumenting-your-app.html) | 
| Cluster | [Amazon CloudWatch](https://docs.aws.amazon.com/eks/latest/developerguide/cloudwatch-metrics.html) |  It logs cluster resources\.  | n/a | 
| Containers | [AWS Fargate](https://docs.aws.amazon.com/eks/latest/userguide/fargate-logging.html) |  It provides compute capacity for containers, including resource usage\.  |  [Setup procedure](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/deploy-container-insights-ECS-cluster.html)  | 