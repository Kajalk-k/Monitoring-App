# Monitoring Application Deployment on Amazon EKS

This project demonstrates how to deploy a monitoring application built with Flask on Amazon EKS (Elastic Kubernetes Service). The application is containerized using Docker and deployed as Kubernetes pods on Amazon EKS for scalability and reliability.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Deployment](#deployment)
- [Monitoring](#monitoring)
- [Contributing](#contributing)
- [The output of application](#output)

## Prerequisites

Before you begin, ensure you have the following prerequisites:

- **Amazon EKS Cluster**: Set up an Amazon EKS cluster in your AWS account.
- **Docker**: Install Docker to build and push container images.
- **Kubernetes Tools**: Install `kubectl` for interacting with your EKS cluster.
- **AWS CLI**: Configure AWS CLI for authentication.
- **Python**: Ensure you have Python installed locally for Flask development.

## Getting Started

Follow these steps to get started with this project:

1. Clone this repository:

   ```bash
   git clone https://github.com/yourusername/your-monitoring-app.git
   cd your-monitoring-app
   ```

2. Build the Docker container image for your Flask application:

   ```bash
   docker build -t Dockerfile .
   ```

3. Push the Docker image to your Amazon ECR (Elastic Container Registry):

   ```bash
   # Authenticate Docker to your ECR registry
   aws ecr get-login-password --region your-region | docker login --username AWS --password-stdin your-account-id.dkr.ecr.your-region.amazonaws.com

   # Tag your Docker image
   docker tag your-monitoring-app:latest your-account-id.dkr.ecr.your-region.amazonaws.com/your-monitoring-app:latest

   # Push the image to ECR
   docker push your-account-id.dkr.ecr.your-region.amazonaws.com/your-monitoring-app:latest
   ```

4. Deploy your application on Amazon EKS:

   ```bash
   python3 eks.py
   ```

5. Monitor and manage your application using Kubernetes tools and Amazon CloudWatch.

## Project Structure

The project structure is organized as follows:

```
your-monitoring-app/
├── app/
├── templates/
│   ├── index.html
├── eks.py
├── Dockerfile
├── ecr.py
├── README.md
```

- `app/`: Contains your Flask application code.
- `ecr.py`: Contains automated creation of repository for image of the application in ECR using BOTO3 SDK module of Python
- `eks.py`: Contains automated deployment of EKS using BOTO3 SDK module of Python.
- `Dockerfile`: Defines how to build the Docker image for your application.
- `README.md`: This file, providing project documentation.

## Deployment

The Kubernetes deployment configuration can be found in `eks.py`. You can customize this file to match your application's requirements and resource specifications.

To deploy or update your application, run:

```bash
python3 ecry.py
python3 eks.py
```

## Monitoring

You can monitor your application and cluster using Amazon CloudWatch, Prometheus, Grafana, or other monitoring solutions. Ensure you have the necessary monitoring tools and configurations in place.

## Contributing

Feel free to contribute to this project by opening issues or creating pull requests. Your contributions are welcome!

## Output

![image](https://github.com/Kajalk-k/Monitoring-App/assets/17482074/4de20f44-e7c2-4ce6-8d37-d7d479e0d484)

![image](https://github.com/Kajalk-k/Monitoring-App/assets/17482074/4c3ad94e-cc66-43f5-9c10-7923ae44c62f)




Remember to replace placeholders like `your-monitoring-app`, `yourusername`, `your-region`, `your-account-id`, and adjust the content as per your actual project details and preferences. This `README.md` provides a starting point for documenting your project's deployment process on Amazon EKS for a Flask-based monitoring application.
