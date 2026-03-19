# Phase 4 — Monitoring & Alerts

## Objective

The purpose of this lab is to understand how to monitor Azure resources and detect changes using:

- Azure Activity Log
- Alert Rules
- Action Groups
- Storage for diagnostics

Monitoring is essential for cloud security to detect unauthorized changes, failures, or suspicious activity.

---

## Lab Environment

Subscription: Azure for Students  
Resource Group: rg-cloud-security-labs  
Region: eastus

Resources used:

- Virtual Machines
- Network Security Group
- Storage Account
- Azure Monitor
- Activity Log Alerts
- Action Group (Email notification)

---

## Step 1 — View Activity Log

Azure Portal → Monitor → Activity Log

Filter by:

- Resource group: rg-cloud-security-labs
- Time range: Last 24 hours

Observation:

All resource changes are recorded in Activity Log.

Examples seen:

- NSG rule changes
- VM start/stop
- Role assignments
- Resource updates

![](/images/activity-log.png)
---

## Step 2 — Create Storage Account for Diagnostics

Azure Portal → Storage Accounts → Create

Settings:

Name: stcloudsecuritylabs  
Region: eastus  
Performance: Standard  
Redundancy: LRS  
Primary workload: Other

Security:

- Secure transfer required enabled
- Public access disabled

Observation:

Storage account can store diagnostic logs.

![](/images/storage-account.png)
---

## Step 3 — Create Action Group

Azure Portal → Monitor → Alerts → Action groups → Create

Name: lab-alert-group  
Display name: LabAlert

Notification type:

Email

Add email address

Review + Create

Observation:

Action group sends notifications when alerts trigger.

![](/images/action-group.png)
---

## Step 4 — Create Alert Rule

Azure Portal → Monitor → Alerts → Create → Alert rule

Scope:

Resource group: rg-cloud-security-labs

Condition:

Signal name:
Activity Log Alert Activated

Category:
Administrative

Action group:
lab-alert-group

Name:
lab-alert-rule

Create rule

Observation:

Alert rule triggers when administrative activity occurs.

![](/images/alert-rule.png)
---

## Step 5 — Test Alert

Test actions:

- Delete NSG rule
- Start / Stop VM
- Modify resource

Check:

Monitor → Activity Log  
Monitor → Alerts  
Email inbox

Observation:

Activity appears in Activity Log.
Alert rule may not always send email in student subscription.

---

## Step 6 — Diagnostics (Attempt)

Enabled diagnostics for VM.

Azure showed warning:

Linux Diagnostics extension deprecated.

Observation:

Azure Monitor Agent is replacing old diagnostics extensions.

---

## Observations

- Activity Log records all control plane actions
- Alerts detect administrative changes
- Action groups send notifications
- Storage can store diagnostic logs
- Some alerts may not trigger in student subscription

---

## Security Insights

- Monitoring is required for cloud security
- Alerts help detect unauthorized changes
- Logs help investigate incidents
- Always enable logging in production

---

## Takeaways

- Azure Monitor provides visibility
- Alerts must be tested after creation
- Activity Log is critical for auditing
- Monitoring is part of cloud security architecture

---
