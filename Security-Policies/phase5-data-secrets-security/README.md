# PHASE 5 — Data & Secrets Security

**Focus:** Protecting data at rest, managing secrets, and enforcing access policies.

### Storage Security
- Created storage accounts for diagnostic and lab data
- Checked NSG rules and subnet access for VMs accessing storage
- **Observation:** Storage account created successfully; guest-level diagnostics were skipped due to Python 2 requirement and potential extra charges
- **Takeaway:** Proper storage configuration and controlled access are essential for data security

### Secrets Management
- Planned creation of Azure Key Vault for storing secrets
- Configured RBAC to control access to secrets
- **Observation:** Not fully implemented in lab
- **Takeaway:** Using Key Vault and RBAC for secrets centralizes management and enforces least privilege

### Monitoring & Alerts
- Activity Logs were enabled for resource group actions
- Administrative events were visible in Activity Log
- **Observation:** Alerts did not fire via email or test action; Activity Log recorded changes correctly
- **Takeaway:** Alerting may require additional configuration or subscription-level support (e.g., Azure Monitor / Log Analytics)