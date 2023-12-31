# Week 0 — Billing and Architecture
## Setting an Organization for Enterpise
1. Create an Active OU and put all Bussiness Unit under that OU, All account should be in use
2. Create a Standby OU for empty AWS account, so we don't need to set up
3. Create a Recycling OU for Account pending clearing when someone leaves or transfers, then move the cleaned accounts to Standby OU
## Create a AWS Budget
```
aws budgets create-budget \
    --account-id 111122223333 \
    --budget file://budget.json \
    --notifications-with-subscribers file://notifications-with-subscribers.json
```
## Create a SNS subscription
```
aws sns create-topic --name $subscription-name
```
##use the arn we get back to create add a subscription
```
aws sns subscribe \
    --topic-arn TopicARN \
    --protocol email \
    --notification-endpoint $email_here
```
## Creating Alarm to Trigger SNS topic
```
aws cloudwatch put-metric-alarm --cli-input-json file://alarm-config.json
```
## Removeing Sensitive Data from git commit history
1. install `bfg`
2. create a file with all the strings you want to remove, i.e `password.txt`
3. using `bfg --replace-text 'file://password.txt'`
4. run `git reflog expire --expire=now --all && git gc --prune=now --aggressiv`
5. get new version of the repo `git clone --mirror <github-repo.git>
