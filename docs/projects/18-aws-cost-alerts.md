# AWS Billing Alerts and Budgets

**Concept**
CloudWatch billing alarms and AWS Budgets help track cloud spending and notify account owners when configured cost thresholds are reached.

**What I worked on**
I created a billing alarm for a $5 threshold with an SNS email notification and configured an AWS Budget.

**How I did it**
- Created an SNS topic and configured the email subscription.
- Created a CloudWatch billing alarm using the billing metric.
- Set the alarm threshold to $5 and connected it to the SNS topic.
- Created an AWS Budget to track account spending.

**Problem it solves**
Cost alerts provide an early warning when spending reaches a chosen limit and help avoid unexpected charges during hands-on testing.

**Flowchart**
```mermaid
flowchart TD
    A["Enable Billing Alerts in Billing Preferences"] --> B["CloudWatch Billing Metrics"]
    B --> C["Create Billing Alarm"]
    C --> D["Set Threshold: $5"]
    D --> E{"Estimated Charges Above Threshold?"}

    E -->|"Yes"| F["Alarm Enters ALARM State"]
    F --> G["SNS Topic"]
    G --> H["Email Subscriber"]

    E -->|"No"| B

    I["Create AWS Budget"] --> J["Configure Budget Threshold"]
    J --> K["Configure Budget Notifications"]
    K --> L["Email Notification"]
```