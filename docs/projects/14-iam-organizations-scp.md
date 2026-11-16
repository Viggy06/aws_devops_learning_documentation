# IAM, AWS Organizations and Service Control Policies

**Concept**
- IAM policies define permissions for identities and resources.
- AWS Organizations manages multiple accounts, and Service Control Policies (SCPs) set the maximum permissions available in member accounts.

**What I worked on**
- I created an Organization and a member account, applied an SCP restricting EC2 instance types in a test account, and set up an IAM Identity Center user with a limited permission set.

**How I did it**
- Created the Organization and added a member account.
- Created and attached an SCP that restricted the test account to the selected EC2 instance type.
- Enabled IAM Identity Center, created a user and permission set, and assigned access to the account.

**Problem it solves**
- These controls help manage access across accounts and apply guardrails centrally.
- An SCP limits what identities can do; it does not grant permissions by itself.

**Flowchart**
### 1. AWS Organizations and SCP
```mermaid
flowchart LR
    A["Create AWS Organization"] --> B["Create Member Account"]
    B --> C["Create SCP Policy"]
    C --> D["Restrict EC2 Instance Types"]
    D --> E["Allow Only t2.micro"]
    E --> F["Attach SCP to Test Account"]
    F --> G["Test EC2 Launch"]
    G --> H{"Requested Instance Type?"}
    H -->|"t2.micro"| I["Allowed by SCP"]
    H -->|"Other Type"| J["Explicitly Denied by SCP"]
```

### 2. IAM Identity Center
```mermaid
flowchart TD
    A["Enable IAM Identity Center"] --> B["Create User"]
    B --> C["Create Permission Set"]
    C --> D["Assign User to AWS Account"]
    D --> E["Permission Set Creates IAM Role in Account"]
    E --> F["User Signs In Through Access Portal"]
    F --> G["Access Account with Assigned Permissions"]
```
