\# 🚫 Unauthorized API Calls Detection Test



\## 🎯 Objective



The objective of this step was to test the Unauthorized API Calls detection by generating a controlled access denied event in AWS.



\## 🧪 Test Setup



A temporary read-only IAM user was created to simulate a user with limited permissions. The user was assigned read-only permissions and then used to attempt an administrative action that should not be allowed.



\## ✅ Actions Completed



\- Created a read-only test user named `readonly-test-user`

\- Signed in as the read-only test user

\- Attempted to create a new IAM user named `blocked-test-user`

\- Generated an access denied event

\- Confirmed that the CloudWatch alarm showed unauthorized API activity

\- Confirmed that the SNS email subscription was active for alarm notifications



\## 🔁 Detection Flow



```text

Read-only user attempted restricted IAM action

&#x20;       ↓

AWS denied the CreateUser action

&#x20;       ↓

CloudTrail recorded the denied API event

&#x20;       ↓

CloudWatch metric filter matched the event

&#x20;       ↓

CloudWatch alarm showed unauthorized API activity

&#x20;       ↓

SNS notification channel was configured and confirmed

```



\## 📊 Result



The detection test successfully generated an access denied event. The read-only user attempted to create a new IAM user, but AWS denied the action because the user did not have permission to perform `iam:CreateUser`.



The CloudWatch metric filter and alarm were configured to detect unauthorized API activity. The alarm showed metric activity after the denied event was generated, confirming that the detection pipeline was working as expected.



\## 📸 Evidence



Screenshots captured:



\- \[Read-only test user created](../screenshots/11-readonly-test-user-created.png)

\- \[Access denied test event](../screenshots/12-access-denied-test-event.png)

\- \[Unauthorized API alarm triggered](../screenshots/13-unauthorized-api-alarm-triggered.png)



Supporting screenshots:



\- \[Unauthorized API metric filter created](../screenshots/08-unauthorized-api-metric-filter.png)

\- \[Unauthorized API alarm created](../screenshots/09-unauthorized-api-alarm-created.png)

\- \[SNS email subscription confirmed](../screenshots/10-sns-email-confirmed.png)



\## 🔒 Security Considerations



Before publishing this project, screenshots should be reviewed and sensitive information should be removed or redacted, including:



\- AWS account IDs

\- ARNs

\- Usernames

\- Email addresses

\- IP addresses

\- SNS subscription details

\- Browser URLs

\- CloudWatch URLs



\## 🧠 SOC Analyst Notes



This test validates that unauthorized IAM activity can be generated and documented in a controlled way. Access denied events may occur during normal administration, but repeated or unusual denied actions can indicate privilege probing, reconnaissance, compromised credentials, or misconfigured permissions.



This test also demonstrates the importance of validating detection rules after they are created. A detection is stronger when it is tested with a known event and supported by screenshots showing the alerting workflow.

