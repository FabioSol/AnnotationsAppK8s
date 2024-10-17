# AnnotationsAppK8s

This repository provides an **Infrastructure as Code (IaC)** version of the [AnnotationsApp](https://github.com/FabioSol/AnnotationsApp) for easy deployment on Kubernetes. The goal is to automate the deployment process using Kubernetes manifests and ensure scalability, security, and maintainability of the application.

## Overview

This project is a Kubernetes-based deployment of the AnnotationsApp. It allows you to easily deploy the app by creating a Kubernetes cluster and applying the manifests in the `k8s-manifests/` directory.

### Prerequisites

- **kubectl**: Command-line tool for interacting with your Kubernetes cluster.
- A Kubernetes cluster (e.g., on Digital Ocean, GKE, etc.).

## Deployment Steps

1. **Create a Kubernetes Cluster**: 
   Ensure you have a Kubernetes cluster running and configured (e.g., on DigitalOcean or any other provider). You must connect `kubectl` to your cluster.

   Example:
   ```bash
   kubectl config use-context <your-cluster-context>
   ```

2. **Set Up Basic Authentication (Optional)**
   Basic auth is already enabled and set to username password by default. You can customize this by doing your own `htpasswd` file
   ```bash
   htpasswd -c auth username
   ```
   Then Base64 encode the credentials
   ```bash
   cat auth | base64
   ```

   And update the `secrets/basic-auth-secret.yaml` file with the encoded credentials.

   You could also change the type of secret to use external secrets.

3. **Deploy the app**
   To deploy the app, simply run the following command. This will apply all the Kubernetes manifests configured through the kustomization file:
   ```bash
   kubectl apply -k k8s-manifests
   ```

## **Notes**
   -  This repository is focused on infrastructure automation using Kubernetes.
   -  For the application-specific details (such as its functionality, Docker Compose version, etc.), please refer to the original [AnnotationsApp repository](https://github.com/FabioSol/AnnotationsApp).
   
   
   
