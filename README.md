# 🚀 DevOps Assignment 5 – Log Streaming, CloudWatch Alarm & SNS Email Alert

This project automates the provisioning of an AWS EC2 instance using Terraform and deploys a Spring Boot application. It then streams logs to CloudWatch, sets up metric filters and alarms on error patterns, and sends alerts to email via SNS.

---

## 🔁 Output Flow & Screenshot Sequence

---

### 1️⃣ Terraform Apply Success

After executing:
```bash
terraform apply
📸 Screenshot #1: 1_terraform_apply_success.png

✅ Terraform provisioning was successful.

2️⃣ EC2 Instance Running
Navigate to:
AWS Console → EC2 → Instances → Instance State = Running

📸 Screenshot #2: 2_ec2_running.png

✅ EC2 instance is launched and running.

3️⃣ Application Running
SSH into your instance or open browser:

bash
Copy
Edit
curl http://<EC2_PUBLIC_IP>:8080
📸 Screenshot #3: 3_app_up_check.png

✅ Spring Boot application is accessible via port 8080.

4️⃣ CloudWatch Log Group Created
Navigate to:
AWS Console → CloudWatch → Log Groups

Log Group:

bash
Copy
Edit
/ec2/app-logs-dev
📸 Screenshot #4: 4_log_group_view.png

✅ Log group created for app logs.

5️⃣ Log Stream Entries Visible
Click on log group → click stream name
Check if logs like app output or simulated errors are appearing.

📸 Screenshot #5: 5_log_stream_entries.png

✅ Application logs are visible in CloudWatch.

6️⃣ Metric Filter on "ERROR"/"Exception"
Navigate to:
CloudWatch → Log Groups → /ec2/app-logs-dev → Metric Filters

Filter Pattern:

arduino
Copy
Edit
"ERROR" "Exception"
📸 Screenshot #6: 6_metric_filter_created.png

✅ Metric filter created using keywords and attached to namespace AppLogs.

7️⃣ CloudWatch Alarm Setup
Navigate to:
CloudWatch → Alarms → app-error-alarm-dev

Check:

Threshold = 1

Period = 60s

EvaluationPeriods = 1

State transitions when errors are logged

📸 Screenshot #7: 7_cloudwatch_alarm_config.png
📸 Screenshot #8: 8_alarm_graph.png

✅ Alarm is in place and linked to metric.

8️⃣ SNS Email Subscription Confirmed
Open inbox and confirm subscription by clicking the AWS link.

📸 Screenshot #9: 9_email_subscription_confirmed.png

✅ Email subscription for alerts is confirmed.

9️⃣ Simulate Errors to Trigger Alarm
SSH into EC2 and simulate errors:

bash
Copy
Edit
for i in {1..3}; do
  echo "ERROR: Simulated issue $i on $(date)" >> /home/ubuntu/app.log
  sleep 2
done
📸 Screenshot #10: 10_simulated_error_log.png

✅ Simulated "ERROR" logs written to app.log

🔟 Alarm Triggers & Email Alert Received
Wait for a minute and check alarm state on AWS.
Check email inbox for SNS notification email.

📸 Screenshot #11: 11_alarm_triggered.png
📸 Screenshot #12: 12_alarm_email_received.png

✅ CloudWatch Alarm triggered and email alert received.
