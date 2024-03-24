
# Kubernetes for Data Engineering

Welcome to the Kubernetes for Data Engineering repository! This repository provides all the necessary configuration files and DAGs (Directed Acyclic Graphs) to set up a robust data engineering environment using Kubernetes and Apache Airflow. It includes the setup for the Kubernetes Dashboard, offering a user-friendly web interface for managing Kubernetes clusters, along with Apache Airflow, a platform for programmatically authoring, scheduling, and monitoring workflows.

## Repository Structure

The repository is organized as follows:

├── dags
│ ├── fetch_and_preview.py
│ └── hello.py
└── k8s
├── dashboard-adminuser.yaml
├── dashboard-clusterrole.yaml
├── dashboard-secret.yaml
├── recommended-dashboard.yaml
└── values.yaml



### DAGs

- `fetch_and_preview.py`: This DAG fetches data and provides a preview.
- `hello.py`: A simple example DAG demonstrating basic Apache Airflow concepts.

### Kubernetes (k8s) Configuration

- `dashboard-adminuser.yaml`: YAML file for setting up an admin user for the Kubernetes Dashboard.
- `dashboard-clusterrole.yaml`: YAML file defining the cluster role for the Kubernetes Dashboard.
- `dashboard-secret.yaml`: YAML file managing secrets used by the Kubernetes Dashboard.
- `recommended-dashboard.yaml`: YAML file for deploying the recommended Kubernetes Dashboard setup.
- `values.yaml`: YAML file containing customizable values for the Kubernetes setup.

## Getting Started

### Prerequisites

Before you begin, ensure you have the following:

- A Kubernetes cluster
- `kubectl` installed and configured
- Helm (optional but recommended for managing Kubernetes applications)

### Setup

1. **Deploy the Kubernetes Dashboard**:

    Apply the YAML files in the `k8s` directory to set up the Kubernetes Dashboard:

    ```bash
    kubectl apply -f k8s/
    ```

    This will establish the Kubernetes Dashboard with the necessary roles and permissions.

2. **Creating a Kubernetes Secret Key**:

    Create a Kubernetes secret key for Airflow:

    ```bash
    kubectl create secret generic airflow-secret --from-literal=fernet-key=<your-fernet-key>
    ```

    Replace `<your-fernet-key>` with your Fernet key value.

3. **Accessing the Kubernetes Dashboard**:

    To access the Dashboard, start a proxy server:

    ```bash
    kubectl proxy
    ```

    Access the Dashboard at: 
   (http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/)
   

    Log in using the token generated for the admin user (refer to `dashboard-secret.yaml`).

5. **Deploy Apache Airflow**:

    You can deploy Apache Airflow using Helm or by applying custom YAML files. For Helm:

    ```bash
    helm repo add apache-airflow https://airflow.apache.org
    helm install airflow apache-airflow/airflow -f k8s/values.yaml
    ```

    This will deploy Airflow with the settings defined in `values.yaml`.

6. **Running Apache Airflow**:

    To run Apache Airflow, port forward the Airflow web server:

    ```bash
    kubectl port-forward svc/airflow-webserver 8080:8080 --namespace default
    ```

    Access the Airflow UI at [http://localhost:8080](http://localhost:8080) and use the Airflow credentials to log in.

7. **Adding DAGs to Airflow**:

    Copy your DAG files (e.g., `fetch_and_preview.py`, `hello.py`) into the DAGs folder of your Airflow deployment. The method of copying depends on your Airflow setup (e.g., using Persistent Volume, Git-sync).


### DAGs

- `fetch_and_preview.py`: This DAG fetches data and provides a preview.
- `hello.py`: A simple example DAG demonstrating basic Apache Airflow concepts.

### Kubernetes (k8s) Configuration

- `dashboard-adminuser.yaml`: YAML file for setting up an admin user for the Kubernetes Dashboard.
- `dashboard-clusterrole.yaml`: YAML file defining the cluster role for the Kubernetes Dashboard.
- `dashboard-secret.yaml`: YAML file managing secrets used by the Kubernetes Dashboard.
- `recommended-dashboard.yaml`: YAML file for deploying the recommended Kubernetes Dashboard setup.
- `values.yaml`: YAML file containing customizable values for the Kubernetes setup.

## Getting Started

### Prerequisites

Before you begin, ensure you have the following:

- A Kubernetes cluster
- `kubectl` installed and configured
- Helm (optional but recommended for managing Kubernetes applications)

### Setup

1. **Deploy the Kubernetes Dashboard**:

    Apply the YAML files in the `k8s` directory to set up the Kubernetes Dashboard:

    ```bash
    kubectl apply -f k8s/
    ```

    This will establish the Kubernetes Dashboard with the necessary roles and permissions.

2. **Creating a Kubernetes Secret Key**:

    Create a Kubernetes secret key for Airflow:
![image](https://github.com/GuirassyFode/kubernetesDataEngineer/assets/25976326/f767652c-a405-46b1-94f6-1d9650bf917d)

    ```bash
    kubectl create secret generic airflow-secret --from-literal=fernet-key=<your-fernet-key>
    ```

    Replace `<your-fernet-key>` with your Fernet key value.

3. **Accessing the Kubernetes Dashboard**:

    To access the Dashboard, start a proxy server:

    ```bash
    kubectl proxy

    
![image](https://github.com/GuirassyFode/kubernetesDataEngineer/assets/25976326/f7dc51ca-4d4b-4f28-b32a-4742cd30b9c7)
```

    Access the Dashboard at: [http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/](http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/).

    Log in using the token generated for the admin user (refer to `dashboard-secret.yaml`).

4. **Deploy Apache Airflow**:

    You can deploy Apache Airflow using Helm or by applying custom YAML files. For Helm:

    ```bash
    helm repo add apache-airflow https://airflow.apache.org
    helm install airflow apache-airflow/airflow -f k8s/values.yaml
    ```

    This will deploy Airflow with the settings defined in `values.yaml`.

5. **Running Apache Airflow**:

    To run Apache Airflow, port forward the Airflow web server:

    ```bash
    kubectl port-forward svc/airflow-webserver 8080:8080 --namespace default
    ```

    Access the Airflow UI at [http://localhost:8080](http://localhost:8080) and use the Airflow credentials to log in.

6. **Adding DAGs to Airflow**:

    Copy your DAG files (e.g., `fetch_and_preview.py`, `hello.py`) into the DAGs folder of your Airflow deployment. The method of copying depends on your Airflow setup (e.g., using Persistent Volume, Git-sync).

## Usage

- **Kubernetes Dashboard**: Utilize the Dashboard to monitor and manage the Kubernetes cluster.
- **Apache Airflow**: Access the Airflow web UI to manage, schedule, and monitor workflows.

Feel free to explore and customize this setup according to your data engineering needs!
![image](https://github.com/GuirassyFode/kubernetesDataEngineer/assets/25976326/25605288-88a0-4f20-85df-6b0d32db8396)
## Usage

- **Kubernetes Dashboard**: Utilize the Dashboard to monitor and manage the Kubernetes cluster.
- **Apache Airflow**: Access the Airflow web UI to manage, schedule, and monitor workflows.

Feel free to explore and customize this setup according to your data engineering needs!
