# 🔐 Account Security Setup

## 🎯 Objective

The objective of this step was to secure the AWS account before deploying any cloud security monitoring services. Since the AWS root user has full access to all account resources, it should only be used for account-level tasks and emergency access.

## ✅ Actions Completed

- Created a new AWS account for the cloud security monitoring lab

- Signed in using the AWS root user

- Enabled multi-factor authentication (MFA) on the root account

- Verified that the MFA device was successfully assigned

- Transitioned daily administrative work to a dedicated IAM admin user

## 🛡️ Security Reasoning

The AWS root user has unrestricted access to the entire AWS account. If the root credentials are compromised, an attacker could modify billing settings, delete resources, create new users, disable security controls, or take over the account.

Enabling MFA reduces the risk of unauthorized access by requiring a second authentication factor in addition to the root password. Limiting root account usage also supports better access management and reduces the chance of accidental or unnecessary use of highly privileged credentials.

## 📉 Risk Reduced

- Unauthorized root account access

- AWS account takeover

- Unauthorized billing or resource creation

- Security control tampering

- Overuse of root-level credentials

## 📸 Evidence

Screenshot captured:

- [Root MFA enabled](../screenshots/01-root-mfa-enabled.png)

## 🔒 Security Considerations

Sensitive details such as account identifiers, IP addresses, ARNs, and sign-in information should be removed or redacted before publishing.

## 🧠 SOC Analyst Notes

Securing the root account is a foundational cloud security step. Before deploying monitoring tools, privileged access should be protected with MFA and root account usage should be minimized. MFA on the root account is a critical preventive control that reduces the likelihood of unauthorized access.
