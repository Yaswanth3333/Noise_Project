# DevOps Project: Orchestrating Containerized Applications with Kubernetes, AWS ECR, and CI/CD

Welcome to this DevOps project repository! Here, you'll find a comprehensive solution for managing containerized applications using Kubernetes, AWS Elastic Container Registry (ECR), and streamlined CI/CD pipelines.

## Project Goals

1. **Kubernetes Cluster Setup:**
    - Provision a Kubernetes cluster with a configuration file (cluster.yaml), suitable for local or cloud-based deployment.
    - Verify deployment to ensure cluster readiness.

2. **Dockerization and ECR Integration:**
    - Create a Dockerfile to containerize a basic web service (e.g., Nginx serving a static HTML page).
    - Document steps to build the Docker image and seamlessly push it to AWS ECR, including repository configuration.

3. **Ingress Management:**
    - Configure an Ingress Controller (Nginx) for efficient external traffic routing.
    - Supply an Ingress configuration file (ingress.yaml) to direct traffic to the web service based on URL paths.
    - Include test URLs and their expected responses for validation.

4. **CI/CD Automation:**
    - Implement a GitHub Actions pipeline for automated processes:
        - Docker image building.
        - ECR image pushing.
        - Kubernetes cluster deployment.
    - Provide the pipeline setup details in pipeline.yaml along with a comprehensive guide on its functionality.

## Implementation Overview

### Kubernetes Cluster Setup
        
1. **Cluster Initialization:**
    - Prepare the `cluster.yaml` file.
    - Deploy the cluster:
        
        ```bash
        kubectl apply -f cluster.yaml
        ```
![WhatsApp Image 2024-06-02 at 12 51 47_663dc7f5](https://github.com/Yaswanth3333/Noise_Project/assets/111300290/92d69c2f-3ed8-4177-99a8-04d04df213c1)

### Dockerization and ECR Integration

1. **Docker Image Creation:**
    - Build the Docker image for the web service.
    - Execute the command:
        
        ```bash
        docker build -t web-service .
        ```
        
2. **ECR Image Push:**
    - Create an ECR repository:
        
        ```bash
        aws ecr create-repository --repository-name web-service --region us-west-2
        ```
        
    - Authenticate Docker to ECR and push the image:
        
        ```bash
        aws ecr get-login-password --region us-west-2 | docker login --username AWS --password-stdin <aws_account_id>.dkr.ecr.us-west-2.amazonaws.com
        docker tag web-service:latest <aws_account_id>.dkr.ecr.us-west-2.amazonaws.com/web-service:latest
        docker push <aws_account_id>.dkr.ecr.us-west-2.amazonaws.com/web-service:latest
        ```
![aws](https://github.com/Yaswanth3333/Noise_Project/assets/111300290/b3b5a469-9cfb-426c-b0bd-41d431c1fb1c)

### Ingress Management

1. **Nginx Ingress Controller Setup:**
    - Apply the Ingress Controller:
        
        ```bash
        kubectl apply -f ingress.yaml
        ```

2. **Verification:**
    - Ensure the Ingress Controller is operational:
        
        ```bash
        kubectl get pods -n kube-system | grep ingress
        ```
![WhatsApp Image 2024-06-02 at 12 45 51_425dd799](https://github.com/Yaswanth3333/Noise_Project/assets/111300290/b6bd1fd1-21c7-4a5d-b765-ec4c0afd52d3)


3. **Access Your Application:**
    - Visit http://noise_Project.com in your web browser to access the deployed web application.

![website](https://github.com/Yaswanth3333/Noise_Project/assets/111300290/9151f997-f46f-45cf-b1aa-e75c221bca54)


### CI/CD Automation

1. **GitHub Actions Pipeline Setup:**
    - Configure a robust pipeline using GitHub Actions.
    - Detailed setup is outlined in pipeline.yaml.

![Screenshot 2024-06-02 131038](https://github.com/Yaswanth3333/Noise_Project/assets/111300290/20a28710-e78d-4622-9cba-faded9f300c3)


## Contributions

Contributions are encouraged! Please fork the repository and submit your pull requests to enhance the project further.

## Conclusion

This DevOps project has provided valuable hands-on experience in orchestrating containerized applications using Kubernetes, AWS ECR, and streamlined CI/CD pipelines. By achieving the project objectives, you've successfully established a microservices architecture, configured Kubernetes clusters, streamlined Docker and ECR workflows, managed Ingress for external traffic routing, and automated deployment via CI/CD pipelines using GitHub Actions.

This endeavor showcases not only technical proficiency but also effective documentation and communication skills. Your contributions and feedback are highly appreciated to refine and improve this solution.

Thank you for engaging with this DevOps project!
