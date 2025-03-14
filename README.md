# 📌 Deploying TimescaleDB on Kubernetes

This guide explains how to deploy **TimescaleDB** on a **Kubernetes cluster** using:

- 🏗️ **Deployment** – Runs the TimescaleDB container.
- 🔒 **Secret** – Stores database credentials securely.
- ⚙️ **ConfigMap** – Provides configuration data.
- 🌐 **Service** – Exposes the database.
- 💾 **PersistentVolumeClaim (PVC)** – Ensures data persistence.

---

## 📌 Prerequisites

Before deploying TimescaleDB, ensure you have:

- ✅ A running **Kubernetes cluster**.
- ✅ **kubectl** installed and configured to interact with the cluster.
- ✅ **StorageClass** installed for persistent volume provisioning.

---

## 🚀 Deployment Steps

### 1️⃣ Create a Kubernetes Secret

Store sensitive credentials such as the database password.

``` kubectl apply -f tsdb-secret.yaml ```


### 2️⃣ Create a ConfigMap

Define environment variables and configurations.

``` kubectl apply -f tsdb-configmap.yaml ```

### 3️⃣ Create a PersistentVolumeClaim (PVC)

Ensure data persistence.

``` kubectl apply -f tsdb-pvc.yaml ```

### 4️⃣ Create a Deployment for TimescaleDB

``` kubectl apply -f tsdb-deployment.yaml ```

### 5️⃣ Create a Service

Expose the database to the cluster or externally.

``` kubectl apply -f tsdb-service.yaml ```

### 🎯 Verify the Deployment

Check if the Pod is running:

``` kubectl get pods ```

### Connect to the database from within the cluster

``` kubectl run -it --rm --image=postgres --env="PGPASSWORD=yourpassword" psql-client -- psql -h timescaledb -U user -d database ```


### 📜 License
This project is licensed under the Apache License. See the LICENSE file for more details.