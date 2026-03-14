⏺️ ➡️ 🟦 🔵🔹🔷 🔵 ☑️ ✔️ 🔴 ⭕ • ‣ → ⁕

# ⏺️ Reactjs/Spring Boot CI/CD and Deployment Flow

## ➡️ How your Reactjs applications are deployed in AWS?

### 🟦 Using Serverless

##### 🔵 Serverless CI/CD Flow

```text
Developer pushes code
        │
        ▼
GitHub Repository
        │
        ▼
CI/CD Pipeline Triggered (Jenkins / GitHub Actions)
        │
        ▼
Install dependencies
        │
        ▼
Build React Application
        │
        ▼
Create build folder
        │
        ▼
Upload build files to S3 bucket
        │
        ▼
Invalidate CloudFront cache (optional)
```

- **CloudFront (CDN)**
  - Global caching
  - Faster delivery
  - HTTPS support
  - DDoS protection

##### 🔵 Serverless Infrastructure Runtime Flow

```text
User Browser
      │
      ▼
CloudFront (CDN)
      │
      ▼
S3 Bucket
      │
      ▼
React Static Files
```

- React runs on EC2.
- Nginx serves the static files.

```text
User Browser
      │
      ▼
CloudFront (optional CDN)
      │
      ▼
Load Balancer(ELB)
      │
      ▼
EC2 Instance
      │
      ▼
Nginx / Apache
      │
      ▼
React Static Files
```

### 🟦 Using Non-Serverless

##### 🔵 Non-Serverless CI/CD Flow

```text
Developer pushes code
        │
        ▼
GitHub Repository
        │
        ▼
CI/CD Pipeline Triggered (Jenkins / GitHub Actions)
        │
        ▼
Install dependencies
        │
        ▼
Build React Application
        │
        ▼
Create build folder
        │
        ▼
Copy build files to EC2
        │
        ▼
Replace old build files
        │
        ▼
Reload Nginx

```

##### 🔵 Non-Serverless Infrastructure Runtime Flow

```text
User Browser
      │
      ▼
CloudFront (optional CDN)
      │
      ▼
Load Balancer (ELB)
      │
      ▼
EC2 Instances
      │
      ▼
Nginx / Apache
      │
      ▼
React Static Files
```

## ➡️ How your Spring Boot applications are deployed in AWS?

### 🟦 Using Serverless

- In serverless, we don’t manage servers or containers. So Kuberntes is not used.
- The cloud provider manages the infrastructure automatically.

##### 🔵 Serverless CI/CD Flow

```text
Developer pushes code
        │
        ▼
GitHub / GitLab Repository
        │
        ▼
CI/CD Pipeline Triggered
(Jenkins / GitHub Actions / GitLab CI)
        │
        ▼
Build Spring Boot Application
        │
        ▼
Create JAR file
        │
        ▼
Package application for Lambda
(zip or container image)
        │
        ▼
Deploy to AWS Lambda
        │
        ▼
Update API Gateway configuration
```

##### 🔵 Serverless Infrastructure Runtime Flow

- Characteristics:
  - No server management
  - Auto scaling
  - Pay only for execution

```text
Client / Browser
        │
        ▼
API Gateway
        │
        ▼
Lambda Function
(Spring Boot logic)
        │
        ▼
Database
(DynamoDB / RDS)
```

### 🟦 Using Non-Serverless

##### 🔵 Non-Serverless CI/CD Flow

```text
Developer pushes code
        │
        ▼
GitHub / GitLab Repository
        │
        ▼
CI/CD Pipeline Triggered
(Jenkins / GitHub Actions)
        │
        ▼
Build Spring Boot Application
        │
        ▼
Create JAR file
        │
        ▼
Build Docker Image
        │
        ▼
Push Image to Container Registry
(AWS ECR / Docker Hub)
        │
        ▼
Update Kubernetes Deployment
(kubectl apply / Helm)
        │
        ▼
Kubernetes updates Pods (rolling update)

```

##### 🔵 Non-Serverless Infrastructure Runtime Flow

```text
Client / Browser
        │
        ▼
Load Balancer (ALB)
        │
        ▼
Kubernetes Cluster (EKS)
        │
        ▼
Kubernetes Service
        │
        ▼
Pods (Spring Boot Containers)
        │
        ▼
RDS Database
```
