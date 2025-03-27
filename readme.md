# Kubernetes Multi-Tier Application

## 📌 **Project Overview**
This project demonstrates the deployment of a multi-tier application using Kubernetes. It consists of a frontend WordPress application, a backend MySQL database, and Kubernetes components like Deployments, Services, and Persistent Volumes.

## 🧱 **Architecture**
The application follows a typical three-tier architecture:
1. **Frontend (WordPress)** - User interface for creating and managing content.
2. **Backend (MySQL)** - Database management for storing and retrieving data.
3. **Kubernetes** - Manages containerized deployment, scaling, and networking.

## 🛠 **Prerequisites**
Make sure you have the following installed:
- Docker
- Kubernetes (Minikube or any Kubernetes cluster)
- kubectl (Kubernetes CLI)
- Git

## 🚀 **Installation and Setup**

1. **Clone the Repository:**
```bash
git clone https://github.com/DaChe01/k8s-multi-tier-app.git
cd k8s-multi-tier-app
```

2. **Start Minikube (If Using Minikube):**
```bash
minikube start
```

3. **Create a Namespace:**
Create a dedicated namespace for the application to keep resources organized:
```bash
kubectl create namespace multi-tier-app
```

4. **Create the MySQL Secret:**
First, create a Kubernetes secret for MySQL credentials within the namespace. Ensure your `mysql-secret.yaml` contains the required environment variables like `MYSQL_ROOT_PASSWORD`, `MYSQL_DATABASE`, `MYSQL_USER`, and `MYSQL_PASSWORD`.
```bash
kubectl apply -f mysql-secret.yaml -n multi-tier-app
```

5. **Deploy the Application:**
```bash
kubectl apply -f mysql-deployment.yaml -n multi-tier-app
kubectl apply -f wordpress-deployment.yaml -n multi-tier-app
```

6. **Verify Deployments and Services:**
```bash
kubectl get pods -n multi-tier-app
kubectl get services -n multi-tier-app
```

7. **Access the Application:**
- Use the `minikube service` command to get the external URL:
```bash
minikube service wordpress-service -n multi-tier-app
```

## 🧑‍💻 **Project Structure**
```plaintext
k8s-multi-tier-app/
├── mysql-deployment.yaml
├── wordpress-deployment.yaml
├── persistent-volume.yaml
├── mysql-secret.yaml
├── README.md
```

- **mysql-deployment.yaml**: Defines the MySQL database deployment and service using MySQL secret.
- **wordpress-deployment.yaml**: Defines the WordPress application deployment and service.
- **persistent-volume.yaml**: Sets up persistent storage for MySQL.
- **mysql-secret.yaml**: Contains the MySQL credentials using Kubernetes secrets. Ensure the MySQL environment variables are correctly configured.

## ⚡ **Useful Commands**
- Check Logs:
```bash
kubectl logs <pod_name> -n multi-tier-app
```
- Delete Resources:
```bash
kubectl delete -f mysql-deployment.yaml -n multi-tier-app
kubectl delete -f wordpress-deployment.yaml -n multi-tier-app
kubectl delete -f mysql-secret.yaml -n multi-tier-app
```
- View Cluster Status:
```bash
kubectl cluster-info
```

## 🛡 **Troubleshooting**
- Ensure Minikube is running with `minikube status`.
- Check pod logs using `kubectl logs <pod_name> -n multi-tier-app`.
- Confirm resources using `kubectl get all -n multi-tier-app`.

## 🤝 **Contributing**
Contributions are welcome! Feel free to submit pull requests or open issues.

## 📜 **License**
This project is licensed under the [MIT License](LICENSE).

---
Happy Coding! 😊