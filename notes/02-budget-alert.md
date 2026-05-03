\# 💰 Budget Alert Setup



\## 🎯 Objective



The objective of this step was to reduce financial risk by creating an AWS budget alert before deploying lab resources.



\## ✅ Actions Completed



\- Opened AWS Billing and Cost Management

\- Created a zero-spend budget for the lab account

\- Configured the budget threshold at a low dollar amount

\- Added an email recipient for cost notifications

\- Verified that the budget was created successfully



\## 🛡️ Security and Operational Reasoning



Cloud environments can generate unexpected costs if resources are misconfigured, left running, or abused. A budget alert helps identify unexpected spending early and supports better cloud governance.



Although a budget alert is not a direct technical security control, it supports operational awareness by notifying the account owner when spending activity occurs.



\## 📉 Risk Reduced



\- Unexpected AWS charges

\- Unmonitored resource usage

\- Cost impact from accidental misconfiguration

\- Cost impact from unauthorized resource creation

\- Delayed awareness of unusual account activity



\## 📸 Evidence



Screenshot captured:



\- \[Budget alert created](../screenshots/02-budget-alert-created.png)



\## 🔒 Security Considerations



Sensitive details such as account identifiers and billing-related information should be removed or redacted before publishing.



\## 🧠 SOC Analyst Notes



Cost monitoring is part of cloud security operations. Unexpected spending may indicate misconfigured resources, abuse, or unauthorized activity. Budget alerts provide an early warning signal for abnormal account activity and help support responsible cloud resource management.

