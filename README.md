# kubernetes-mongo-express
A Kubernetes setup for deploying Mongo Express with an Ingress controller. This project includes Kubernetes manifests for exposing Mongo Express via a LoadBalancer and Ingress, along with DNS configuration instructions. Ideal for managing MongoDB through a web-based interface with secure access.
Files to Include:
mongo-express-deployment.yaml

Contains the Kubernetes Deployment manifest for Mongo Express.
mongo-express-service.yaml

Contains the Kubernetes Service manifest to expose Mongo Express via a LoadBalancer.
mongo-express-ingress.yaml (if using Ingress)

Contains the Kubernetes Ingress manifest for routing HTTP requests to Mongo Express.
1. Apply Kubernetes Manifests
Run these commands in the given order to apply your Kubernetes configurations:
kubectl apply -f mongo-secret.yaml
kubectl apply -f mongo.yaml
kubectl apply -f mongo-configmap.yaml
kubectl apply -f mongo-express.yaml
Apply NGINX Ingress Controller
To apply the Ingress controller manifest, use
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml
Check the Pods in the ingress-nginx Namespace
Once the manifest is applied, you can check the status of the Ingress controller pods:
kubectl get pods --namespace ingress-nginx
1. Apply the Ingress Configuration
Run the command to apply your Ingress configuration:
kubectl apply -f ingress.yaml
Check Services
After applying the Ingress configuration, you might want to check the status of your services to ensure they are correctly set up and exposed:
kubectl get svc
Conclusion
In this project, we successfully set up Mongo Express to provide a web-based interface for managing an internally running MongoDB application on Google Kubernetes Engine (GKE). We achieved this by following these key steps:

Deployment: We created and applied Kubernetes manifests to deploy Mongo Express and MongoDB, ensuring that they run efficiently within the cluster.

Exposure: To make Mongo Express accessible externally, we configured a LoadBalancer service that provides an external IP address. Additionally, we used Ingress resources to manage and route HTTP traffic to Mongo Express, allowing for domain-based access.

DNS Configuration: We configured DNS settings to map a custom domain to the external IP provided by the LoadBalancer or Ingress, facilitating easy access to Mongo Express via a user-friendly URL.

Verification and Debugging: We verified the deployment and configuration by checking the status of Kubernetes resources, examining logs, and ensuring DNS resolution was correctly configured.

This setup ensures that Mongo Express is accessible for web-based management of MongoDB, leveraging GKE's capabilities for scaling, load balancing, and secure access. The project demonstrates a practical application of Kubernetes and cloud services for deploying and managing containerized applications with external access.
