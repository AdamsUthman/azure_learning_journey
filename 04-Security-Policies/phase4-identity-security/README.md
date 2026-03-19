## Phase 4 — Security Policies

### Objective
- Implement identity security and emergency access.

### Key Steps

- Enable Security Defaults in Microsoft Entra ID (enforces MFA).

- Create Break-Glass Admin account with Global Administrator role.

- Test MFA enforcement:

    - noc-user, security-user, cloud-admin

- Test Break-Glass Admin login (emergency access).

- Review sign-in logs for all users.

- Document observations and takeaways.

### Observations
- MFA was required for all users, including break-glass (expected with Security Defaults).

- RBAC roles continued to enforce correct access levels.

- Sign-in logs accurately recorded all logins and MFA prompts.

- Break-glass account successfully allowed emergency login.


### Takeaways / Security Insights
- Security Defaults provides a baseline for identity security.

- MFA significantly reduces risk of account compromise.

- Break-glass accounts are crucial for emergency recovery.

- Testing with different roles validates policies and compliance.


### Below is a screenshot of the sign-in logs showing users logged in successfully with MFA enabled
![](/images/signin-logs.png)