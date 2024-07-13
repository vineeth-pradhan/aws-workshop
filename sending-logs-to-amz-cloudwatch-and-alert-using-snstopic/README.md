# Standing Up an Apache Web Server EC2 Instance and Sending Logs to Amazon CloudWatch

## Introduction
During this hands-on lab project you are going to work on configuring an Amazon EC2 instance to push some custom log files to Amazon CloudWatch using the CloudWatch agent. Once the log files are correctly configured to be sent to Amazon CloudWatch, you will then implement a simple alerting system to catch some specific warnings and error messages using Metric Filters and Amazon SNS notifications.
Prerequisites

## Challenge Objectives
1. Install and Configure the Amazon CloudWatch Agent
1. Connect to the ApacheWebServer EC2 instance using Session Manager.

1. Once connected, use the commands listed [here](commands/README.md) to install the Amazon CloudWatch agent and create the agent configuration file.

1. Copy and paste the [JSON configuration code](configs/cloudwatch-agent-config.json) into the new file then start the agent with the new config file using the command listed on GitHub.

1. Create a Metric Filter for 404 Status Codes
1. Within the Amazon CloudWatch Apache-Access-Logs Log Group, create a new metric filter looking for 404 status codes within the log entries.

1. For the Filter pattern enter the following text to create a metric filter that matches for any 404 status codes.

    %\b404\b%

* Metric Filter Settings:
** Filter Name: `404`
** Metric namespace: `Apache`
** Metric name: `404`
** Metric value: `1`
** Default value: _blank_
** Unit: Count
** For testing, open the public IP of the ApacheWebServer instance in your browser, change the URL to http and append a fake page on the end (Example: http://YOUR_PUBLIC_IP/fake.html).

1. Create SNS Topic and CloudWatch Alarm
1. Now, we can put it all together and set up a new CloudWatch Alarm to send a message through Amazon SNS to notify us whenever a 404 is detected in our Log Group.

1. Create a new alarm via the CloudWatch Alarms dashboard for the newly created Apache namespace.

> Hint: There is a shortcut from within the graphed metric section.

1. Alarm Metric Settings:

** Metric namespace: `Apache`
** Metric name: `404`
** Statistic: `Sum`
** Alarm Conditions Settings:
** Threshold type: `Static`
** Whenever 404 is...: `Greater/Equal`
** than: `0`
** Alarm state trigger: `In alarm`
** Alarm name: `404-Detections`

1. Then, create a new SNS topic named `404-Alerts` and confirm subscription to it received on your email before moving further. Then, refresh the fake ApacheWebServer page to generate 404 errors and test the alarm.
