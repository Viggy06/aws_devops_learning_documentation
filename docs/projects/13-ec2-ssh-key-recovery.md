# EC2 SSH Key Recovery

**Concept**
EC2 key pairs are used for SSH access to Linux instances. If the configured public key is no longer available, access can be recovered through an alternate access path or by updating the authorized keys on the instance.

**What I worked on**
I practised recovering access with EC2 Instance Connect and replacing the public key. I also worked through a helper-instance method using the affected instance's EBS volume.

**How I did it**
- Used EC2 Instance Connect to access the instance through a temporary key.
- Created a replacement key pair and updated the public key in the instance's `authorized_keys` file.
- For the volume-based method, attached the affected root EBS volume to a helper instance, updated the key, then reattached the volume.
- Tested SSH access with the replacement key.

**Problem it solves**
It provides recovery options when an administrator loses the original SSH key, avoiding an unnecessary rebuild of the instance.

**Flowchart**
### 1. Recover access using EC2 Instance Connect
```mermaid
flowchart TD
    A["SSH Key Lost"] --> B["Prepare Primary and Helper EC2"]
    B --> C["Detach Primary EBS Volume"]
    C --> D["Attach Volume to Helper EC2"]
    D --> E["Mount Volume"]
    E --> F["Replace Public Key in authorized_keys"]
    F --> G["Unmount and Detach Volume"]
    G --> H["Reattach Volume to Primary EC2"]
    H --> I["Start Primary EC2"]
    I --> J["Connect Using New SSH Key"]

```

### 2. Recover access using a helper EC2 and EBS
```mermaid
flowchart TD
    A["SSH Key Lost"] --> B["Prepare Primary and Helper EC2"]
    B --> C["Detach Primary EBS Volume"]
    C --> D["Attach Volume to Helper EC2"]
    D --> E["Mount Volume"]
    E --> F["Replace Public Key in authorized_keys"]
    F --> G["Unmount and Detach Volume"]
    G --> H["Reattach Volume to Primary EC2"]
    H --> I["Start Primary EC2"]
    I --> J["Connect Using New SSH Key"]
```
