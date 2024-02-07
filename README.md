# kubernetest-reference-4tier-webapp

this is a basic script to create a Kubernetes cluster for a 4-tier web application architecture

basic script to create a Kubernetes cluster for a 4-tier web application architecture. This assumes you have Kubernetes installed and configured, and you're using YAML files to define your resources. You'll need to modify this script to fit your specific requirements and configurations:

This script creates a Kubernetes namespace called CM-web-app and then defines deployments for the frontend, backend, and database tiers with their respective replicas and container images. It also creates a load balancer service to expose the frontend to external traffic. Customize this script further based on the specific requirements, such as adding additional services, configuring persistent storage, or setting resource limits.

only platform admin should have access to the /var/logs folder 
Prometheus scrapes the log data in real time
Grafana visualizes the health metrics of the cluster

Namespace:

This section defines a Kubernetes namespace named web-app. Namespaces provide a way to divide cluster resources between multiple users or projects.
Frontend Deployment:

This section defines a Kubernetes Deployment resource for the frontend tier of the web application.
It specifies that three replicas of the frontend container should be created.
The selector ensures that pods with the label app: frontend are managed by this deployment.
The container spec defines the frontend container, including its name, Docker image, and the port it listens on.
Backend Deployment:

Similar to the frontend deployment, this section defines a Deployment resource for the backend tier of the web application.
It also specifies three replicas of the backend container and ensures that pods with the label app: backend are managed by this deployment.
Database Deployment:

This section defines a Deployment resource for the database tier of the web application.
It specifies a single replica of the database container and ensures that pods with the label app: database are managed by this deployment.
The database container is configured with its name, Docker image, and the port it listens on.
Load Balancer Service:

This section defines a Kubernetes Service resource named frontend-lb.
The service selects pods with the label app: frontend, effectively routing traffic to the frontend tier.
It exposes port 80 of the frontend containers within the Kubernetes cluster.
By setting the service type to LoadBalancer, Kubernetes will provision an external load balancer to distribute incoming traffic to the frontend pods. This allows external clients to access the frontend of the web application.
