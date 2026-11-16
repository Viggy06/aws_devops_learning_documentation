# Route 53 Private DNS

**Concept**
- A Route 53 private hosted zone resolves DNS names only within the VPCs associated with that hosted zone.

**What I worked on**
- I created a private hosted zone, associated it with a VPC, and configured a record for an internal resource.

**How I did it**
- Created the private hosted zone using the internal domain name.
- Associated the zone with the target VPC.
- Added a DNS record pointing to the resource's private address.
- Tested name resolution from an instance in the associated VPC.

**Problem it solves**
- Applications and administrators can use internal DNS names instead of relying on instance IP addresses or exposing internal resources through public DNS.

**Flowchart**
```mermaid
flowchart LR
    A["Create Two EC2 Instances in Same VPC"] --> B["Create Private Hosted Zone"]
    B --> C["Associate Hosted Zone with VPC"]
    C --> D["Create A Record"]
    D --> E["Map db.mytestapp.com to Private EC2 IP"]

    F["Client EC2 Instance"] --> G["DNS Lookup"]
    E --> H["Route 53 Private Hosted Zone"]
    G --> H
    H --> I["Return Private IP Address"]
    I --> J["Connect to Target EC2 Using DNS Name"]
```
