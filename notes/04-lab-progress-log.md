# 📋 AWS Cloud Security Monitoring Lab Progress Log

## ☁️ Project

AWS Cloud Security Monitoring Lab

## 📌 Current Status

AWS account security setup, CloudTrail log delivery, and two detection rules have been completed. The Unauthorized API Calls detection and Failed AWS Console Login detection were created, tested, validated, and documented. Temporary IAM resources used for testing were removed after validation.

## ✅ Completed Steps

### Step 1: AWS Account Created

Created a new AWS account dedicated to the cloud security monitoring lab.

### Step 2: Root MFA Enabled

Enabled multi-factor authentication (MFA) for the AWS root account to reduce the risk of unauthorized account access.

Evidence:

- [Root MFA enabled](../screenshots/01-root-mfa-enabled.png)

### Step 3: Budget Alert Created

Created a zero-spend budget alert to monitor AWS usage and reduce the risk of unexpected charges.

Evidence:

- [Budget alert created](../screenshots/02-budget-alert-created.png)

### Step 4: IAM Admin Group Created

Created an IAM user group named `Administrators` and attached the `AdministratorAccess` policy for lab administration.

Evidence:

- [Admin group created](../screenshots/03-admin-group-created.png)

### Step 5: IAM Admin User Created

Created a dedicated IAM admin user named `aws-lab-admin` for daily lab activities instead of using the root account.

Evidence:

- [IAM admin user created](../screenshots/04-iam-admin-user-created.png)

### Step 6: IAM Admin MFA Enabled

Enabled multi-factor authentication for the IAM admin user.

Evidence:

- [IAM admin MFA enabled](../screenshots/05-iam-admin-mfa-enabled.png)

### Step 7: CloudTrail Trail Created

Created a multi-region CloudTrail trail named `aws-security-monitoring-trail` to record AWS account management activity.

Evidence:

- [CloudTrail created](../screenshots/06-cloudtrail-created.png)

### Step 8: CloudWatch Logs Integration Enabled

Configured CloudTrail to deliver logs to the CloudWatch log group `/aws/cloudtrail/security-monitoring`.

Evidence:

- [CloudTrail created and CloudWatch integration enabled](../screenshots/06-cloudtrail-created.png)

### Step 9: CloudTrail Logs Verified in CloudWatch

Verified that CloudTrail events are being delivered to the CloudWatch log group `/aws/cloudtrail/security-monitoring`.

The CloudWatch log group showed multiple log streams with recent event timestamps, confirming that AWS account activity is being captured and sent to CloudWatch Logs successfully.

Evidence:

- [CloudWatch log streams verified](../screenshots/07-cloudwatch-log-streams.png)

### Step 10: Unauthorized API Calls Metric Filter Created

Created a CloudWatch metric filter named `UnauthorizedAPICalls` to detect CloudTrail events with access denied or unauthorized operation error codes.

Evidence:

- [Unauthorized API metric filter created](../screenshots/08-unauthorized-api-metric-filter.png)

### Step 11: Unauthorized API Calls Alarm Created

Created a CloudWatch alarm named `UnauthorizedAPICallsAlarm` that triggers when one or more unauthorized API calls are detected within a 5-minute period.

Configured SNS topic `aws-security-alerts` to send email notifications when the alarm enters the alarm state.

Evidence:

- [Unauthorized API alarm created](../screenshots/09-unauthorized-api-alarm-created.png)

- [SNS email subscription confirmed](../screenshots/10-sns-email-confirmed.png)

### Step 12: Unauthorized API Calls Detection Tested

Created a temporary read-only IAM user named `readonly-test-user` and attempted to create another IAM user named `blocked-test-user`.

The action was denied because the read-only user did not have permission to perform `iam:CreateUser`.

Evidence:

- [Read-only test user created](../screenshots/11-readonly-test-user-created.png)

- [Access denied test event](../screenshots/12-access-denied-test-event.png)

### Step 13: Unauthorized API Calls Alarm Validated

Reviewed the CloudWatch alarm graph and confirmed that the unauthorized API call metric showed activity after the denied action was generated.

Evidence:

- [Unauthorized API alarm activity validated](../screenshots/13-unauthorized-api-alarm-triggered.png)

### Step 14: Test IAM User Deleted

Deleted the temporary IAM user `readonly-test-user` after the detection test was completed.

Evidence:

- [Read-only test user deleted](../screenshots/14-readonly-test-user-deleted.png)

### Step 15: Test IAM Group Deleted

Deleted the temporary IAM group `ReadOnlyTestGroup` after the detection test was completed.

Evidence:

- [Read-only test group deleted](../screenshots/15-readonly-test-group-deleted.png)

### Step 16: Failed Console Login Metric Filter Created

Created a CloudWatch metric filter named `FailedConsoleLogins` to detect failed AWS Management Console login attempts using CloudTrail `ConsoleLogin` events.

Evidence:

- [Failed console login metric filter created](../screenshots/16-failed-console-login-metric-filter.png)

### Step 17: Failed Console Login Alarm Created

Created a CloudWatch alarm named `FailedConsoleLoginAlarm` that triggers when one or more failed AWS Console login attempts are detected within a 5-minute period.

Connected the alarm to the existing SNS topic `aws-security-alerts`.

Evidence:

- [Failed console login alarm created](../screenshots/17-failed-console-login-alarm-created.png)

### Step 18: Failed Console Login Test Event Generated

Generated a controlled failed AWS Console login event by attempting to sign in with the correct IAM username and an intentionally incorrect password.

Evidence:

- [Failed console login test event](../screenshots/18-failed-console-login-test-event.png)

### Step 19: Failed Console Login Alarm Validated

Reviewed the CloudWatch alarm graph and confirmed that the `FailedConsoleLoginCount` metric showed activity after the failed login attempt was generated.

The alarm later returned to an OK state after the evaluation period ended, which is expected when no additional failed login attempts occur.

Evidence:

- [Failed console login alarm activity validated](../screenshots/19-failed-console-login-alarm-triggered.png)

## 🚦 Current Lab Phase

```text

Phase 1: AWS Account Security Setup — Complete

Phase 2: CloudTrail and CloudWatch Log Delivery — Complete

Phase 3: Unauthorized API Calls Detection — Complete

Phase 4: Test Resource Cleanup — Complete

Phase 5: Failed AWS Console Login Detection — Complete

```

## 🧠 Detection Rules Completed

| Detection Rule | Status | Documentation |

|---|---|---|

| Unauthorized API Calls | Complete | [View Rule](../detection-rules/unauthorized-api-calls.md) |

| Failed AWS Console Login Attempts | Complete | [View Rule](../detection-rules/failed-console-logins.md) |

## 📸 Current Screenshot Set

| # | Evidence | Screenshot |

|---:|---|---|

| 01 | Root MFA enabled | [View](../screenshots/01-root-mfa-enabled.png) |

| 02 | Budget alert created | [View](../screenshots/02-budget-alert-created.png) |

| 03 | Admin group created | [View](../screenshots/03-admin-group-created.png) |

| 04 | IAM admin user created | [View](../screenshots/04-iam-admin-user-created.png) |

| 05 | IAM admin MFA enabled | [View](../screenshots/05-iam-admin-mfa-enabled.png) |

| 06 | CloudTrail created | [View](../screenshots/06-cloudtrail-created.png) |

| 07 | CloudWatch log streams verified | [View](../screenshots/07-cloudwatch-log-streams.png) |

| 08 | Unauthorized API metric filter created | [View](../screenshots/08-unauthorized-api-metric-filter.png) |

| 09 | Unauthorized API alarm created | [View](../screenshots/09-unauthorized-api-alarm-created.png) |

| 10 | SNS email subscription confirmed | [View](../screenshots/10-sns-email-confirmed.png) |

| 11 | Read-only test user created | [View](../screenshots/11-readonly-test-user-created.png) |

| 12 | Access denied event generated | [View](../screenshots/12-access-denied-test-event.png) |

| 13 | Unauthorized API alarm activity validated | [View](../screenshots/13-unauthorized-api-alarm-triggered.png) |

| 14 | Read-only test user deleted | [View](../screenshots/14-readonly-test-user-deleted.png) |

| 15 | Read-only test group deleted | [View](../screenshots/15-readonly-test-group-deleted.png) |

| 16 | Failed console login metric filter created | [View](../screenshots/16-failed-console-login-metric-filter.png) |

| 17 | Failed console login alarm created | [View](../screenshots/17-failed-console-login-alarm-created.png) |

| 18 | Failed console login test event generated | [View](../screenshots/18-failed-console-login-test-event.png) |

| 19 | Failed console login alarm activity validated | [View](../screenshots/19-failed-console-login-alarm-triggered.png) |

## 🔜 Next Planned Step

Create the next detection rule for IAM policy changes or security group configuration changes.

## 📝 Notes

The lab is currently at a clean stopping point. Account security controls are in place, CloudTrail has been created, CloudWatch Logs integration is enabled, CloudTrail log delivery has been verified, and two detection rules have been created and tested.

Temporary IAM resources used for testing were removed after validation.

During the Failed Console Login detection test, the existing `UnauthorizedAPICallsAlarm` also entered the alarm state. This showed that authentication failure activity may generate related unauthorized or denied activity in CloudTrail and should be reviewed during investigation.

Before publishing this project, screenshots should be reviewed and sensitive information such as account IDs, ARNs, IP addresses, sign-in URLs, subscription identifiers, browser URLs, and credential-related details should be removed or redacted.
