# SIT737 Task 5.2D - Dockerization and Cloud Deployment

## 📘 Introduction

This task extends the microservice developed in Task 5.1P by publishing the Dockerized application to a cloud environment using Google Cloud Platform (GCP). The calculator microservice, built with Node.js and Express.js, performs basic arithmetic operations such as addition, subtraction, multiplication, and division. It integrates Winston for structured logging and includes Docker Compose configuration and health checks. Task 5.2D focuses on tagging and pushing the Docker image to Google Artifact Registry, testing its deployment, and documenting the cloud publishing process.

---

## ✅ Step 1: Set up your Private Container Registry on Google Cloud

1. Go to the [Google Cloud Console](https://console.cloud.google.com)
2. Create or use an existing project
3. Enable **Artifact Registry API**
4. Create a Docker repository:
   - Name: `microservices`
   - Format: `Docker`
   - Location: `australia-southeast1`
   - Visibility: Private

---

## ✅ Step 2: Tag Your Docker Image

```bash
cd C:\Uni\SIT737\SIT737-2025-T1-2.1P\5.1P\sit737-2025-prac4.1P

# Build image
docker build -t mayura1994/5.2d-calculator-microservice .

# Tag for Artifact Registry
docker tag mayura1994/5.2d-calculator-microservice \
australia-southeast1-docker.pkg.dev/sit737-25t1-neroshan-7dfbbd9/sit737-5d-microservice/mayura1994/5.2d-calculator-microservice
```

---

## ✅ Step 3: Authenticate Docker with GCP

```bash
gcloud auth login
gcloud config set project sit737-25t1-neroshan-7dfbbd9
gcloud auth configure-docker australia-southeast1-docker.pkg.dev
```

---

## ✅ Step 4: Push Docker Image to Registry

```bash
docker push australia-southeast1-docker.pkg.dev/sit737-25t1-neroshan-7dfbbd9/sit737-5d-microservice/mayura1994/5.2d-calculator-microservice
```

---

## ✅ Step 5: Run Image from Google Cloud

```bash
docker run -p 3001:3000 \
australia-southeast1-docker.pkg.dev/sit737-25t1-neroshan-7dfbbd9/sit737-5d-microservice/mayura1994/5.2d-calculator-microservice
```

Visit: [http://localhost:3001](http://localhost:3001)

---

## ✅ Step 6: Push Code to GitHub

```bash
git init
git remote add origin https://github.com/<your-github-username>/sit737-2025-prac5d
git add .
git commit -m "Task 5.2D completed"
git branch -M main
git push -u origin main
```

---

## 📄 Conclusion

The Docker image was successfully built and pushed to Google Artifact Registry. The application can now be deployed directly from the cloud for use in modern microservice environments.
