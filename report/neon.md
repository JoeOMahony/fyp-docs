# Neon: PostgreSQL backend

Neon is a managed, serverless database platform for PostgreSQL. The core functionality that sets it apart from other relational database providers, like Amazon RDS, is the separation of the storage and compute planes. This leads to features like:

1. Instant database branching using a Copy-on-Write (CoW) storage model, like Docker uses when building images. I'll be able to create a clean branch of the silver layer within a second for testing out data transformations like binning when training.
2. The ability to instantly restore a database from a snapshot will enable faster development of the silver layer through reducing the time spent rebuilding the database after failed transformation attempts. Without this feature, an expensive connection would need to be established between the silver S3 buckets and Neon.
3. Scale-to-zero computing. When the compute plane has been inactive for five or more minutes, it suspends entirely. When a request does arrive, Neon can ready the database within a few hundred milliseconds. This is especially beneficial for Aeroq due to the nature of the final year project; months of sparse traffic followed by a surge. This also enables configurable compute plane auto-scaling.

I thoroughly considered deploying Postgres with Amazon RDS, a platform I'm familiar with, before settling on Neon due to the expensive complexities of AWS. RDS must be deployed in a VPC and, given that security and development best practices are considerations, in a private subnet. Since Postgres will hold the data that I will use locally to train the model, either a route is needed to communicate with RDS from outside of that VPC, or, the training must be done within the VPC. There are a number of suitable implementations for opening a route over the Internet, like a bastion host and an Internet Gateway or an API Gateway with Elastic Network Interfaces attached to relevant Lambdas, but these require relatively expensive appliances and extensive network planning. Training on AWS is limited by a combination of Lambda's maximum runtime of 15 minutes, my lack of experience, and the cost. After evaluation and re-evaluation, I determined that only Neon could meet my need for an easy-to-learn, cost-effective, API-friendly, scalable relational database provider.

Sources:

https://neon.com/docs/get-started/why-neon
https://neon.com/docs/introduction/scale-to-zero
https://www.lenovo.com/ie/en/glossary/what-is-cow/ (for Docker reference)