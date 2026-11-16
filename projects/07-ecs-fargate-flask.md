# Flask Application Deployment on ECS Fargate

**Concept**
ECS runs and manages container workloads. ECR stores container images, while Fargate provides the compute capacity without requiring me to manage EC2 worker instances.

**What I worked on**
I packaged a Flask application in a Docker image, pushed it to ECR, and ran it as an ECS service on Fargate. The application listened on port 8080 and exposed a health-check endpoint.

**How I did it**
- Built the Flask Docker image and pushed it to an ECR repository.
- Created an ECS task definition with the image, port and task settings.
- Created an ECS cluster and Fargate service.
- Ran the task and tested the application health endpoint.

**Problem it solves**
The application can be deployed as a repeatable container workload without managing the underlying EC2 hosts. ECS keeps the service at its configured desired task count.
