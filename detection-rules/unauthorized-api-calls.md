# 🚫 Detection Rule: Unauthorized API Calls

## 🎯 Objective

Detect AWS API calls that fail because the user, role, or service does not have permission to perform the requested action.

## 📥 Data Source

- AWS CloudTrail

- Amazon CloudWatch Logs

## 📂 Log Group

`/aws/cloudtrail/security-monitoring`

## 🔎 Filter Pattern

```text

{ ($.errorCode = "*UnauthorizedOperation") || ($.errorCode = "AccessDenied*") }

```

## 📊 Metric Details

| Field | Value |

|---|---|

| Filter name | `UnauthorizedAPICalls` |

| Metric namespace | `CloudSecurityMonitoring` |

| Metric name | `UnauthorizedAPICallCount` |

| Metric value | `1` |

| Default value | `0` |

| Unit | `Count` |

## 🚨 Alarm Details

| Field | Value |

|---|---|

| Alarm name | `UnauthorizedAPICallsAlarm` |

| Statistic | `Sum` |

| Period | `5 minutes` |

| Threshold | `>= 1` |

| Notification topic | `aws-security-alerts` |

## 🧠 Detection Logic

This rule monitors CloudTrail events for unauthorized or access denied API activity. When a matching event is written to the CloudWatch log group, the metric filter increments the `UnauthorizedAPICallCount` metric.

The CloudWatch alarm triggers when the metric count is greater than or equal to `1` within a 5-minute period.

## 🛡️ Security Reasoning

Unauthorized API calls may indicate misconfigured permissions, application errors, privilege misuse, or attempted access to AWS resources without proper authorization.

Monitoring these events helps reduce detection time and provides visibility into denied actions across the AWS account.

## ⚠️ Possible Causes

- IAM user lacks required permissions

- IAM role is misconfigured

- User attempts to access unauthorized AWS services

- Application uses outdated or incorrect credentials

- Suspicious activity from compromised credentials

- Reconnaissance or privilege probing activity

## 🧪 Analyst Response

1. Review the CloudTrail event.

2. Identify the user, role, source IP address, event name, and affected service.

3. Determine whether the action was expected or authorized.

4. Validate whether the denied request came from a known user or service.

5. Review IAM permissions if the action was legitimate.

6. Investigate further if the activity appears suspicious, repeated, or unusual.

## 📸 Evidence

Screenshots captured:

- [Unauthorized API metric filter created](../screenshots/08-unauthorized-api-metric-filter.png)

- [Unauthorized API alarm created](../screenshots/09-unauthorized-api-alarm-created.png)

- [SNS email subscription confirmed](../screenshots/10-sns-email-confirmed.png)

- [Read-only test user created](../screenshots/11-readonly-test-user-created.png)

- [Access denied test event](../screenshots/12-access-denied-test-event.png)

- [Unauthorized API alarm triggered](../screenshots/13-unauthorized-api-alarm-triggered.png)

## 🔒 Security Considerations

Before publishing this project, screenshots should be reviewed and sensitive information should be removed or redacted, including:

- AWS account IDs

- ARNs

- Usernames

- Email addresses

- IP addresses

- SNS subscription details

- Browser URLs

- CloudWatch URLs

## 🧠 SOC Analyst Notes

This detection provides visibility into denied AWS API activity. While not every unauthorized API call is malicious, repeated or unusual denied actions can indicate reconnaissance, privilege probing, compromised credentials, or misconfigured access.

In this lab, the detection was validated by using a read-only IAM test user to attempt a restricted IAM action. The denied action generated an access denied event, which was captured by CloudTrail and monitored through CloudWatch.
