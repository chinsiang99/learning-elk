# learning-elk
this repo is a poc for learning elk

- there are some prerequisites for this to run in local, minikube and kubectl

# Setting up Minikube
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