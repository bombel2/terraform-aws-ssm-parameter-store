# Terraform API Gateway Module

## About:

This Terraform module creates Systems Manager Parameters and uses standard prefixes ``environment`` and ``application_name`` for your parameters.

For instance:
``/dev/example/cognito_user_pool_arn``

## How to use:

```terraform
module "ssm_parameters" {
  source = "github.com/rpstreef/terraform-aws-ssm-parameter-store?ref=master"

  application_name = "example"
  environment      = "dev"

  parameters = {
    "cognito_user_pool_arn" = {
      "type"  = "String"
      "value" = module.cognito.cognito_user_pool_arn
    },
    "cognito_user_pool_client_id" = {
      "type"  = "String"
      "value" = module.cognito.cognito_user_pool_client_id
    },
    "cognito_identity_pool_id" = {
      "type"  = "String"
      "value" = module.cognito.cognito_identity_pool_id
    }
  }
}
```

## Changelog

### v1.0

Initial release