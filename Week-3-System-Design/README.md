# Week 3 — System Design Applications

**Julius Otega | Cloud Engineer Academy | AWS Cloud Engineering Portfolio**

## Overview
Week 3 focused on scalable application architecture, comparing monolithic, microservices, and serverless approaches, and designing cloud systems for e-commerce and video sharing. These are **conceptual system designs**, not deployed or benchmarked applications.

## Concepts studied
- Monolithic, microservices, and serverless architectures
- APIs, API Gateway, and load balancing
- Three-tier architecture
- Block, object, and file storage (EBS, S3, EFS)
- Caching and content delivery networks
- Vertical and horizontal scaling; EC2 Auto Scaling and AWS Lambda
- Video platform system-design case studies

## Architecture projects

### 1. Julius Otega CloudShop — Traditional vs. Serverless
A conceptual e-commerce application compared across two AWS approaches.

- **Traditional:** Application Load Balancer, EC2 Auto Scaling, Amazon RDS, caching, and S3
- **Serverless:** CloudFront, S3, API Gateway, Lambda, Cognito, DynamoDB, and EventBridge
- **Tradeoffs:** operational complexity, traffic patterns, cost models, resilience, security, and scaling limits

[Design PDF](projects/cloudshop/CloudShop_Design.pdf) | [Traditional diagram](projects/cloudshop/traditional_architecture.png) | [Serverless diagram](projects/cloudshop/serverless_architecture.png)

### 2. Julius Otega CloudStream — Video-Sharing Platform
A conceptual design for uploading, processing, moderating, and globally delivering videos.

- S3 for original and processed video storage
- DynamoDB for video metadata
- API Gateway and Lambda for upload/API workflows
- Step Functions and MediaConvert for transcoding orchestration
- Rekognition for content moderation design
- CloudFront for CDN delivery

[Design PDF](projects/cloudstream/CloudStream_Design.pdf) | [Architecture diagram](projects/cloudstream/CloudStream_Architecture.png)

## Security considerations
Least-privilege IAM, private S3 buckets, encryption, authenticated API requests, monitoring, and controlled publication of moderated videos.

## Evidence and scope
The project documents describe proposed AWS designs and architectural reasoning. They do not establish that infrastructure was provisioned, performance tested, or production deployed. Academy screenshots and proprietary course materials are intentionally excluded.

## Next steps
Implement selected components in an AWS sandbox, document testing and cost measurements, and refine architecture diagrams using official AWS icons.
