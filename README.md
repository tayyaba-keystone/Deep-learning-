🚀 DevOps Assignment – Enhanced Deployment Workflow
This project provisions an AWS EC2 instance, deploys a Spring Boot application, streams logs to CloudWatch, sets alarms on error patterns, and sends alert emails using SNS.

🔁 Output Flow & Screenshot Sequence
1️⃣ Terraform Apply Success
✅ After running terraform apply, all AWS resources (EC2, IAM, S3, SNS, CloudWatch) are created successfully.

📸 Screenshot: 1_terraform_apply_success.png

2️⃣ EC2 Running & App Up
✅ EC2 Instance Running
📍 Navigation:
AWS Console → EC2 → Instances → State: Running

📸 Screenshot: 2_ec2_running.png

Confirms EC2 instance is created and running.

✅ App Running on Port 8080
📍 Command (local or via EC2 SSH):

bash
Copy
Edit
curl http://<EC2_PUBLIC_IP>:8080
📸 Screenshot: 3_app_up_check.png

Confirms Spring Boot app is accessible.

3️⃣ CloudWatch Logs Streaming
📍 Navigation:
AWS Console → CloudWatch → Log groups → /ec2/app-logs-dev

📸 Screenshot:

4_log_group_view.png (Log group view)

5_log_stream_entries.png (Log stream content with logs)

Confirms EC2 app logs are being streamed to CloudWatch Logs.

4️⃣ Metric Filter Created
📍 Navigation:
CloudWatch → Logs → Log groups → Select /ec2/app-logs-dev → Metric Filters

📸 Screenshot: 6_metric_filter_created.png

Filter Pattern: "ERROR" "Exception"

Metric Name: ErrorCount-dev

Namespace: AppLogs

Confirms metric is generated from logs.

5️⃣ CloudWatch Alarm Setup
📍 Navigation:
CloudWatch → Alarms → app-error-alarm-dev

📸 Screenshots:

7_cloudwatch_alarm_state.png (Alarm state and configuration)

8_alarm_graph.png (Graph showing metric)

Confirms alarm is linked with the metric and is in evaluation mode.

6️⃣ SNS Email Subscription Confirmed
📍 Inbox:
Check for a confirmation email from AWS SNS and click the confirmation link.

📸 Screenshot: 9_email_subscription_confirmed.png

Confirms SNS email subscription is verified.

7️⃣ Simulate Error to Trigger Alarm
📍 SSH into EC2 and run:

bash
Copy
Edit
for i in {1..3}; do echo "ERROR: Simulated issue $i on $(date)" >> /home/ubuntu/app.log; sleep 2; done
📸 Screenshot: 10_simulated_error_log.png

Adds ERROR logs to trigger alarm.

8️⃣ Email Alert Received
📍 Inbox:
Look for alarm email from AWS SNS (subject includes "ALARM: app-error-alarm-dev").

📸 Screenshot: 11_alarm_email_received.png

Confirms alarm-to-email pipeline is working.

