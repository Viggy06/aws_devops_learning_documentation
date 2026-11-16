# S3 Static Website and EventBridge Automation

**Concept**
- S3 can host static website files.
- S3 events can also be routed through EventBridge to trigger actions in other AWS services.

**What I worked on**
- I hosted a basic website from an S3 bucket and configured an EventBridge rule to invoke a Lambda function when objects in the bucket were updated.

**How I did it**
- Uploaded an `index.html` file and its related assets to an S3 bucket.
- Enabled static website hosting and set the index document.
- Configured the bucket's EventBridge integration.
- Created an EventBridge rule for the bucket event and selected a Lambda function as the target.
- Tested the rule by updating an object in the bucket.

**Problem it solves**
- The website exercise demonstrates hosting static content without managing a web server.
- The event workflow demonstrates how an upload or object change can start automated processing without a continuously running server.

**Flowchart**
### 1. S3 static website hosting
```mermaid
flowchart TD
    A["Prepare index.html and Assets"] --> B["Create S3 Bucket"]
    B --> C["Upload Website Files"]
    C --> D["Enable Static Website Hosting"]
    D --> E["Set index.html as Root Document"]
    E --> F["Configure Bucket Policy"]
    F --> G["Access Website Endpoint"]
    G --> H["Website Opens in Browser"]
```

### 2. S3 event triggering Lambda
```mermaid
flowchart TD
    A["Upload or Update S3 Object"] --> B["S3 Bucket"]
    B --> C["Enable EventBridge Integration"]
    C --> D["Create EventBridge Rule"]
    D --> E["Configure Object Event Filter"]
    E --> F["Select Lambda as Target"]
    F --> G["Lambda Function Triggered"]
```
