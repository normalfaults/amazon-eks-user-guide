# Installing `eksctl`<a name="eksctl"></a>

This topic covers `eksctl`, a simple command line utility for creating and managing Kubernetes clusters on Amazon EKS\. The `eksctl` command line utility provides the fastest and easiest way to create a new cluster with nodes for Amazon EKS\. For more information and to see the official documentation, visit [https://eksctl\.io/](https://github.com/weaveworks/eksctl)\.

This topic helps you to download and install `eksctl` binaries for macOS, Linux, and Windows operating systems\.

**Prerequisite**  
The `kubectl` command line tool is installed on your computer or AWS CloudShell\. The version can be the same as or up to one minor version earlier or later than the Kubernetes version of your cluster\. For example, if your cluster version is `1.21`, you can use `kubectl` version `1.20`,`1.21`, or `1.22` with it\. To install or upgrade `kubectl`, see [Installing `kubectl`](install-kubectl.md)\.

## Installing or upgrading `eksctl`<a name="installing-eksctl"></a>

This section helps you install or upgrade to the latest version of the `eksctl` command line utility\. Complete the procedure for your operating system\.

------
#### [ macOS ]<a name="install-eksctl-macos"></a>

**To install or upgrade `eksctl` on macOS**

The easiest way to get started with Amazon EKS and macOS is by installing `eksctl` with Homebrew, an open\-source tool that can be installed using [these instructions](https://brew.sh/)\. The `eksctl` Homebrew recipe installs `eksctl` and any other dependencies that are required for Amazon EKS, such as `kubectl`\. The recipe also installs the [`aws-iam-authenticator`](install-aws-iam-authenticator.md), which is required if you don't have the AWS CLI version `1.16.156` or higher installed\.

1. If you do not already have Homebrew installed on macOS, install it with the following command\.

   ```
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
   ```

1. Install the Weaveworks Homebrew tap\.

   ```
   brew tap weaveworks/tap
   ```

1. Install or upgrade `eksctl`\.
   + Install `eksctl` with the following command:

     ```
     brew install weaveworks/tap/eksctl
     ```
   + If `eksctl` is already installed, run the following command to upgrade:

     ```
     brew upgrade eksctl && brew link --overwrite eksctl
     ```

1. Test that your installation was successful with the following command\.

   ```
   eksctl version
   ```
**Note**  
 The `GitTag` version should be at least `0.103.0`\. If not, check your terminal output for any installation or upgrade errors, or manually download an archive of the release from [https://github\.com/weaveworks/eksctl/releases/download/v0\.103\.0/eksctl\_Darwin\_amd64\.tar\.gz](https://github.com/weaveworks/eksctl/releases/download/v0.103.0/eksctl_Darwin_amd64.tar.gz), extract `eksctl`, and then run it\.

------
#### [ Linux ]<a name="install-eksctl-linux"></a>

**To install or upgrade `eksctl` on Linux**

1. Download and extract the latest release of `eksctl` with the following command\.

   ```
   curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
   ```

1. Move the extracted binary to `/usr/local/bin`\.

   ```
   sudo mv /tmp/eksctl /usr/local/bin
   ```

1. Test that your installation was successful with the following command\.

   ```
   eksctl version
   ```
**Note**  
The `GitTag` version should be at least `0.103.0`\. If not, check your terminal output for any installation or upgrade errors, or replace the address in step 1 with `https://github.com/weaveworks/eksctl/releases/download/v0.103.0/eksctl_Linux_amd64.tar.gz` and complete steps 1\-3 again\.

------
#### [ Windows ]<a name="install-eksctl-windows"></a>

**To install or upgrade `eksctl` on Windows**

1. If you do not already have Chocolatey installed on your Windows system, see [Installing Chocolatey](https://chocolatey.org/install)\.

1. Install or upgrade `eksctl`\.
   + Install the binaries with the following command:

     ```
     choco install -y eksctl 
     ```
   + If they are already installed, run the following command to upgrade:

     ```
     choco upgrade -y eksctl 
     ```

1. Test that your installation was successful with the following command\.

   ```
   eksctl version
   ```
**Note**  
 The `GitTag` version should be at least `0.103.0`\. If not, check your terminal output for any installation or upgrade errors, or manually download an archive of the release from [https://github\.com/weaveworks/eksctl/releases/download/v0\.103\.0/eksctl\_Windows\_amd64\.zip](https://github.com/weaveworks/eksctl/releases/download/v0.103.0/eksctl_Windows_amd64.zip), extract `eksctl`, and then run it\.

------