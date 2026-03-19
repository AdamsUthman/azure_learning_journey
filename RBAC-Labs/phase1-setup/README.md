## Phase 1 — User & Role Setup (RBAC)

**Lab Setup:**
- **Environment:** Azure Student Subscription  
- **Resource Group:** `rg-cloud-security-labs`  
- **Users:** `noc-user`, `security-user`, `cloud-admin`  
- **Groups:** `NOC-Team`, `Security-Team`, `Cloud-Admins`  
- **Roles Assigned:**
  - `NOC-Team` → Reader  
  - `Security-Team` → Contributor  
  - `Cloud-Admins` → Owner  

**Steps Taken:**
1. Created users in Microsoft Entra ID
2. Created groups and added users
3. Created resource group `rg-cloud-security-labs`
4. Assigned RBAC roles to groups
5. Logged in as each user to verify access
6. Documented observations

**Observations:**
- NOC-Team users can view resources but cannot create or modify them
- Security-Team users can create and modify resources but cannot delete the resource group
- Cloud-Admins have full control over the resource group
- RBAC correctly enforces least privilege

**Takeaways / Security Insights:**
- Using groups instead of individual users simplifies access management
- Proper RBAC configuration reduces risk of accidental or malicious changes
- Testing with different accounts validates security and access policies

## Screenshots
*(All sensitive info, such as Object IDs, is masked or blurred.)*  

![/RBAC%20Labs/images/noc-user-error.png](/RBAC%20Labs/images/noc-user-error.png)
NOC user blocked from creating VM
*****************************************************************************************************************************************************************************
![/RBAC%20Labs/images/vm-create-success.png](/RBAC%20Labs/images/vm-create-success.png)
Security-Team user successfully created VM
*****************************************************************************************************************************************************************************

![/RBAC%20Labs/images/cloudadmin-full-access.png](/RBAC%20Labs/images/cloudadmin-full-access.png)
Cloud-Admins full permissions view