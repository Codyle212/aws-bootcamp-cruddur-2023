# Week 0 — Billing and Architecture
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
