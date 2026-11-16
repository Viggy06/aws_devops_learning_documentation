# VPC Flow Logs

**Concept**
VPC Flow Logs capture metadata about IP traffic to and from a VPC, subnet or network interface. They can be delivered to CloudWatch Logs or S3.

**What I worked on**
I configured VPC Flow Logs with CloudWatch Logs as the destination.

**How I did it**
- Created a CloudWatch log group.
- Prepared the IAM role needed for log delivery.
- Enabled Flow Logs for the selected VPC network scope.
- Selected CloudWatch Logs as the destination and checked the log delivery.

**Problem it solves**
Flow Logs help investigate connectivity issues, identify rejected traffic, and review whether security-group or network ACL rules are behaving as expected. They record flow metadata, not full packet contents.
