# 👤 IAM Admin User Setup

## 🎯 Objective

The objective of this step was to create a dedicated IAM administrative user for daily lab activities instead of using the AWS root account.

## ✅ Actions Completed

- Created an IAM user group named `Administrators`

- Attached the `AdministratorAccess` policy to the group for lab administration

- Created a dedicated IAM admin user named `aws-lab-admin`

- Added the IAM admin user to the `Administrators` group

- Signed out of the root account

- Signed in using the IAM admin user

- Enabled multi-factor authentication (MFA) for the IAM admin user

## 🛡️ Security Reasoning

Using the root account for daily work is not recommended because the root user has unrestricted permissions and cannot be limited by IAM policies. A dedicated IAM admin user allows better identity management and supports safer daily operations.

Adding the user to a group improves permission management because access can be controlled at the group level instead of attaching policies directly to individual users.

For this lab, the `AdministratorAccess` policy was used to simplify setup and configuration. In a production environment, permissions should follow the principle of least privilege and only allow the specific actions required for each role.

## 📉 Risk Reduced

- Overuse of the AWS root account

- Unauthorized privileged access

- Weak identity separation

- Poor access management practices

- Lack of MFA protection for administrative access

## 📸 Evidence

Screenshots captured:

- [Admin group created](../screenshots/03-admin-group-created.png)

- [IAM admin user created](../screenshots/04-iam-admin-user-created.png)

- [IAM admin MFA enabled](../screenshots/05-iam-admin-mfa-enabled.png)

## 🔒 Security Considerations

Sensitive details such as account identifiers, ARNs, console sign-in URLs, and credential information should be removed or redacted before publishing.

## 🧠 SOC Analyst Notes

Identity and access management is one of the most important areas of cloud security. Before deploying logging and monitoring services, privileged access should be protected with MFA and separated from the root user.

This setup demonstrates a basic cloud security practice: minimizing root account usage, enforcing MFA, and managing administrative access through IAM groups.
