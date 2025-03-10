# Amazon EKS optimized Windows AMI versions<a name="eks-ami-versions-windows"></a>

This topic lists versions of the Amazon EKS optimized Windows AMIs and their corresponding versions of `kubelet`, Docker, containerd, and `csi-proxy`\.

The Amazon EKS optimized AMI metadata, including the AMI ID, for each variant can be retrieved programmatically\. For more information, see [Retrieving Amazon EKS optimized Windows AMI IDs](retrieve-windows-ami-id.md)\.

AMIs are versioned by Kubernetes version and the release date of the AMI in the following format:

```
k8s_major_version.k8s_minor_version-release_date
```

## Amazon EKS optimized Windows Server 20H2 Core AMI<a name="eks-ami-versions-windows-20h2-core"></a>

The tables below list the current and previous versions of the Amazon EKS optimized Windows AMI\.

------
#### [ Kubernetes version 1\.22 ]


**Kubernetes version `1.22`**  

| AMI version | `kubelet` version | Docker version | `containerd` version | `csi-proxy` version | 
| --- | --- | --- | --- | --- | 
| 1\.22\-2022\.04\.14 | 1\.22\.6 | 20\.10\.9 | 1\.6\.2 | 1\.1\.1 | 

------
#### [ Kubernetes version 1\.21 ]


**Kubernetes version `1.21`**  

| AMI version | `kubelet` version | Docker version | `containerd` version | `csi-proxy` version | 
| --- | --- | --- | --- | --- | 
| 1\.21\.2022\.04\.14 | 1\.21\.5 | 20\.10\.9 | 1\.62 | 1\.1\.1 | 
| 1\.21\.2022\.03\.10 | 1\.21\.5 | 20\.10\.9 | 1\.61 | N/A | 
| 1\.21\.2022\.02\.23 | 1\.21\.5 | 20\.10\.9 | N/A | N/A | 
| 1\.21\.2022\.01\.18 | 1\.21\.5 | 20\.10\.9 | N/A | N/A | 
| 1\.21\.2021\.12\.21 | 1\.21\.5 | 20\.10\.8 | N/A | N/A | 
| 1\.21\-2021\.11\.10 | 1\.21\.4 | 20\.10\.7 | N/A | N/A | 
| 1\.21\-2021\.10\.14 | 1\.21\.4 | 20\.10\.7 | N/A | N/A | 
| 1\.21\-2021\.09\.16 | 1\.21\.2 | 20\.10\.7 | N/A | N/A | 
| 1\.21\-2021\.08\.12 | 1\.21\.2 | 20\.10\.6 | N/A | N/A | 

------

## Amazon EKS optimized Windows Server 2019 Core AMI<a name="eks-ami-versions-windows-2019-core"></a>

The tables below list the current and previous versions of the Amazon EKS optimized Windows AMI\.

------
#### [ Kubernetes version 1\.22 ]


**Kubernetes version `1.22`**  

| AMI version | `kubelet` version | Docker version | `containerd` version | `csi-proxy` version | 
| --- | --- | --- | --- | --- | 
| 1\.22\-2022\.04\.14 | 1\.22\.6 | 20\.10\.9 | 1\.6\.2 | 1\.1\.1 | 

------
#### [ Kubernetes version 1\.21 ]


**Kubernetes version `1.21`**  

| AMI version | `kubelet` version | Docker version | `containerd` version | `csi-proxy` version | 
| --- | --- | --- | --- | --- | 
| 1\.21\-2022\.04\.14 | 1\.21\.5 | 20\.10\.9 | 1\.62 | 1\.1\.1 | 
| 1\.21\.2021\.03\.10 | 1\.21\.5 | 20\.10\.9 | 1\.61 | N/A | 
| 1\.21\.2022\.02\.23 | 1\.21\.5 | 20\.10\.9 | N/A | N/A | 
| 1\.21\.2022\.01\.18 | 1\.21\.5 | 20\.10\.9 | N/A | N/A | 
| 1\.21\.2021\.12\.21 | 1\.21\.5 | 20\.10\.8 | N/A | N/A | 
| 1\.21\-2021\.10\.14 | 1\.21\.4 | 20\.10\.7 | N/A | N/A | 
| 1\.21\-2021\.11\.10 | 1\.21\.4 | 20\.10\.7 | N/A | N/A | 
| 1\.21\-2021\.09\.16 | 1\.21\.2 | 20\.10\.7 | N/A | N/A | 
| 1\.21\-2021\.08\.12 | 1\.21\.2 | 20\.10\.6 | N/A | N/A | 

------
#### [ Kubernetes version 1\.20 ]


**Kubernetes version `1.20`**  

| AMI version | `kubelet` version | Docker version | `csi-proxy` version | 
| --- | --- | --- | --- | 
| 1\.20\-2022\.04\.14 | 1\.20\.11 | 20\.10\.9 | 1\.1\.1 | 
| 1\.20\-2022\.03\.10 | 1\.20\.11 | 20\.10\.9 | N/A | 
| 1\.20\-2022\.02\.23 | 1\.20\.11 | 20\.10\.9 | N/A | 
| 1\.20\-2022\.01\.8 | 1\.20\.11 | 20\.10\.9 | N/A | 
| 1\.20\-2021\.12\.21 | 1\.20\.11 | 20\.10\.8 | N/A | 
| 1\.20\-2021\.11\.10 | 1\.20\.10 | 20\.10\.7 | N/A | 
| 1\.20\-2021\.10\.14 | 1\.20\.10 | 20\.10\.7 | N/A | 
| 1\.20\-2021\.09\.16 | 1\.20\.7 | 20\.10\.7 | N/A | 
| 1\.20\-2021\.08\.12 | 1\.20\.4 | 20\.10\.6 | N/A | 
| 1\.20\-2021\.07\.14 | 1\.20\.4 | 20\.10\.6 | N/A | 
| 1\.20\-2021\.06\.16 | 1\.20\.4 | 20\.10\.5 | N/A | 
| 1\.20\-2021\.05\.18 | 1\.20\.4 | 20\.10\.4 | N/A | 

------
#### [ Kubernetes version 1\.19 ]


**Kubernetes version `1.19`**  

| AMI version | `kubelet` version | Docker version | `csi-proxy` version | 
| --- | --- | --- | --- | 
| 1\.19\-2022\.04\.14 | 1\.19\.15 | 20\.10\.9 | 1\.1\.1 | 
| 1\.19\-2022\.03\.10 | 1\.19\.15 | 20\.10\.9 | N/A | 
| 1\.19\-2022\.02\.23 | 1\.19\.15 | 20\.10\.9 | N/A | 
| 1\.19\-2022\.01\.18 | 1\.19\.15 | 20\.10\.9 | N/A | 
| 1\.19\-2021\.12\.21 | 1\.19\.15 | 20\.10\.8 | N/A | 
| 1\.19\-2021\.11\.10 | 1\.19\.14 | 20\.10\.7 | N/A | 
| 1\.19\-2021\.10\.14 | 1\.19\.14 | 20\.10\.7 | N/A | 
| 1\.19\-2021\.09\.16 | 1\.19\.13 | 20\.10\.7 | N/A | 
| 1\.19\-2021\.08\.12 | 1\.19\.8 | 20\.10\.6 | N/A | 
| 1\.19\-2021\.07\.14 | 1\.19\.8 | 20\.10\.6 | N/A | 
| 1\.19\-2021\.06\.16 | 1\.19\.8 | 20\.10\.5 | N/A | 
| 1\.19\-2021\.05\.18 | 1\.19\.8 | 20\.10\.4 | N/A | 
| 1\.19\-2021\.04\.14 | 1\.19\.6 | 20\.10\.0 | N/A | 
| 1\.19\-2021\.03\.10 | 1\.19\.6 | 19\.03\.14 | N/A | 
| 1\.19\-2021\.02\.18 | 1\.19\.6 | 19\.03\.14 | N/A | 

------
#### [ Kubernetes version 1\.18 ]


**Kubernetes version `1.18`**  

| AMI version | `kubelet` version | Docker version | `csi-proxy` version | 
| --- | --- | --- | --- | 
| 1\.18\-2022\.03\.10 | 1\.18\.20 | 20\.10\.9 | 1\.1\.1 | 
| 1\.18\-2022\.02\.23 | 1\.18\.20 | 20\.10\.9 | N/A | 
| 1\.18\-2022\.01\.18 | 1\.18\.20 | 20\.10\.9 | N/A | 
| 1\.18\-2021\.12\.21 | 1\.18\.20 | 20\.10\.8 | N/A | 
| 1\.18\-2021\.11\.10 | 1\.18\.20 | 20\.10\.7 | N/A | 
| 1\.18\-2021\.10\.14 | 1\.18\.20 | 20\.10\.7 | N/A | 
| 1\.18\-2021\.09\.16 | 1\.18\.20 | 20\.10\.7 | N/A | 
| 1\.18\-2021\.08\.12 | 1\.18\.16 | 20\.10\.6 | N/A | 
| 1\.18\-2021\.07\.14 | 1\.18\.16 | 20\.10\.6 | N/A | 
| 1\.18\-2021\.06\.16 | 1\.18\.16 | 20\.10\.5 | N/A | 
| 1\.18\-2021\.05\.18 | 1\.18\.16 | 20\.10\.4 | N/A | 
| 1\.18\-2021\.04\.14 | 1\.18\.9 | 20\.10\.0 | N/A | 
| 1\.18\-2021\.03\.10 | 1\.18\.9 | 19\.03\.14 | N/A | 
| 1\.18\-2021\.02\.10 | 1\.18\.9 | 19\.03\.14 | N/A | 
| 1\.18\-2021\.01\.13 | 1\.18\.9 | 19\.03\.14 | N/A | 
| 1\.18\-2020\.12\.11 | 1\.18\.9 | 19\.03\.13 | N/A | 
| 1\.18\-2020\.11\.12 | 1\.18\.9 | 18\.09\.7 | N/A | 
| 1\.18\-2020\.10\.29 | 1\.18\.8 | 18\.09\.7 | N/A | 
| 1\.18\-2020\.10\.08 | 1\.18\.8 | 18\.09\.7 | N/A | 

------
#### [ Kubernetes version 1\.17 ]

The most recent version is the last version we're releasing for Amazon EKS `1.17` clusters\. It will be available until the `1.17` end of support date\. For more information, see [Amazon EKS Kubernetes release calendar](kubernetes-versions.md#kubernetes-release-calendar)\. For newer AMI releases, update your cluster to a later Kubneretes version\. For more information, see [Updating an Amazon EKS cluster Kubernetes version](update-cluster.md)\.


**Kubernetes version `1.17`**  

| AMI version | `kubelet` version | Docker version | 
| --- | --- | --- | 
| 1\.17\-2021\.08\.12 | 1\.17\.17 | 20\.10\.6 | 
| 1\.17\-2021\.06\.16 | 1\.17\.17 | 20\.10\.5 | 
| 1\.17\-2021\.05\.18 | 1\.17\.17 | 20\.10\.4 | 
| 1\.17\-2021\.04\.14 | 1\.17\.12 | 20\.10\.0 | 
| 1\.17\-2021\.03\.10 | 1\.17\.12 | 19\.03\.14 | 
| 1\.17\-2021\.02\.10 | 1\.17\.12 | 19\.03\.14 | 
| 1\.17\-2021\.01\.13 | 1\.17\.12 | 19\.03\.14 | 
| 1\.17\-2020\.12\.11 | 1\.17\.12 | 19\.03\.13 | 
| 1\.17\-2020\.11\.12 | 1\.17\.12 | 18\.09\.7 | 
| 1\.17\-2020\.10\.29 | 1\.17\.11 | 18\.09\.7 | 
| 1\.17\-2020\.09\.09 | 1\.17\.11 | 18\.09\.7 | 
| 1\.17\-2020\.08\.13 | 1\.17\.9 | 18\.09\.7 | 

------

## Amazon EKS optimized Windows Server 2019 Full AMI<a name="eks-ami-versions-windows-2019-full"></a>

The tables below list the current and previous versions of the Amazon EKS optimized Windows AMI\.

------
#### [ Kubernetes version 1\.22 ]


**Kubernetes version `1.22`**  

| AMI version | `kubelet` version | Docker version | `containerd` version | 
| --- | --- | --- | --- | 
| 1\.22\-2022\.04\.14 | 1\.22\.6 | 20\.10\.9 | 1\.6\.2 | 

------
#### [ Kubernetes version 1\.21 ]


**Kubernetes version `1.21`**  

| AMI version | `kubelet` version | Docker version | `containerd` version | `csi-proxy` version | 
| --- | --- | --- | --- | --- | 
| 1\.21\.2022\.04\.14 | 1\.21\.5 | 20\.10\.9 | 1\.6\.2 | 1\.1\.1 | 
| 1\.21\.2022\.03\.10 | 1\.21\.5 | 20\.10\.9 | 1\.6\.1 | N/A | 
| 1\.21\.2022\.02\.23 | 1\.21\.5 | 20\.10\.9 | N/A | N/A | 
| 1\.21\.2022\.01\.18 | 1\.21\.5 | 20\.10\.9 | N/A | N/A | 
| 1\.21\.2021\.12\.21 | 1\.21\.5 | 20\.10\.8 | N/A | N/A | 
| 1\.21\-2021\.11\.10 | 1\.21\.4 | 20\.10\.7 | N/A | N/A | 
| 1\.21\-2021\.10\.14 | 1\.21\.4 | 20\.10\.7 | N/A | N/A | 
| 1\.21\-2021\.09\.16 | 1\.21\.2 | 20\.10\.7 | N/A | N/A | 
| 1\.21\-2021\.08\.12 | 1\.21\.2 | 20\.10\.6 | N/A | N/A | 

------
#### [ Kubernetes version 1\.20 ]


**Kubernetes version `1.20`**  

| AMI version | `kubelet` version | Docker version | `csi-proxy` version | 
| --- | --- | --- | --- | 
| 1\.20\-2022\.04\.14 | 1\.20\.11 | 20\.10\.9 | 1\.1\.1 | 
| 1\.20\-2022\.03\.10 | 1\.20\.11 | 20\.10\.9 | N/A | 
| 1\.20\-2022\.02\.23 | 1\.20\.11 | 20\.10\.9 | N/A | 
| 1\.20\-2022\.01\.8 | 1\.20\.11 | 20\.10\.9 | N/A | 
| 1\.20\-2021\.12\.21 | 1\.20\.11 | 20\.10\.8 | N/A | 
| 1\.20\-2021\.11\.10 | 1\.20\.10 | 20\.10\.7 | N/A | 
| 1\.20\-2021\.10\.14 | 1\.20\.10 | 20\.10\.7 | N/A | 
| 1\.20\-2021\.09\.16 | 1\.20\.7 | 20\.10\.7 | N/A | 
| 1\.20\-2021\.08\.12 | 1\.20\.4 | 20\.10\.6 | N/A | 
| 1\.20\-2021\.07\.14 | 1\.20\.4 | 20\.10\.6 | N/A | 
| 1\.20\-2021\.06\.16 | 1\.20\.4 | 20\.10\.5 | N/A | 
| 1\.20\-2021\.05\.18 | 1\.20\.4 | 20\.10\.4 | N/A | 

------
#### [ Kubernetes version 1\.19 ]


**Kubernetes version `1.19`**  

| AMI version | `kubelet` version | Docker version | `csi-proxy` version | 
| --- | --- | --- | --- | 
| 1\.19\-2022\.04\.14 | 1\.19\.15 | 20\.10\.9 | 1\.1\.1 | 
| 1\.19\-2022\.03\.10 | 1\.19\.15 | 20\.10\.9 | N/A | 
| 1\.19\-2022\.02\.23 | 1\.19\.15 | 20\.10\.9 | N/A | 
| 1\.19\-2022\.01\.18 | 1\.19\.15 | 20\.10\.9 | N/A | 
| 1\.19\-2021\.12\.21 | 1\.19\.15 | 20\.10\.8 | N/A | 
| 1\.19\-2021\.11\.10 | 1\.19\.14 | 20\.10\.7 | N/A | 
| 1\.19\-2021\.10\.14 | 1\.19\.14 | 20\.10\.7 | N/A | 
| 1\.19\-2021\.09\.16 | 1\.19\.13 | 20\.10\.7 | N/A | 
| 1\.19\-2021\.08\.12 | 1\.19\.8 | 20\.10\.6 | N/A | 
| 1\.19\-2021\.07\.14 | 1\.19\.8 | 20\.10\.6 | N/A | 
| 1\.19\-2021\.06\.16 | 1\.19\.8 | 20\.10\.5 | N/A | 
| 1\.19\-2021\.05\.18 | 1\.19\.8 | 20\.10\.4 | N/A | 
| 1\.19\-2021\.04\.14 | 1\.19\.6 | 20\.10\.0 | N/A | 
| 1\.19\-2021\.03\.10 | 1\.19\.6 | 19\.03\.14 | N/A | 
| 1\.19\-2021\.02\.18 | 1\.19\.6 | 19\.03\.14 | N/A | 

------
#### [ Kubernetes version 1\.18 ]


**Kubernetes version `1.18`**  

| AMI version | `kubelet` version | Docker version | `csi-proxy` version | 
| --- | --- | --- | --- | 
| 1\.18\-2022\.03\.10 | 1\.18\.20 | 20\.10\.9 | 1\.1\.1 | 
| 1\.18\-2022\.02\.23 | 1\.18\.20 | 20\.10\.9 | N/A | 
| 1\.18\-2022\.01\.18 | 1\.18\.20 | 20\.10\.9 | N/A | 
| 1\.18\-2021\.12\.21 | 1\.18\.20 | 20\.10\.8 | N/A | 
| 1\.18\-2021\.11\.10 | 1\.18\.20 | 20\.10\.7 | N/A | 
| 1\.18\-2021\.10\.14 | 1\.18\.20 | 20\.10\.7 | N/A | 
| 1\.18\-2021\.09\.16 | 1\.18\.20 | 20\.10\.7 | N/A | 
| 1\.18\-2021\.08\.12 | 1\.18\.16 | 20\.10\.6 | N/A | 
| 1\.18\-2021\.07\.14 | 1\.18\.16 | 20\.10\.6 | N/A | 
| 1\.18\-2021\.06\.16 | 1\.18\.16 | 20\.10\.5 | N/A | 
| 1\.18\-2021\.05\.18 | 1\.18\.16 | 20\.10\.4 | N/A | 
| 1\.18\-2021\.04\.14 | 1\.18\.9 | 20\.10\.0 | N/A | 
| 1\.18\-2021\.03\.10 | 1\.18\.9 | 19\.03\.14 | N/A | 
| 1\.18\-2021\.02\.10 | 1\.18\.9 | 19\.03\.14 | N/A | 
| 1\.18\-2021\.01\.13 | 1\.18\.9 | 19\.03\.14 | N/A | 
| 1\.18\-2020\.12\.11 | 1\.18\.9 | 19\.03\.13 | N/A | 
| 1\.18\-2020\.11\.12 | 1\.18\.9 | 18\.09\.7 | N/A | 
| 1\.18\-2020\.10\.29 | 1\.18\.8 | 18\.09\.7 | N/A | 
| 1\.18\-2020\.10\.08 | 1\.18\.8 | 18\.09\.7 | N/A | 

------
#### [ Kubernetes version 1\.17 ]

The most recent version is the last version we're releasing for Amazon EKS `1.17` clusters\. It will be available until the `1.17` end of support date\. For more information, see [Amazon EKS Kubernetes release calendar](kubernetes-versions.md#kubernetes-release-calendar)\. For newer AMI releases, update your cluster to a later Kubneretes version\. For more information, see [Updating an Amazon EKS cluster Kubernetes version](update-cluster.md)\.


**Kubernetes version `1.17`**  

| AMI version | `kubelet` version | Docker version | 
| --- | --- | --- | 
| 1\.17\-2021\.08\.12 | 1\.17\.17 | 20\.10\.6 | 
| 1\.17\-2021\.06\.16 | 1\.17\.17 | 20\.10\.5 | 
| 1\.17\-2021\.05\.18 | 1\.17\.17 | 20\.10\.4 | 
| 1\.17\-2021\.04\.14 | 1\.17\.12 | 20\.10\.0 | 
| 1\.17\-2021\.03\.10 | 1\.17\.12 | 19\.03\.14 | 
| 1\.17\-2021\.02\.10 | 1\.17\.12 | 19\.03\.14 | 
| 1\.17\-2021\.01\.13 | 1\.17\.12 | 19\.03\.14 | 
| 1\.17\-2020\.12\.11 | 1\.17\.12 | 19\.03\.13 | 
| 1\.17\-2020\.11\.12 | 1\.17\.12 | 18\.09\.7 | 
| 1\.17\-2020\.10\.29 | 1\.17\.11 | 18\.09\.7 | 
| 1\.17\-2020\.09\.09 | 1\.17\.11 | 18\.09\.7 | 
| 1\.17\-2020\.08\.13 | 1\.17\.9 | 18\.09\.7 | 

------