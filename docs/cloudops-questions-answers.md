Q1: How do you design a highly available architecture on AWS for a web application?

A: I would deploy the application across multiple Availability Zones behind a load balancer to distribute traffic. I’d use an Auto Scaling Group so instances can recover from failures and scale with demand, and ensure the database is Multi-AZ or replicated for redundancy. For maximum availability, I might also implement a multi-region failover with DNS if required.

Q2: What are RTO and RPO, and how do they influence your AWS disaster recovery strategy?

A: RTO (Recovery Time Objective) is the target maximum downtime, and RPO (Recovery Point Objective) is the target maximum data loss in time. These drive the DR strategy: a low RTO/RPO means we need faster recovery solutions (like active-active multi-region or real-time replication), whereas a higher RTO/RPO allows for simpler solutions like restoring from backups with more downtime.

Q3: If an AWS region hosting your application goes down, what steps would you take to recover?

A: I would fail over to a secondary region that has been prepared for DR. For example, if I have set up cross-region replication or backups, I’d launch the infrastructure in the DR region (using automated templates/IaC), restore data from the latest backup or replica, and update DNS (Route 53) to point users to the application in the new region. The key is having a pre-planned DR environment and automated processes to bring services back quickly.

Q4: You notice a sudden 30% increase in AWS costs this month. How do you investigate and address it?

A: First, I’d use AWS Cost Explorer or billing reports to identify which services or resources saw the cost spike. Once I pinpoint the cause (for example, an oversized instance left running or a sudden increase in data transfer), I’d take action to correct it – such as shutting down or right-sizing the resource, or fixing the usage issue. I would also set up cost alerts or budgets to catch future anomalies early.

Q5: Explain the difference between vertical and horizontal scaling in AWS, and when you might use each.

A: Vertical scaling means increasing the resources of a single server (for example, upgrading to a larger EC2 instance), while horizontal scaling means adding more instances/servers to distribute the load. I’d use horizontal scaling for most web applications because it improves fault tolerance and scalability (adding more instances behind a load balancer). Vertical scaling is sometimes used for quick performance boosts or when an application can’t be distributed, but it has limits and a single point of failure.

Q6: How do you monitor a production environment in AWS? Name some key services or metrics you focus on.

A: I rely on Amazon CloudWatch for monitoring. I track metrics like CPU utilization, memory (using the CloudWatch agent), disk I/O, network traffic, and custom application metrics (like latency or error rates). I set up CloudWatch Alarms on critical metrics to get alerts, use CloudWatch Logs (or a centralized logging solution) to monitor application logs, and may use AWS X-Ray or other APM tools to trace and diagnose performance issues.

Q7: Your application’s response times have increased significantly. What AWS tools or approaches would you use to identify the bottleneck?

A: I would start by checking CloudWatch metrics to see if any resource (CPU, memory, database throughput, etc.) is under pressure or if latency spiked on a specific component. Then I’d use AWS X-Ray (or another tracing/APM tool) to trace requests through the application and identify which service or call is slow. Examining CloudWatch Logs or enabling detailed logs on services (like ALB access logs or RDS performance insights) can also help pinpoint the issue.

Q8: An EC2 instance in a private subnet cannot reach the internet. What could be the problem and how do you fix it?

A: The likely issue is that the instance has no route to the internet – typically missing a NAT Gateway (or NAT instance) setup. In a private subnet, instances need a NAT in a public subnet and a route in their route table pointing to that NAT for outbound internet access. I would deploy a NAT Gateway in a public subnet (with an Internet Gateway on the VPC) and update the private subnet’s route table to send outbound traffic through the NAT

Q9: A developer accidentally left an S3 bucket open to the public. How do you remediate this and prevent it from happening again?

A: I would immediately remove public access by adjusting the bucket policy/ACL and enabling S3 Block Public Access on that bucket (and at the account level if appropriate). Then, to prevent recurrence, I’d implement guardrails: for example, use AWS Config rules or IAM SCPs to detect or disallow public buckets, and ensure all buckets have proper access policies and default encryption. I’d also review access logs to verify no sensitive data was accessed while it was public.

Q10: What is the principle of least privilege, and how do you apply it in AWS IAM?

A: The principle of least privilege means giving users and services only the minimum permissions they need to perform their tasks and nothing more. In AWS IAM, I implement this by creating finely-scoped policies (specifying exact allowed actions on specific resources), using IAM roles for services with only the necessary permissions, and regularly reviewing and removing any excessive or unused privileges.

Q11: How do you ensure compliance and audit readiness for your AWS infrastructure?

A: I enable AWS CloudTrail to log all API actions for audit tracking and use AWS Config to continuously evaluate resource configurations against our compliance rules. We enforce best practices like encryption at rest/in transit and IAM least privilege. I also might use AWS Security Hub or third-party audit tools to run compliance checks (for standards like CIS, PCI, etc.) and produce reports. Regular audits and automated alerts for any violations (for example, an unencrypted volume or open security group) help ensure we stay compliant.

Q12: How do you manage Terraform state in a team environment using AWS?

A: We store Terraform state in a remote backend (for example, an S3 bucket with DynamoDB table for state locking in AWS). This allows team members to share state and avoids conflicts – only one person can modify state at a time thanks to the lock. The remote state is secured and versioned, and we manage access to it via IAM, ensuring state files are not stored locally or lost.

Q13: What would you do if a Terraform apply failed due to a state lock or a conflict?

A: If it’s a state lock issue (for instance, the state file is locked from a previous run), I’d clear the lock – for AWS backend that might mean using DynamoDB to remove a stale lock or running terraform force-unlock after confirming no other process is running. If it’s a conflict because something was changed outside of Terraform, I’d import the resource or run a terraform refresh to reconcile state, update the configuration to match the real environment, and then re-run the apply.

Q14: You ran an AWS CloudFormation update and it failed. How do you troubleshoot and roll back the changes?

A: I’d go to the CloudFormation console and check the stack events to see which resource failed and what the error was. From there, I’d fix the underlying issue – for example, correct a parameter or resolve a dependency – and then attempt the update again. CloudFormation will automatically attempt to roll back on failure, but if it gets stuck, I might need to manually intervene (possibly update the stack with a known good configuration or delete/recreate the stack if the failure left it in an unrecoverable state).

Q15: Describe a CI/CD pipeline you have set up for deploying infrastructure or applications to AWS.

A: In one case, I set up a pipeline using Jenkins (and also used AWS CodePipeline in another project). The flow was: a commit in Git triggers the pipeline, which then runs automated tests and builds an artifact or Docker image. If tests pass, the pipeline runs our Infrastructure as Code (Terraform/CloudFormation) to provision/update AWS resources, and then deploys the application (for example, updates the ECS service or pushes the new code to EC2/Beanstalk). We also included approval steps and automated rollbacks on failure to make deployments safe.

Q16: How do you minimize downtime during deployments of a cloud-native application?

A: I use deployment strategies that allow zero-downtime releases, like blue-green or rolling deployments. For example, with blue-green, I deploy the new version to a parallel environment (new set of servers or containers) and then switch over traffic via load balancer or DNS once it’s verified. With rolling deployments (or canary releases), I gradually replace or update instances/pods with the new version so that a portion of traffic is always served by an up-to-date instance and the application never fully goes down during the release.

Q17: You need to deploy a containerized application on AWS. What services would you use and what are the steps?

A: I would use Amazon ECR to store the Docker images and then deploy using a container orchestration service like Amazon ECS or EKS. The steps include: building the Docker image and pushing it to ECR, then creating a task definition (if using ECS) or a Kubernetes deployment (if using EKS) for the application. Next, I’d set up a service (ECS service or Kubernetes service) to run the containers, often behind an Application Load Balancer for traffic. Finally, I’d configure auto-scaling for the tasks/pods and use IaC/pipeline to automate this deployment process.

Q18: If you receive an alert that CPU utilization is high on a critical server, what actions would you take?

A: I would first log in to AWS or our monitoring dashboard to confirm the high CPU and check what's causing it (looking at CloudWatch metrics and possibly the instance logs or processes). If it’s due to legitimate load, I might scale out by adding instances or scale up the instance size temporarily, and then investigate optimizing the workload. If it looks like an abnormal spike (for example, a stuck process or a memory leak leading to swap usage), I’d remediate by restarting or fixing that service, and ensure auto-scaling or proper limits are in place to handle future spikes.

Q19: What are the key differences between Terraform and CloudFormation?

A: Terraform is an open-source Infrastructure as Code tool that works across multiple cloud providers and uses its own state file to track resources, whereas CloudFormation is AWS’s native IaC service that manages AWS resources without an external state file (state is managed by AWS within the stack). Terraform uses HCL for configuration and can provision resources in different clouds or services in one workflow, while CloudFormation uses JSON/YAML templates and is limited to AWS (with deep integration, offering features like change sets, stack policies, and drift detection). In practice, Terraform offers more flexibility for hybrid/multi-cloud environments, and CloudFormation is convenient for AWS-only setups with out-of-the-box integration.

Q20: If you suspect a security breach in your AWS environment, what steps would you take to respond?

A: First, I would contain the incident by isolating affected resources – for example, take compromised EC2 instances offline (stop or quarantine them) and disable any exposed credentials. Next, I’d investigate using CloudTrail logs, CloudWatch logs, and other monitoring data to determine the scope and root cause of the breach. I would rotate any compromised keys or passwords, patch vulnerabilities or misconfigurations that were exploited, and restore clean backups if necessary. Throughout the process, I’d follow our incident response plan, which includes communicating with the security team and stakeholders and later conducting a post-mortem to prevent similar incidents in the future.