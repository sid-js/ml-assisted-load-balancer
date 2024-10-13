## ML Assisted Web Load Balancing using Kubernetes and KEDA
This project, titled "ML Assisted Web Load Balancing," explores the integration of machine learning algorithms to enhance the autoscaling of Kubernetes pods for web services. The primary goal is to develop a system that intelligently adjusts the number of active pods based on real-time usage metrics, ensuring optimal performance and resource utilization.

![Project Architecture](https://github.com/sid-js/ml-assisted-load-balancer/blob/82b8faa2c880707bcbb47d39375172dcfb94049f/image.png)


## Prerequisites

Before running the cluster creation script, ensure you have the following installed:

- **Minikube**: [Install Minikube](https://minikube.sigs.k8s.io/docs/start/)
- **kubectl**: [Install kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- **gnome-terminal**: Ensure you have `gnome-terminal` installed. If using a different terminal emulator, adjust the script accordingly.

## Script Usage

1. **Use the Script**: Use the `setup_minikube.sh` script in the repository root folder:

2. **Make the Script Executable**:

    ```bash
    chmod +x setup_minikube.sh
    ```

3. **Run the Script**:

    ```bash
    ./setup_minikube.sh
    ```

4. Run minikube tunnel in a new terminal

    ```bash
    minikube tunnel
    ```

5. Run port-forward for Prometheus in a new terminal
    ```bash
    kubectl port-forward service/prometheus-kube-prometheus-prometheus 9090:9090 -n monitoring
    ```

6. Run port-forward for Ingress-NGINX in a new terminal
    ```bash
    kubectl port-forward service/ingress-app-ingress-nginx-controller 3000:80
    ```

7. Run port-forward for ML API service in a new terminal
    ```bash
    kubectl port-forward service/ml-api-service 5000:5000
    ```
8. Visit Localhost
    - http://localhost:3000 - Web App
    - http://localhost:9000 - Prometheus
    - http://localhost:5000/predict - ML API
