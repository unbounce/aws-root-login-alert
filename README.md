# aws-root-login-alert

![Knowledge-Intermediate](https://img.shields.io/badge/Knowledge-Intermediate-yellow.svg)
![Cloud-AWS](https://img.shields.io/badge/Cloud-AWS-orange.svg)
![Category-Security](https://img.shields.io/badge/Category-Security-blue.svg)

Alerts when the AWS root user logs into AWS by sending an email to a
designated email address.

## Status — Migrated to OpenTofu/Terragrunt (PS-4592)

This service was migrated from CloudFormation to OpenTofu/Terragrunt.
The live CFN stack (`root-login-alerts-production`) is retained with
`DeletionPolicy: Retain` on all resources and is **not** the source of truth
for ongoing changes. Do not run `make create-stack` against this template.

Active management lives in `ub-tf-infrastructure`:

```
ub-tf-infrastructure/infrastructure/platform-services/unbounce-production/production/us-east-1/aws-root-login-alert/
  sns/                          (modules/sns)
  legacy-aws-root-login-alert/  (legacy-modules/legacy-aws-root-login-alert)
```

The CFN template (`template.cft`), stack policy (`policy.json`), and Makefile
deploy targets are commented out and preserved for historical reference only.

## Cross-stack export

The CFN stack still exports `root-login-alerts:sns:topic:arn`. Because the
stack is retained, the export remains valid for any consumer using
`!ImportValue`. New consumers should reference the SNS topic ARN through the
Terragrunt outputs in `ub-tf-infrastructure` rather than the CFN export.

## License

MIT License.  Please see [LICENSE](LICENSE) for more information.
