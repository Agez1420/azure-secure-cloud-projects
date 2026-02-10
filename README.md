# azure-secure-cloud-projects
A startup migrated its infrastructure to the Azure cloud, but security controls were not yet properly configured. A developer exposed sensitive data stored in Azure to the public, an attacker gained access and stole credentials because MFA was not enabled. The company lost money as a result, as there were no billing alerts or monitoring in place.

### Exercise 1: Entra ID User and RBAC
Created an Entra ID user and assigned the Security Administrator role.
This limits access to security controls and follows least privilege principles.

Evidence:
- Entra ID user creation
- Security Administrator role assignment

<img width="1917" height="910" alt="screenshots_ex1-user-created" src="https://github.com/user-attachments/assets/ed9fdbcb-ef4a-4af8-8c71-e835de817c07" />
<img width="1916" height="891" alt="screenshpts_ex1-role-assigned" src="https://github.com/user-attachments/assets/b74e2d3a-8257-4608-bc08-b2851738eeaa" />

### Exercise 2: MFA Enforcement (Security Defaults)
Conditional Access policy creation requires Entra ID Premium P1.
As an alternative, Security Defaults were enabled to enforce MFA and block legacy authentication.

This approach aligns with Microsoft baseline security recommendations for small environments.

Evidence:
- Security Defaults enabled

<img width="1865" height="825" alt="ex2-security-defaults-enabled" src="https://github.com/user-attachments/assets/84094ed8-d1c1-45d9-9990-135ca484fd3d" />

### Exercise 3: Enable Azure Monitor and Log Analytics and Set Up Cost Alerts.

Accessed Azure Monitor Logs using the new Queries Hub UI.
No data was present as no resources were generating logs yet.
<img width="1846" height="766" alt="image" src="https://github.com/user-attachments/assets/5596dd26-78e3-4228-b2cb-27c1a6360b96" />
