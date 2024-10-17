# learning-elk
this repo is a poc for learning elk

- there are some prerequisites for this to run in local, minikube and kubectl

# Setting Up Minikube
**Minikube** is a tool that creates a **local Kubernetes cluster** on your machine, ideal for development and testing. Follow these steps to set up Minikube and prepare it for deploying RabbitMQ.

- On macOS

    1. Install Homebrew (if you haven't already):
    > /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

    2. Install Minikube:
    > brew install minikube

- On Windows

    1. Install Chocolatey (if you haven’t):
    > @powershell -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"

    2. Install Minikube:
    > choco install minikube

- On Linux

    1. Download Minikube Binary:
    > curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

    2. Install Minikube:
    > sudo install minikube-linux-amd64 /usr/local/bin/minikube

# Seting Up kubectl
**kubectl** is the command-line tool for interacting with your Kubernetes cluster.

1. Install kubectl:

- On macOS:
> brew install kubectl
 
- On Windows:
> choco install kubernetes-cli

- On Linux:
> curl -LO "https://dl.k8s.io/release/v1.27.1/bin/linux/amd64/kubectl" chmod +x ./kubectl sudo mv ./kubectl /usr/local/bin/kubectl

2. Verify kubectl Configuration:
> kubectl config use-context minikube kubectl get nodes

Ensure that kubectl is configured to use your Minikube cluster and that it can communicate with the cluster.

# Start Minikube
1. Start Minikube:
> minikube start

You can **specify the driver** to use for virtualization (e.g., Docker, VirtualBox) with the --driver flag. For example, to use **Docker**:
> minikube start --driver=docker

2. Verify Minikube Status:
> minikube status

Ensure that Minikube is **running** and the Kubernetes components are up.