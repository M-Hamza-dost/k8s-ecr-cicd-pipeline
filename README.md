Kubernetes CI/CD Pipeline with ECR
==================================

Overview
--------

This project shows a simple end-to-end DevOps workflow.

I created a basic web app, containerized it using Docker, and set up a CI/CD pipeline using GitHub Actions. Whenever code is pushed, the image is built and pushed to AWS ECR using OIDC authentication (so no AWS keys are stored).

The app is then deployed on Kubernetes using Deployment and Service.

<br>

Tools Used
----------

*   Docker
    
*   Kubernetes
    
*   GitHub Actions
    
*   AWS ECR
    
<br>

How It Works
------------

1.  Code is pushed to GitHub
    
2.  GitHub Actions runs automatically
    
3.  Docker image is built
    
4.  GitHub authenticates with AWS using OIDC
    
5.  Image is pushed to ECR
    
6.  Kubernetes pulls the image and runs the app
    
<br>

CI/CD Pipeline
--------------

*   Trigger: push to main branch
    
*   Builds Docker image
    
*   Uses OIDC to authenticate with AWS
    
*   Pushes image to ECR
    

<br>

Kubernetes Deployment
---------------------

Apply manifests:
    
    kubectl apply -f k8s/

Check resources:

    kubectl get podskubectl get svc

<br>

Updating the Application
------------------------

When code changes:

1.  GitHub Actions builds and pushes a new image
    
2.  Restart the deployment to use the latest image:
    
         kubectl rollout restart deployment nginx-deployment

<br>

Access the App
--------------

    http://localhost:30007 


<br>

What I Learned
--------------

*   How Docker images are built and used
    
*   How Kubernetes runs and exposes applications
    
*   How GitHub Actions automates build pipelines
    
*   How OIDC allows secure access to AWS without storing keys
    
*   Basic flow of CI (build) and CD (deploy)
