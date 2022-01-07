# Learn Terraform outputs

Learn how Terraform output values allow you to export structured data about your resources.

Follow along [with this
tutorial](https://learn.hashicorp.com/tutorials/terraform/outputs?in=terraform/configuration-language) on HashiCorp
Learn.


Authentication
Environment Variables

You can provide your credentials via the AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY, environment variables, representing your AWS Access Key and AWS Secret Key, respectively. Note that setting your AWS credentials using either these (or legacy) environment variables will override the use of AWS_SHARED_CREDENTIALS_FILE and AWS_PROFILE. The AWS_DEFAULT_REGION and AWS_SESSION_TOKEN environment variables are also used, if applicable:

provider "aws" {}

Usage:

$ export AWS_ACCESS_KEY_ID="anaccesskey"
$ export AWS_SECRET_ACCESS_KEY="asecretkey"
$ export AWS_DEFAULT_REGION="us-west-2"
$ terraform plan

Shared Credentials File

You can use an AWS credentials or configuration file to specify your credentials. The default location is $HOME/.aws/credentials on Linux and macOS, or "%USERPROFILE%\.aws\credentials" on Windows. You can optionally specify a different location in the Terraform configuration by providing the shared_credentials_file argument or using the AWS_SHARED_CREDENTIALS_FILE environment variable. This method also supports a profile configuration and matching AWS_PROFILE environment variable:

Usage:

provider "aws" {
  region                  = "us-west-2"
  shared_credentials_file = "/Users/tf_user/.aws/creds"
  profile                 = "customprofile"
}

Please note that the AWS Go SDK, the underlying authentication handler used by the Terraform AWS Provider, does not support all AWS CLI features.