Provide your solution here:

Overview Diagram of Services and Their Roles
Here’s a textual representation of the architecture, optimized for 500 RPS and <100ms p99 latency:


[Clients: Web, Mobile, API]
         ⇅
[AWS API Gateway + Route 53]
         ⇅
-------------------------------------------------
| Region: us-east-1 (Active) | us-west-2 (Standby) |
-------------------------------------------------
[Authentication Service]
   (AWS Cognito + EKS)
         ⇅
[DynamoDB Global Tables]
         ⇅
[Order Management Service]
       (EKS + Kafka)
         ⇅
[Matching Engine]
    (EC2 + Redis Cluster)
         ⇅
[Market Data Service]
   (AppSync + CloudFront)
         ⇅
[Trade Settlement Service]
      (EKS + SQS)
         ⇅
[Aurora DB + S3 Backups]



-------------------------------------------------
[Monitoring: CloudWatch + X-Ray]
