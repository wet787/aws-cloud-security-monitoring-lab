# ☁️ AWS Cloud Security Monitoring Lab

![AWS](https://img.shields.io/badge/AWS-Cloud%20Security-orange) ![CloudTrail](https://img.shields.io/badge/CloudTrail-Logging-blue) ![CloudWatch](https://img.shields.io/badge/CloudWatch-Monitoring-purple) ![SNS](https://img.shields.io/badge/SNS-Alerting-green) ![Status](https://img.shields.io/badge/Status-In%20Progress-yellow)

---

## 📌 Project Overview

This project demonstrates how AWS security monitoring can be implemented using **CloudTrail**, **CloudWatch Logs**, **CloudWatch Metric Filters**, **CloudWatch Alarms**, **Amazon SNS**, and **IAM**.

The goal of this lab is to collect AWS account activity, create cloud security detection rules, generate controlled test events, validate alerting workflows, and document the results from a **SOC analyst perspective**.

---

## 🎯 Lab Objectives

- 🔐 Secure the AWS account before deploying monitoring services

- 🛡️ Enable MFA on the AWS root account

- 💰 Create a budget alert for cost monitoring

- 👤 Create a dedicated IAM admin user for daily lab work

- 🧾 Configure CloudTrail to record AWS management activity

- 📥 Send CloudTrail logs to CloudWatch Logs

- 🔎 Create CloudWatch metric filters for suspicious AWS activity

- 🚨 Create CloudWatch alarms for detected security events

- 📧 Configure SNS email notifications

- 🧪 Generate controlled test events

- ✅ Validate detection workflows

- 🧹 Remove temporary test resources after validation

- 📝 Document findings, evidence, and analyst notes

---

## 🧰 Tools and AWS Services Used

| Service | Purpose |

|---|---|

| 🔐 **AWS IAM** | User, group, and access management |

| 🧾 **AWS CloudTrail** | API activity and console login logging |

| 📊 **Amazon CloudWatch Logs** | Centralized log storage and review |

| 🔎 **CloudWatch Metric Filters** | Detection logic for suspicious activity |

| 🚨 **CloudWatch Alarms** | Alerting based on metric thresholds |

| 📧 **Amazon SNS** | Email notification delivery |

| 💰 **AWS Budgets** | Cost monitoring and governance |

| 🔑 **AWS KMS** | Encryption for CloudTrail logs |

| 🪣 **Amazon S3** | CloudTrail log storage |

---

## 🏗️ Lab Architecture

```text

AWS Account

   ↓

CloudTrail records AWS API and console activity

   ↓

CloudTrail sends logs to CloudWatch Logs

   ↓

CloudWatch metric filters detect suspicious events

   ↓

CloudWatch alarms evaluate detection metrics

   ↓

SNS sends email notifications

   ↓

Analyst reviews evidence and documents findings

```

---

## 🔍 Detection Use Cases

### 🚫 Detection 1: Unauthorized API Calls

This detection identifies AWS API calls that fail because the user, role, or service does not have permission to perform the requested action.

**Filter Pattern**

```text

{ ($.errorCode = "*UnauthorizedOperation") || ($.errorCode = "AccessDenied*") }

```

This detection can help identify:

- ⚠️ Misconfigured IAM permissions

- 🚫 Unauthorized access attempts

- 🧪 Privilege probing

- 🕵️ Reconnaissance activity

- 🔑 Compromised credentials attempting restricted actions

---

### 🔐 Detection 2: Failed AWS Console Login Attempts

This detection identifies failed AWS Management Console login attempts using CloudTrail `ConsoleLogin` events.

**Filter Pattern**

```text

{ ($.eventName = "ConsoleLogin") && ($.responseElements.ConsoleLogin = "Failure") }

```

This detection can help identify:

- ❌ Incorrect password attempts

- 🚫 Unauthorized console access attempts

- 🧪 Credential guessing

- 🔁 Brute-force login behavior

- 🔑 Possible compromised credential testing

---

## 📂 Project Structure

```text
aws-cloud-security-monitoring-lab/
├── README.md
├── notes/
│   ├── 01-account-security.md
│   ├── 02-budget-alert.md
│   ├── 03-iam-admin-user.md
│   ├── 04-lab-progress.md
│   ├── 05-cloudtrail-setup.md
│   ├── 06-unauthorized-api-detection-test.md
│   ├── 07-cleanup-test-resources.md
│   └── 08-failed-console-login-detection-test.md
├── detection-rules/
│   ├── unauthorized-api-calls.md
│   └── failed-console-logins.md
└── screenshots/
    ├── 01-root-mfa-enabled.png
    ├── 02-budget-alert-created.png
    ├── 03-admin-group-created.png
    ├── 04-iam-admin-user-created.png
    ├── 05-iam-admin-mfa-enabled.png
    ├── 06-cloudtrail-created.png
    ├── 07-cloudwatch-log-streams.png
    ├── 08-unauthorized-api-metric-filter.png
    ├── 09-unauthorized-api-alarm-created.png
    ├── 10-sns-email-confirmed.png
    ├── 11-readonly-test-user-created.png
    ├── 12-access-denied-test-event.png
    ├── 13-unauthorized-api-alarm-triggered.png
    ├── 14-readonly-test-user-deleted.png
    ├── 15-readonly-test-group-deleted.png
    ├── 16-failed-console-login-metric-filter.png
    ├── 17-failed-console-login-alarm-created.png
    ├── 18-failed-console-login-test-event.png
    └── 19-failed-console-login-alarm-triggered.png
```

## ✅ Completed Work

- ✅ Created and secured a new AWS account

- ✅ Enabled MFA on the root account

- ✅ Created a budget alert

- ✅ Created an IAM admin group

- ✅ Created an IAM admin user

- ✅ Enabled MFA for the IAM admin user

- ✅ Created a multi-region CloudTrail trail

- ✅ Enabled CloudTrail log file validation

- ✅ Enabled SSE-KMS encryption for CloudTrail logs

- ✅ Sent CloudTrail logs to CloudWatch Logs

- ✅ Verified CloudTrail log streams in CloudWatch

- ✅ Created an unauthorized API calls metric filter

- ✅ Created a CloudWatch alarm for unauthorized API activity

- ✅ Confirmed SNS email subscription

- ✅ Created a read-only test user

- ✅ Generated a controlled access denied event

- ✅ Validated unauthorized API metric activity

- ✅ Deleted temporary test IAM resources

- ✅ Created a failed console login metric filter

- ✅ Created a CloudWatch alarm for failed console login attempts

- ✅ Generated a controlled failed AWS Console login event

- ✅ Validated failed console login metric activity

---

## 📸 Evidence Screenshots

| # | Evidence | Screenshot |

|---:|---|---|

| 01 | 🔐 Root MFA enabled | [View](screenshots/01-root-mfa-enabled.png) |

| 02 | 💰 Budget alert created | [View](screenshots/02-budget-alert-created.png) |

| 03 | 👥 Admin group created | [View](screenshots/03-admin-group-created.png) |

| 04 | 👤 IAM admin user created | [View](screenshots/04-iam-admin-user-created.png) |

| 05 | 🛡️ IAM admin MFA enabled | [View](screenshots/05-iam-admin-mfa-enabled.png) |

| 06 | 🧾 CloudTrail created | [View](screenshots/06-cloudtrail-created.png) |

| 07 | 📥 CloudWatch log streams verified | [View](screenshots/07-cloudwatch-log-streams.png) |

| 08 | 🔎 Unauthorized API metric filter created | [View](screenshots/08-unauthorized-api-metric-filter.png) |

| 09 | 🚨 Unauthorized API alarm created | [View](screenshots/09-unauthorized-api-alarm-created.png) |

| 10 | 📧 SNS email subscription confirmed | [View](screenshots/10-sns-email-confirmed.png) |

| 11 | 👤 Read-only test user created | [View](screenshots/11-readonly-test-user-created.png) |

| 12 | 🚫 Access denied event generated | [View](screenshots/12-access-denied-test-event.png) |

| 13 | 📈 Unauthorized API alarm activity validated | [View](screenshots/13-unauthorized-api-alarm-triggered.png) |

| 14 | 🧹 Read-only test user deleted | [View](screenshots/14-readonly-test-user-deleted.png) |

| 15 | 🧹 Read-only test group deleted | [View](screenshots/15-readonly-test-group-deleted.png) |

| 16 | 🔎 Failed console login metric filter created | [View](screenshots/16-failed-console-login-metric-filter.png) |

| 17 | 🚨 Failed console login alarm created | [View](screenshots/17-failed-console-login-alarm-created.png) |

| 18 | ❌ Failed console login test event generated | [View](screenshots/18-failed-console-login-test-event.png) |

| 19 | 📈 Failed console login alarm activity validated | [View](screenshots/19-failed-console-login-alarm-triggered.png) |

---

## 📝 Documentation

| Document | Description |

|---|---|

| [Account Security Setup](notes/01-account-security.md) | Root account MFA and initial account hardening |

| [Budget Alert Setup](notes/02-budget-alert.md) | Cost monitoring and financial risk reduction |

| [IAM Admin User Setup](notes/03-iam-admin-user.md) | IAM admin group, admin user, and MFA setup |

| [Lab Progress Log](notes/04-lab-progress.md) | Step-by-step project progress |

| [CloudTrail Setup](notes/05-cloudtrail-setup.md) | CloudTrail, KMS, CloudWatch Logs, and log validation |

| [Unauthorized API Calls Detection Test](notes/06-unauthorized-api-detection-test.md) | Controlled access denied test and validation |

| [Cleanup: Test IAM Resources](notes/07-cleanup-test-resources.md) | Cleanup of temporary IAM test resources |

| [Failed Console Login Detection Test](notes/08-failed-console-login-detection-test.md) | Controlled failed login test and validation |

---

## 🧠 Detection Rules

| Detection Rule | Description |

|---|---|

| [Unauthorized API Calls](detection-rules/unauthorized-api-calls.md) | Detects denied AWS API activity using CloudTrail and CloudWatch |

| [Failed AWS Console Login Attempts](detection-rules/failed-console-logins.md) | Detects failed AWS Management Console login attempts |

---

## 🧪 Detection Validation Summary

### 🚫 Unauthorized API Calls

A temporary read-only IAM user was created to safely generate a controlled denied action. The user attempted to create another IAM user, which resulted in an access denied event.

```text

readonly-test-user attempted iam:CreateUser

       ↓

AWS denied the action

       ↓

CloudTrail recorded the event

       ↓

CloudWatch metric filter detected the event

       ↓

CloudWatch alarm showed unauthorized API activity

       ↓

SNS notification channel was confirmed

```

---

### 🔐 Failed AWS Console Login Attempts

A controlled failed login attempt was generated by attempting to sign in to the AWS Management Console using the correct IAM username and an intentionally incorrect password.

```text

Incorrect AWS Console password entered

       ↓

AWS rejected the login attempt

       ↓

CloudTrail recorded a ConsoleLogin failure event

       ↓

CloudWatch metric filter detected the event

       ↓

CloudWatch alarm showed failed login metric activity

       ↓

SNS notification channel was available for alerting

```

During testing, the existing `UnauthorizedAPICallsAlarm` also triggered. This provided additional context that authentication failures may generate related unauthorized or denied activity in CloudTrail.

---

## 🛡️ Skills Demonstrated

- ☁️ AWS cloud security fundamentals

- 🔐 Identity and access management

- 🧾 CloudTrail logging

- 📊 CloudWatch log monitoring

- 🔎 Detection engineering

- 🚨 CloudWatch alarm configuration

- 📧 SNS alerting

- 🧪 Detection validation

- 🧹 Cloud security hygiene

- 📝 SOC-style documentation

- 📁 GitHub project organization

- 🧠 Security investigation thinking

---

## 🔒 Security Considerations

Before publishing this project, all screenshots should be reviewed and sensitive information should be removed or redacted, including:

- AWS account IDs

- ARNs

- IP addresses

- Email addresses

- Browser URLs

- Console sign-in URLs

- SNS subscription details

- S3 bucket paths

- CloudTrail log paths

- CloudWatch URLs

- Credential-related information

---

## 🚧 Project Status

**In progress**

### ✅ Completed

- Phase 1: AWS Account Security Setup

- Phase 2: CloudTrail and CloudWatch Log Delivery

- Phase 3: Unauthorized API Calls Detection

- Phase 4: Test Resource Cleanup

- Phase 5: Failed AWS Console Login Detection

### 🔜 Next Planned Step

Create the next detection rule for **IAM policy changes** or **security group configuration changes**.

---

## 👤 Author

**Wetser Santos Feliciano**
