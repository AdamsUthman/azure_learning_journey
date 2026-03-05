# RBAC Lab - Azure Cloud Security

## Objective
The purpose of this lab is to understand and implement **Role-Based Access Control (RBAC)** in Microsoft Azure. This lab demonstrates how to:

- Create users and groups in **Microsoft Entra ID**
- Assign users to groups
- Assign RBAC roles to groups for a resource group
- Test the principle of **least privilege** by logging in as different users

This is a foundational lab for cloud security, ensuring proper access management and minimizing risk.

## Lab Setup
**Environment:**  
- Azure Student Subscription  
- Resource Group: `rg-cloud-security-labs`  
- Users: `noc-user`, `security-user`, `cloud-admin`  
- Groups: `NOC-Team`, `Security-Team`, `Cloud-Admins`  
- Roles Assigned:  
  - NOC-Team → Reader  
  - Security-Team → Contributor  
  - Cloud-Admins → Owner

**Steps Taken:**  
1. Created users in Microsoft Entra ID  
2. Created groups and added users  
3. Created a resource group `rg-cloud-security-labs`  
4. Assigned RBAC roles to groups  
5. Logged in as each user to verify access  
6. Documented observations

## Observations
- NOC-Team users can **view resources** but cannot create or modify them  
- Security-Team users can **create and modify resources** but cannot delete the resource group  
- Cloud-Admins have **full control** over the resource group  
- RBAC correctly enforces **least privilege**  

## Takeaways / Security Insights
- Using **groups instead of individual users** simplifies access management  
- Proper RBAC configuration reduces risk of accidental or malicious changes  
- Testing with different accounts validates security and access policies  

## Screenshots
*(All sensitive info, such as Object IDs, is masked or blurred.)*  
- "images/noc-user-error.img" - NOC user blocked from creating VM 


