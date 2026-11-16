# Application Load Balancer with HTTPS and Host-Based Routing

**Concept**
An Application Load Balancer routes HTTP and HTTPS requests to target groups based on listener rules, including the hostname in a request.

**What I worked on**
I configured an ALB with EC2 target groups, added HTTPS using an ACM certificate, and routed two hostnames to separate target groups. I also tested load-balancer stickiness.

**How I did it**
- Created the ALB and target groups for the EC2 instances.
- Requested an ACM certificate and added the Route 53 DNS validation record.
- Attached the issued certificate to the ALB HTTPS listener.
- Created host-based listener rules and Route 53 records for the domains.
- Tested routing and configured a load-balancer-generated sticky session.

**Problem it solves**
One ALB can provide HTTPS access and route multiple domains or applications to the correct backend without exposing each EC2 instance directly.

**Flowchart**
```mermaid
flowchart TD
    ACM["Request ACM Certificate"] --> DNS["Create DNS Validation Record"]
    DNS --> CERT["Certificate Validated"]
    CERT --> LISTENER["Configure ALB HTTPS Listener :443"]

    USER["Client / Browser"] --> R53["Route 53 Domain Record"]
    R53 --> ALB["Application Load Balancer"]
    LISTENER --> ALB

    ALB --> RULE{"Host-based Routing"}

    RULE -->|"Domain A"| TG1["Target Group A"]
    RULE -->|"Domain B"| TG2["Target Group B"]

    TG1 --> EC2A["EC2 Instance A"]
    TG2 --> EC2B["EC2 Instance B"]

    EC2A --> HC["Target Group Health Checks"]
    EC2B --> HC
```