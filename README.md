# Helm Chart Deployment Guide

This guide will walk you through the process of deploying applications using Helm charts from this repository. Helm is a package manager for Kubernetes that simplifies the deployment of applications and services.

## Prerequisites

Before you start, ensure that you have the following:

- A running Kubernetes cluster
- Helm, version 3.0 or higher

You can check the versions of Kubernetes and Helm with the following commands:

```bash
kubectl version --short
helm version --short

```

## Structure of the Repository

The repository contains several directories, each hosting a specific Helm chart. A Helm chart is essentially a bundle of information necessary to create an instance of a Kubernetes application.

## Deployment Steps

1. **Clone the repository**
    
    Clone this repository to your local machine using the following command:
    
    ```bash
    git clone <https://github.com/hasan2001jk/Helm_Charts.git>
    
    ```
    
2. **Navigate to the chart directory**
    
    Change to the specific chart directory that you want to deploy. For example:
    
    ```bash
    cd Helm_Charts/charts/cakestudio-chart
    
    ```
    
3. **Customize configuration parameters**
    
    Open the `values.yaml` file in the chart directory. This file contains configuration parameters for the chart. Customize these parameters according to your requirements.
    
4. **Deploy the application**
    
    Run the following command to deploy the application:
    
    ```bash
    helm install [RELEASE_NAME] .
    
    ```
    
    Replace `[RELEASE_NAME]` with the name you want to give to your application.
    

## What Happens When You Deploy the Helm Chart?

When you run the `helm install` command, Helm combines the chart and your configuration parameters to generate a Kubernetes manifest file. Helm then applies this file to your Kubernetes cluster, creating the resources defined in the manifest.

The Helm chart includes several files, each serving a specific purpose:

- `_helpers.tpl`: This file contains helper templates that can be reused throughout the chart.
- `cakestudio-app-deploy.yaml`: This file defines a Kubernetes Deployment for the Cakestudio application. The Deployment controller provides declarative updates for Pods and ReplicaSets.
- `cakestudio-db-stateful.yaml`: This file defines a Kubernetes StatefulSet for the Cakestudio database. StatefulSets are used to manage stateful applications with persistent data.
- `cakestudio-pv.yaml`: This file defines a Kubernetes PersistentVolume (PV) for storage. PVs are used for managing storage in the cluster and can be provisioned either dynamically or manually for use by the cluster.
- `config-map.yaml`: This file defines a Kubernetes ConfigMap that holds configuration data for the application and database. ConfigMaps are used to separate configuration artifacts from image content to keep containerized applications portable.
- `secret.yaml`: This file defines a Kubernetes Secret that holds sensitive data such as database credentials. Secrets are used to store and manage sensitive information.
- `service-app.yaml`: This file defines a Kubernetes Service that exposes the Cakestudio application to the network. Services enable network access to a set of pods.
- `service-db.yaml`: This file defines a Kubernetes Service that exposes the Cakestudio database to the network.
- `storage-class.yaml`: This file defines a Kubernetes StorageClass that provisions storage for the PersistentVolume. StorageClasses are used to define different classes of storage.

Remember, the actual deployment in your cluster might differ based on the configuration parameters you set in the `values.yaml` file.
