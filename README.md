###  SNS to Slack

# Lambda code written by: Mohamed Labouardy (https://read.acloud.guru/slack-notification-with-cloudwatch-alarms-lambda-6f2cc77b463a)
# Guide by Raphael Farias de Andrade (https://github.com/Raphz0rD/sns-to-slack)

Prereqs:

AWS CLI previously configured

Download Package: 

1- Create SNS Topic:

aws sns create-topic --name <topicName> --region <awsRegion>

2 - Configure Webhook on Slack Channel

<webhookURL>
Example: https://hooks.slack.com/services/ZZZZZZZZZ/YYYYYYYYYYYY/XXXXXXXXXXXXXXXXXXX

3 - Configure Lambda

aws lambda create-function --function-name <lambdaName> --zip-file fileb://deployment.zip --runtime go1.x --handler main --role <roleARN> --environment Variables={SLACK_WEBHOOK=<webhookURL>} --region <awsRegion>

4 - Subscribe SNS

aws sns subscribe --topic-arn <topicArn> --protocol lambda --notification-endpoint <lambdaArn --region <awsRegion>

5 - Create Alarm and subscribe to the created SNS

6 - Profit!


