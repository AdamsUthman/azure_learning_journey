# Phase 5 — Data & Secrets Security

**Focus:** Protecting data at rest, managing secrets, and enforcing access policies.

---

## Storage Security

### Steps:

1. **Create a Storage Account**
   - Resource Group: `rg-cloud-security-labs`
   - Name: `st-lab-phase5`
   - Region: `East US`
   - Standard performance, general-purpose v2
   - Default settings for networking and access

2. **Check VM Access**
   - Ensure VMs can access storage according to NSG rules and subnet.
   - Guest-level diagnostics skipped due to Python 2 requirement and extra monitoring charges.

### Observations:
- Storage account created successfully.
- VMs could reach the storage account based on NSG rules.
- Guest-level diagnostics were skipped.

### Takeaways:
- Proper storage configuration and controlled access are essential for data security.
- Even optional features like diagnostics may have prerequisites (Python 2) and cost implications.

---

## Secrets Management

### Steps:

1. **Create Azure Key Vault**
   - Resource Group: `rg-cloud-security-labs`
   - Name: `kv-lab-phase5`
   - Region: `East US`
   - Use default settings for networking (allow access from all networks initially).

2. **Assign RBAC Roles**
   - Cloud Admin Group: Key Vault Secrets User (can create/edit secrets)
   - Security Team: Key Vault Secrets Reader (can view secrets but not edit/delete)
   - ⚠ Important: Assign roles **before** creating secrets, otherwise they may not be visible to intended users.

3. **Add Secret**
   - Secret Name: `vmAdminPassword`
   - Value: Admin password for lab VMs
   - Create using Cloud Admin account
   - Security Team can now view it.

### Observations:
- Secret creation successful after assigning roles.
- Roles worked as intended: Cloud Admin could edit, Security Team could read.
- Creating secrets before role assignment caused them not to appear for Security Team.

### Takeaways:
- Always assign roles before secret creation.
- RBAC enforces least privilege effectively.
- Key Vault centralizes secret management securely.

---

## Monitoring & Alerts

### Steps:

1. Enabled Activity Logs for the Resource Group.
2. Administrative events (like NSG changes, VM creation/deletion) were visible.
3. Alerts attempted via action group, but test alert emails did not fire (subscription may require Azure Monitor/Log Analytics for full functionality).

### Observations:
- Activity Log accurately captured administrative changes.
- Email alerts did not trigger in lab environment.
- Manual NSG/VM changes confirmed in logs.

### Takeaways:
- Alerts require proper configuration and subscription support.
- Logging is critical for visibility, even if alerts fail initially.