## How to Install AWS CLI and Connect to EKS

This guide provides step-by-step instructions for installing the AWS Command Line Interface (AWS CLI) and connecting to an Amazon Elastic Kubernetes Service (EKS) cluster.
Prerequisites

- A computer with macOS, Linux, or Windows
- AWS IAM User - Access key and secret access key
- Basic familiarity with terminal commands

----------------------------------

### Step 1: Install AWS CLI
The AWS CLI allows you to interact with AWS services from the command line.

### For macOS

1. Open a terminal.

2. Install Homebrew (if not already installed):
```/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"```


3. Install AWS CLI using Homebrew:
```brew install awscli```


4. Verify the installation:
```aws --version```



### For Linux

1. Open a terminal. Download the AWS CLI installer:

```curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"```


2. Unzip the file:
```unzip awscliv2.zip```


3. Install AWS CLI:
```sudo ./aws/install```


4. Verify the installation:
```aws --version```



### For Windows

1. Download the AWS CLI MSI installer from: https://awscli.amazonaws.com/AWSCLIV2.msi

2. Run the installer and follow the prompts.

3. Open a Command Prompt or PowerShell.

4. Verify the installation:
```aws --version```

----------------------------------

### Step 2: Configure AWS CLI

1. Run the configuration command:
aws configure


2. Enter the following details when prompted:

AWS Access Key ID: Your AWS access key
AWS Secret Access Key: Your AWS secret key
Default region name: ap-southeast-1


3. Verify the configuration:
```aws sts get-caller-identity```

This should return your AWS account details.

-----------------------

### Step 3: Install kubectl

**kubectl** is required to interact with Kubernetes clusters.


1. Installing Kubectl

### For macOS:
```brew install kubectl```


### For Linux:
```curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
```

### For Windows:

Download the binary: https://dl.k8s.io/release/v1.28.0/bin/windows/amd64/kubectl.exe
Move it to a directory in your system PATH.


2. Verify the installation:
```kubectl version --client```

--------------------------

### Step 4: Connect to EKS Cluster

1. Update the kubeconfig file to include your EKS cluster. Replace <region-name> with your cluster's region (e.g., us-west-2) and <cluster-name> with your EKS cluster name.

```aws eks update-kubeconfig --region ap-southeast-1 --name gcash-fecp5-cluster```

2. Verify the cluster connection:
```kubectl get svc```

This should list the services in the default namespace of your EKS cluster.

--------------------------

## Step 5: Test Cluster Access

1. Check the nodes in your cluster:
```kubectl get nodes```


