\# 🧹 Cleanup: Test IAM Resources



\## 🎯 Objective



The objective of this step was to remove temporary IAM resources that were created only for testing the Unauthorized API Calls detection.



\## ✅ Actions Completed



\- Deleted the temporary IAM user named `readonly-test-user`

\- Deleted the temporary IAM group named `ReadOnlyTestGroup`

\- Confirmed that the test resources were no longer needed after the access denied event was generated and documented



\## 🛡️ Security Reasoning



Temporary test users and groups should be removed after testing to reduce unnecessary identities and permissions in the AWS account. Leaving unused IAM resources in place can increase the attack surface and make access management harder to audit.



Removing test resources also keeps the lab environment clean and reduces confusion during future monitoring, troubleshooting, or access reviews.



\## 📉 Risk Reduced



\- Unused IAM identities

\- Unnecessary permissions

\- Identity sprawl

\- Increased attack surface

\- Confusion during future access reviews



\## 📸 Evidence



Screenshots captured:



\- \[Read-only test user deleted](../screenshots/14-readonly-test-user-deleted.png)

\- \[Read-only test group deleted](../screenshots/15-readonly-test-group-deleted.png)



\## 🔒 Security Considerations



Before publishing this project, screenshots should be reviewed and sensitive information should be removed or redacted, including:



\- AWS account IDs

\- ARNs

\- Usernames

\- Browser URLs

\- Account dropdown details



\## 🧠 SOC Analyst Notes



Cleaning up temporary resources is an important part of secure cloud operations. Security testing should include not only detection validation, but also removal of test artifacts that are no longer required.



This cleanup step demonstrates responsible cloud hygiene and helps ensure the AWS account remains easier to monitor and manage.

