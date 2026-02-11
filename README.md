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

#### Task 1: Enable Azure Monitor and Log Analytics
<img width="930" height="383" alt="ex4-log-analytics-workspace" src="https://github.com/user-attachments/assets/d6f9f6fe-3368-4a2b-81c4-17d8fb052df2" />

### Exercise 4: Storage Account Logging and Monitoring

This exercise focuses on configuring Azure Storage diagnostic logging and validating log ingestion into Azure Monitor Log Analytics. The goal is to generate storage activity and confirm visibility using KQL queries.

Objectives
Create a storage account for centralised logging
Enable diagnostic settings for Azure Blob Storage
Send logs and metrics to Log Analytics
Generate storage activity to validate ingestion
Query logs using KQL

Azure Resources Used:
Azure Storage Account
Azure Blob Storage
Azure Monitor
Log Analytics Workspace
Azure Portal

Configuration Steps:
Created a standard Azure Storage account for logging.
Navigated to Monitoring → Diagnostic settings.
Selected the Blob service under the storage account.

Created a diagnostic setting with:
StorageRead
StorageWrite
StorageDelete
Transaction metrics
Sent all logs and metrics to the Log Analytics workspace.
Validation Process

To generate log data:
Created a blob container
Uploaded a test file
Deleted the file
Deleted the container
After a short ingestion delay, logs were queried in Log Analytics.

KQL query used:
StorageBlobLogs
| order by TimeGenerated desc

Evidence
Screenshots captured during this exercise:
ex4-blob-diagnostic-settings.png
<img width="932" height="389" alt="ex4-blob-diagnostic-settings" src="https://github.com/user-attachments/assets/0408df17-be29-42f4-ad03-a4f3c29a8964" />

ex4-storagebloblogs.png
<img width="932" height="387" alt="ex4-storagebloblogs" src="https://github.com/user-attachments/assets/f478b331-468c-4a01-8521-83b8fdab3680" />

These confirm diagnostic settings and successful log ingestion.

Key Learnings
Azure Storage does not log activity by default.
Diagnostic settings must be configured per storage service.
Log ingestion requires actual resource activity.
Validation using KQL is essential to confirm visibility.
Relevance to Security Operations

This exercise mirrors real-world SOC workflows:
Enabling telemetry
Verifying data ingestion
Using logs for investigation and auditing
Understanding Azure-native logging architecture
