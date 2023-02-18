# AWS Command Line Interface - CLI

The [AWS Command Line Interface (AWS CLI)](https://aws.amazon.com/cli/) is a unified tool to manage your AWS services. With just one tool to download and configure, you can control multiple AWS services from the command line and automate them through scripts.

!!! EXAMPLE "Practicalli dotfiles .aws/config"
    [practicalli/dotfiles .aws/config file](https://github.com/practicalli/dotfiles/blob/main/aws/config) is an example of an AWS Config with profiles and Okta single sign-on


## Creating profiles for environments

Software engineering teams should have the ability to deploy on at least a test and staging environment (with production typically kept for operations focused roles or teams).

The AWS CLI can have multiple profiles with configuration specific to the environment.

```shell
## Default settings used with all profiles
# [default]
# region = eu-west-2


# [profile test]
# role_arn = arn:aws:iam::************:role/Developer
# mfa_serial = arn:aws:iam::************:mfa/my.email@company-domain.com
# source_profile = default

# [profile staging]
# role_arn = arn:aws:iam::************:role/Developer
# mfa_serial = arn:aws:iam::************:mfa/my.email@company-domain.com
# source_profile = default
```


## Okta Single Sign-on

Okta is a widely used Single Sign-on solution for managing access to business apps as well as Amazon Web Services (AWS) console and APIs.

Define a profile (optional, but recommended) that contains the URL for the Okta single sign-on service and its authorisation endpoint.

Define an `sso_region` that matches the AWS region in which the AWS profile should operate within.

Add and `sso_account_id` and `sso_role_name` to define identity within AWS.

```shell
[profile domain-staging]
sso_start_url = https://<sso-domain>.com/start
sso_region = eu-west-2
sso_account_id = <arn:aws:iam value>
sso_role_name = PowerUserAccess
region = eu-west-2
```


## AWS Shell
