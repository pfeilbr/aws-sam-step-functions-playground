# aws-sam-step-functions-playground

learn and experiment with using [AWS SAM](https://aws.amazon.com/serverless/sam/) to define and deploy [AWS Step Functions](https://aws.amazon.com/step-functions/).

see [`template.yaml`](template.yaml) and [`data/event-bus-events.json`](data/event-bus-events.json)

## Running

```sh
# deploy
sam deploy --guided

# trigger step fn via EventBridge rule
aws events put-events --cli-input-json file://data/event-bus-events.json

# teardown
aws cloudformation delete-stack --stack-name "aws-sam-step-functions-playground" --region "us-east-1"
```

## Resources

* [Simplifying application orchestration with AWS Step Functions and AWS SAM](https://aws.amazon.com/blogs/compute/simplifying-application-orchestration-with-aws-step-functions-and-aws-sam/)
* [aws | events | put-events]](https://docs.aws.amazon.com/cli/latest/reference/events/put-events.html#examples)