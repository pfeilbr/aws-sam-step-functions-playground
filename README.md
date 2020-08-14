# aws-sam-step-functions-playground

learn and experiment with using [AWS SAM](https://aws.amazon.com/serverless/sam/) to define and deploy [AWS Step Functions](https://aws.amazon.com/step-functions/).

see [`template.yaml`](template.yaml) and [`data/event-bus-events.json`](data/event-bus-events.json)

## Running

```sh
# deploy
sam deploy --guided

# trigger step fn via EventBridge rule
aws events put-events --cli-input-json file://data/event-bus-events.json

# e.g. output
# {
#     "FailedEntryCount": 0,
#     "Entries": [
#         {
#             "EventId": "369fc438-8a99-bc45-7d79-46788420dbf8"
#         }
#     ]
# }

# trigger via API Gateway.  starts step fn then returns (does not wait for step fn to complete)
curl https://4cakde2i15.execute-api.us-east-1.amazonaws.com/Prod/start

# e.g. output
# {
#     "executionArn": "arn:aws:states:us-east-1:529276214230:execution:SimpleStateMachine-zIFFWgUF6O6D:53313d15-1005-44d0-84a0-ea57b66d1ac3",
#     "startDate": 1.597426336318E9
# }


# teardown
aws cloudformation delete-stack --stack-name "aws-sam-step-functions-playground" --region "us-east-1"
```

## Resources

* [Simplifying application orchestration with AWS Step Functions and AWS SAM](https://aws.amazon.com/blogs/compute/simplifying-application-orchestration-with-aws-step-functions-and-aws-sam/)
* [aws | events | put-events]](https://docs.aws.amazon.com/cli/latest/reference/events/put-events.html#examples)