# Adams' Azure Learning Journey

## Overview
This repository documents my **hands-on Azure learning journey**, focused on cloud security, RBAC, NSG configuration, and VM deployment.  
It captures all practical labs, observations, and insights from each phase, along with screenshots, commands, and takeaways.

The purpose of this repo is to:
- Track learning progress
- Document labs and exercises
- Validate skills with hands-on practice
- Serve as a reference for future projects or certifications

---

## Folder Structure
```text
Azure-Learning-Journey/
├─ RBAC-Labs/                # Role-Based Access Control labs
│   ├─ phase1-user-setup/
│   ├─ phase2-NSG-configuration/
│   ├─ phase3-VM-testing/
│   └─ README.md
├─ Networking-Labs/          # Networking & subnetting exercises
├─ VM-Deployments/           # Virtual Machine deployment practice
├─ Security-Policies/        # Conditional access, MFA, break-glass admin accounts
├─ Notes/                    # Key insights, cheatsheets, and concepts
└─ README.md                 # Root folder overview

---

## Learning Objectives
- Understand **Azure fundamentals**, including subscriptions, resource groups, and virtual networks
- Implement **Role-Based Access Control (RBAC)** for secure access management
- Configure **Network Security Groups (NSGs)** for subnet-level traffic control
- Deploy **virtual machines** and test connectivity between subnets
- Explore **Azure security best practices** such as MFA, conditional access, and break-glass accounts
- Develop a structured **documentation habit** using Markdown, GitHub, and screenshots

---

## How to Use This Repository
1. Navigate to each lab folder to access **step-by-step exercises**
2. Review the `README.md` in each lab folder for:
   - Lab setup and objectives
   - Commands and scripts used
   - Observations and takeaways
   - Screenshots for validation
3. Document your own findings and mark completed steps
4. Use the **Notes folder** for extra learning, cheat sheets, or reminders

---

## Key Takeaways
- Hands-on labs reinforce **least privilege principles** and proper access management
- NSG rules and VM connectivity require careful planning, especially with priority orders
- Testing with multiple accounts and IP scenarios is essential to validate security controls
- Maintaining organized documentation (folders, Markdown, screenshots) accelerates learning
- Cloud Shell sessions are ephemeral — always save scripts or outputs to persistent storage

---

## Recommendations
- Always test access with **non-admin accounts** to verify RBAC
- Use **private IPs for VM-to-VM tests** to avoid unnecessary public exposure
- Keep screenshots **masked or blurred** to protect sensitive info like Object IDs
- Update this repo continuously as your Azure skills grow
- Pair labs with learning resources like **Microsoft Learn, Azure docs, and certification guides**

---

## Notes
This repository is intended as a **personal reference and study tool** for Azure learning and cloud security.  
It can serve as a foundation for **Azure certifications**, cloud engineering roles, and security projects.
