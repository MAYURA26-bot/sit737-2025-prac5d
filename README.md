# SIT737 Task 5.2D - Dockerization and Cloud Deployment

##  Introduction

This task extends the microservice developed in Task 5.1P by publishing the Dockerized application to a cloud environment using Google Cloud Platform (GCP). The calculator microservice, built with Node.js and Express.js, performs basic arithmetic operations such as addition, subtraction, multiplication, and division. It integrates Winston for structured logging and includes Docker Compose configuration and health checks. Task 5.2D focuses on tagging and pushing the Docker image to Google Artifact Registry, testing its deployment, and documenting the cloud publishing process.


##  Step 1: Set up your Private Container Registry on Google Cloud

1. Go to the [Google Cloud Console](https://console.cloud.google.com)
2. Create or use an existing project
3. Enable **Artifact Registry API**
4. Create a Docker repository:
   - Name: `microservices`
   - Format: `Docker`
   - Location: `australia-southeast1`
   - Visibility: Private


##  Step 2: Tag Your Docker Image

# Build image
`docker build . -t <docker-username>/<image-name>`

# Tag for Artifact Registry
`docker tag <docker-username>/<image-name> <your-region>-docker.pkg.dev/<your-project-id>/<repo-name>/<docker-username>/<image-name>`

## Step 3: Authenticate Docker with GCP
gcloud auth login
gcloud config set project sit737-25t1-neroshan-7dfbbd9
gcloud auth configure-docker australia-southeast1-docker.pkg.dev

##  Step 4: Push Docker Image to Registry
`docker push <your-region>-docker.pkg.dev/<your-project-id>/<repo-name>/<docker-username>/<image-name>`

## Step 5: Run Image from Google Cloud
`docker run -p <host-port>:<container-port> <your-region>-docker.pkg.dev/<your-project-id>/<repo-name>/<docker-username>/<image-name>`

Visit: [http://localhost:3001](http://localhost:3001)
