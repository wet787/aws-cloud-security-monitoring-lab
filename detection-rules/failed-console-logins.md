# 🔐 Detection Rule: Failed AWS Console Login Attempts

## 🎯 Objective

Detect failed AWS Management Console login attempts using CloudTrail events delivered to CloudWatch Logs.

## 📥 Data Source

- AWS CloudTrail

- Amazon CloudWatch Logs

## 📂 Log Group

`/aws/cloudtrail/security-monitoring`

## 🔎 Filter Pattern

```text

{ ($.eventName = "ConsoleLogin") && ($.responseElements.ConsoleLogin = "Failure") }

```

## 📊 Metric Details

| Field | Value |

|---|---|

| Filter name | `FailedConsoleLogins` |

| Metric namespace | `CloudSecurityMonitoring` |

| Metric name | `FailedConsoleLoginCount` |

| Metric value | `1` |

| Default value | `0` |

| Unit | `Count` |

## 🚨 Alarm Details

| Field | Value |

|---|---|

| Alarm name | `FailedConsoleLoginAlarm` |

| Statistic | `Sum` |

| Period | `5 minutes` |

| Threshold | `>= 1` |

| Notification topic | `aws-security-alerts` |

## 🧠 Detection Logic

This rule monitors CloudTrail events for failed AWS Management Console login attempts. When a `ConsoleLogin` event has a result of `Failure`, the CloudWatch metric filter increments the `FailedConsoleLoginCount` metric.

The CloudWatch alarm evaluates this metric and triggers when one or more failed console login attempts are detected within a 5-minute period.

## 🛡️ Security Reasoning

Failed console login attempts may indicate a user typing the wrong password, but they can also indicate suspicious authentication behavior such as credential guessing, brute-force attempts, or unauthorized access attempts.

Monitoring failed console logins helps security teams identify possible account compromise attempts and review authentication activity in the AWS account.

## ⚠️ Possible Causes

- User entered an incorrect password

- User attempted to sign in with the wrong account information

- Unauthorized user attempted to access the AWS console

- Credential guessing or brute-force activity

- Compromised credentials being tested

- Misconfigured authentication workflow

## 🧪 Analyst Response

1. Review the CloudTrail `ConsoleLogin` event.

2. Identify the username, source IP address, user agent, event time, and login result.

3. Determine whether the failed login attempt came from the expected user.

4. Check whether the source IP address is known or suspicious.

5. Review the number of failed attempts and whether they are repeated.

6. Confirm whether MFA is enabled for the affected user.

7. Investigate further if the activity appears unusual, repeated, or unauthorized.

## 📸 Evidence

Screenshots captured:

- [Failed console login metric filter created](../screenshots/16-failed-console-login-metric-filter.png)

- [Failed console login alarm created](../screenshots/17-failed-console-login-alarm-created.png)

- [Failed console login test event](../screenshots/18-failed-console-login-test-event.png)

- [Failed console login alarm activity validated](../screenshots/19-failed-console-login-alarm-triggered.png)

## 🔒 Security Considerations

Before publishing this project, screenshots should be reviewed and sensitive information should be removed or redacted, including:

- AWS account IDs

- ARNs

- Usernames

- Email addresses

- IP addresses

- Browser URLs

- Console sign-in URLs

- CloudWatch URLs

## 🧠 SOC Analyst Notes

This detection provides visibility into failed AWS Management Console login attempts. While a single failed login may be normal user error, repeated failures or failures from unfamiliar locations may indicate credential guessing, brute-force attempts, or unauthorized access attempts.

During testing, the failed console login generated metric activity for the `FailedConsoleLoginAlarm`. The alarm later returned to OK after the evaluation period ended, which is expected behavior after the failed login activity stops.

The existing Unauthorized API Calls alarm also triggered during testing. This showed that authentication failures may generate additional unauthorized or denied activity in CloudTrail, which should be reviewed during investigation.
