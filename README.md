
# Local Kubernetes and Helm Nginx Deployment

## Description
This project demonstrates how to deploy an Nginx application on a local Kubernetes cluster using Minikube and manage it with Helm charts.

## Prerequisites
- Visual Studio Code (VSC)
- Docker
- Minikube
- Kubectl
- Helm

## Installation

### Step 1: Install Docker
Docker is a platform for developing, shipping, and running applications in containers.

- **[Docker for Mac](https://docs.docker.com/docker-for-mac/install/)**
- **[Docker for Windows](https://docs.docker.com/docker-for-windows/install/)**
- **[Docker for Linux](https://docs.docker.com/engine/install/#server)**

Follow the instructions on the Docker installation page for your operating system.

### Step 2: Install Minikube
Minikube is a tool that lets you run Kubernetes locally.

- **[Minikube for macOS](https://minikube.sigs.k8s.io/docs/start/#installing-minikube)**
- **[Minikube for Windows](https://minikube.sigs.k8s.io/docs/start/#installing-minikube)**
- **[Minikube for Linux](https://minikube.sigs.k8s.io/docs/start/#installing-minikube)**

### Step 3: Install Kubectl
Kubectl is a command-line tool for interacting with Kubernetes clusters.

- **[Kubectl for macOS](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/)**
- **[Kubectl for Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/)**
- **[Kubectl for Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)**

### Step 4: Install Helm
Helm is a package manager for Kubernetes.

- **[Helm for macOS, Windows, and Linux](https://helm.sh/docs/intro/install/)**

## Usage

### Step 1: Clone the Repository

Open your terminal in VSC and run:

```bash
git clone https://github.com/rsergio07/local-k8s-helm-nginx.git
cd local-k8s-helm-nginx
```

### Step 2: Start Minikube

Start Minikube to set up a local Kubernetes cluster:

```bash
minikube start
```

### Step 3: Deploy the Application using Helm

Install the Helm chart provided in the repository:

```bash
helm install my-nginx ./my-nginx-chart
```

### Step 4: Access the Application

Get the URL to access the Nginx service:

```bash
export NODE_PORT=$(kubectl get --namespace default -o jsonpath="{.spec.ports[0].nodePort}" services my-nginx-my-nginx-chart)
export NODE_IP=$(kubectl get nodes --namespace default -o jsonpath="{.items[0].status.addresses[0].address}")
echo http://$NODE_IP:$NODE_PORT
```

Open the provided URL in your browser to see the Nginx welcome page.

### Step 5: Clean Up

To clean up the resources, you can delete the Helm release and stop Minikube:

```bash
helm uninstall my-nginx
minikube stop
minikube delete
```

## Summary
This project provides a solid foundation for working with Kubernetes and Helm in a local development environment.

## License
This project is licensed under the MIT License.
