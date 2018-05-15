# aws-root-login-alert

Alerts when the AWS root user logs into AWS by sending an email to a
designated email address.  This infrastructure is intended to be
long-lived and requires no up-keep.  It should run for free or close
to free, depending on your account usage.

## Requirements

* `make`
* AWS CLI tool
* Permission to create AWS resources

## Getting Started

Run `make` to see a list of targets.

## Launching the Stack

The Makefile requires specific input variables to be passed in through
the command line.  If in doubt, run the Makefile with a specific target
and it will guide you through which variables are required.

```
make create-stack AWS_PROFILE=example AWS_REGION=us-east-1 RECIPIENT_EMAIL=alerts@example.com
{
  "StackId": "..."
}
```

The stack creation will happen asynchronously, but you can check on its
status with `make status`.  The stack creation will pause while the
SNS subscription is waiting for manual confirmation.  You will need
access to the recipient email address you used in the create-stack
command in order to confirm the SNS topic subscription and allow
CloudFormation to proceed with the rest of the stack creation.

## License

MIT License.  Please see [LICENSE](LICENSE) for more information.

