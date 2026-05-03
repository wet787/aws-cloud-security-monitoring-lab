# 🧾 CloudTrail Setup

## 🎯 Objective

The objective of this step was to enable AWS CloudTrail to record AWS account management activity and deliver those logs to CloudWatch Logs for monitoring and detection.

## ✅ Actions Completed

- Created a multi-region CloudTrail trail named `aws-security-monitoring-trail`

- Enabled SSE-KMS encryption using the KMS alias `alias/aws-security-monitoring-cloudtrail`

- Enabled log file validation

- Configured CloudTrail to send logs to CloudWatch Logs

- Configured the CloudWatch log group `/aws/cloudtrail/security-monitoring`

- Created the IAM role `CloudTrail_CloudWatchLogs_Role` for CloudWatch Logs delivery

- Configured CloudTrail to log all management events

- Left data events, Insights events, and network activity events disabled for the initial lab setup

- Verified that CloudTrail log streams were appearing in CloudWatch Logs

## 🛡️ Security Reasoning

CloudTrail provides visibility into AWS account activity by recording API calls and management events. These logs are important for investigating administrative actions, access changes, resource modifications, and denied API activity.

Sending CloudTrail logs to CloudWatch Logs allows the account activity to be monitored using metric filters and alarms. This supports detection engineering use cases such as unauthorized API calls, failed login attempts, security group changes, and IAM policy changes.

Enabling log file validation helps verify the integrity of delivered CloudTrail log files, while SSE-KMS encryption helps protect log data at rest.

## 📉 Risk Reduced

- Lack of visibility into AWS account activity

- Unmonitored administrative actions

- Delayed detection of suspicious API activity

- Limited investigation capability during cloud security incidents

- Risk of unauthorized changes going unnoticed

## 📸 Evidence

Screenshots captured:

- [CloudTrail created](../screenshots/06-cloudtrail-created.png)

- [CloudWatch log streams verified](../screenshots/07-cloudwatch-log-streams.png)

## 🔒 Security Considerations

Sensitive details such as account identifiers, ARNs, S3 bucket names, KMS key information, and CloudTrail log paths should be removed or redacted before publishing.

## 🧠 SOC Analyst Notes

CloudTrail is one of the most important logging sources for AWS security monitoring. By recording management events and delivering them to CloudWatch Logs, CloudTrail provides the foundation for detection, alerting, and investigation.

This setup supports SOC-style monitoring by allowing suspicious AWS activity to be detected through CloudWatch metric filters and alarms.
