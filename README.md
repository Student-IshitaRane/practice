Deployment Architecture

After the application was developed and tested locally, it was deployed on Red Hat OpenShift, which is an enterprise container orchestration platform built on Kubernetes.

The deployment process consists of the following steps:

1. Build the Application

The frontend and backend are built separately.

The Spring Boot backend is packaged as a JAR file.
The frontend is built into static production files.
2. Create Docker Images

Each application is containerized using a Dockerfile.

A Docker image contains:

The application code
Required runtime (Java 17 for backend)
Dependencies
Configuration
Startup command

This ensures that the application runs the same way in every environment.

3. Push Images to a Container Registry

The Docker images are uploaded to a container registry.

OpenShift pulls these images whenever a deployment is created or updated.

4. Deploy on OpenShift

OpenShift creates separate pods for each service.

In our deployment:

Frontend Pod
Serves the web application.
Receives requests from users.
Backend Pod
Hosts the Spring Boot REST APIs.
Processes business logic.
Communicates with the database.

Keeping them in separate pods provides better modularity and allows independent deployment.

5. Communication Between Pods

When a user performs an action:

Browser
    │
    ▼
Frontend Pod
    │ REST API Call
    ▼
Backend Pod
    │
    ▼
Database

The frontend never accesses the database directly.

All requests go through the backend APIs.

6. OpenShift Management

OpenShift continuously monitors the application.

It provides features such as:

Pod health monitoring
Automatic restart if a pod crashes
Resource allocation (CPU and Memory)
Scaling when required
Deployment management

This improves application reliability and availability.

Resource Monitoring

OpenShift also provides resource monitoring.

For every pod, we can monitor:

CPU usage
Memory usage
Pod status
Restart count
Health

This helps ensure that the application performs efficiently in production.

(If you have screenshots of the OpenShift dashboard showing CPU and memory usage, include them in your PPT.)

Swagger

The backend APIs are exposed through Swagger (OpenAPI).

Swagger provides:

Documentation for every REST API
Request and response formats
API testing directly from the browser

This simplifies development, testing, and integration with the frontend.
