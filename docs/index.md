# AWS & Infrastructure – Practical Work

A short index of the AWS and Linux infrastructure tasks I have worked on. Each note covers the concept, what I configured, how I approached it, and the problem it addresses.

## 1. AWS practical works

| Document | Work covered | Impact |
|---|---|---|
| [EC2 and IAM role-based S3 access](projects/01-ec2-iam-s3-access.md) | Launching and accessing EC2; using an instance role to access S3 | Allows EC2 to access S3 securely using temporary IAM credentials instead of storing access keys on the instance. |
| [VPC public and private networking](projects/02-vpc-public-private-networking.md) | Subnets, route tables, bastion access, NAT Gateway and S3 Gateway Endpoint | Keeping private instance isolated, allowing only ssh through public instance and private S3 access |
| [ALB with HTTPS and host-based routing](projects/03-alb-https-host-routing.md) | ACM certificate, Route 53 validation, listeners and target groups | Secures application traffic with HTTPS, Routing traffics to multiple backend through LB, ACM and Route53 integration |
| [EC2 Auto Scaling](projects/04-ec2-auto-scaling.md) | Launch template, multi-AZ Auto Scaling Group and CPU-based scaling | Automatically scaleup/down EC2 instance based on CPU utilization |
| [S3 static website and event automation](projects/05-s3-static-website-eventbridge.md) | Static website hosting and S3 events routed to Lambda through EventBridge | Hosts static websites without web servers and triggers Lambda automatically when S3 objects are updated. |
| [CloudFront with a private S3 origin](projects/06-cloudfront-private-s3-origin.md) | CDN distribution and Origin Access Control | cached content through CloudFront while restricting direct access to the S3 bucket. |
| [Flask deployment on ECS Fargate](projects/07-ecs-fargate-flask.md) | Docker image, ECR, ECS task definition, service and health check | Runs containerized applications without managing EC2 worker instances and maintains the desired number of tasks. |
| [Private RDS MySQL connectivity](projects/08-ec2-private-rds-mysql.md) | EC2-to-RDS connection controlled by security groups | Enables secure private database connectivity |
| [API using Lambda and DynamoDB](projects/09-lambda-api-dynamodb.md) | DynamoDB table, Lambda permissions and API Gateway | Exposes database operations through a serverless API. |
| [VPC deployment with CloudFormation](projects/10-cloudformation-vpc.md) | YAML template uploaded to S3 and deployed as a stack | Creates infrastructure through reusable templates. |
| [EC2 monitoring with CloudWatch](projects/11-cloudwatch-ec2-monitoring.md) | CloudWatch Agent, IAM role, metrics, alarm and notification | Tracks instance metrics and triggers alerts. |
| [EC2 access with Systems Manager](projects/12-ssm-session-manager.md) | Session Manager access to managed instances | Accesses private EC2 without SSH keys. |
| [EC2 SSH key recovery](projects/13-ec2-ssh-key-recovery.md) | Recovering access and replacing an instance's authorized key | Restores SSH access to an existing instance without needing to rebuild the entire server. |
| [IAM, Organizations and SCP](projects/14-iam-organizations-scp.md) | Role assumption, member accounts, policy restrictions and Identity Center | Centralizes permissions and account-level restrictions. |
| [Fail2ban on EC2](projects/15-fail2ban-ec2-protection.md) | Detecting repeated login failures and applying host-level bans | Automatically blocks IP addresses after repeated failed authentication attempts, reducing exposure to brute-force attacks (rate-limiting on Http/Https). |
| [Centralized EC2 monitoring with Nagios](projects/16-nagios-core-nrpe-monitoring.md) | Nagios Core, NRPE, remote checks and notifications | Provides a central dashboard to monitor multiple EC2 instances and notify administrators about configured host or service failures. |
| [Route 53 private DNS](projects/17-route53-private-dns.md) | Resolving internal resources using a private hosted zone | Allows internal resources to communicate using private DNS names instead of depending on fixed IP addresses |
| [AWS billing alerts and budgets](projects/18-aws-cost-alerts.md) | Billing alarm, SNS notification and budget tracking | Helps track spending and avoid unexpected costs. |

These are hands-on lab exercises and learning implementations. They are not presented as production deployments.

## 2. What I Learned Overall

Working through these AWS exercises helped me understand how the main parts of an environment fit together: networking controls connectivity, IAM controls access, compute and containers run applications, and monitoring helps identify issues.

### 3. Hands-on Work

- Set up VPC networking with public and private subnets, route tables, an Internet Gateway, NAT Gateway and an S3 Gateway Endpoint.
- Worked with EC2 access, IAM roles and Security Groups, including private-instance access and SSH recovery.
- Configured an Application Load Balancer with HTTPS, ACM certificates, Route 53 records and host-based routing.
- Created an Auto Scaling Group and tested CPU-based scaling using CloudWatch metrics.
- Hosted a static website in S3 and connected S3 events to Lambda through EventBridge.
- Built a Flask container, pushed the image to ECR and ran it as an ECS Fargate service.
- Connected EC2 to a private RDS MySQL instance using Security Group rules.
- Set up CloudWatch Agent and VPC Flow Logs, and worked with Fail2ban and Nagios/NRPE for host security and monitoring.
- Practised CloudFormation, Systems Manager, AWS Organizations, IAM Identity Center, private DNS and billing alerts.

These exercises gave me a practical base for understanding and troubleshooting common AWS setups. I still have more to learn, especially by working with an existing team environment and real operational tasks.

## 4. What I'd Like to Work on Next

I'd like to use my available time to contribute to the team's work and build on the AWS practice I've done so far.

- **Pick up tasks:** Please let me know where I can help or whether there are pending tasks I could take on.
- **Work on real project tasks:** I'd like to apply what I've learned to the team's environment and gradually take on production-related work with guidance.
- **Understand the AWS setup:** Appropriate access to the AWS account would help me review the existing infrastructure, understand how the services are connected, and assist with troubleshooting or debugging when needed. I'm happy to start with read-only access and use whichever permissions are suitable.

I had also spoken to Yatin Sir and Kartik Sir about getting more involved in the actual work. I wanted to mention it here as well and check where I could start contributing.
