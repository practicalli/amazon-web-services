# AWS Vault

AWS Vault is a tool to securely store and access AWS credentials in a development environment.

AWS Vault stores IAM credentials in the operating system secure keystore, generating temporary credentials to the shell and command line applications. Vault is designed to be complementary to the AWS CLI tools and is aware of profiles and configuration in `~/.aws/config`.


!!! EXAMPLE "Practicalli dotfiles .aws/config"
    [practicalli/dotfiles .aws/config file](https://github.com/practicalli/dotfiles/blob/main/aws/config) is an example of an AWS Config with profiles and Okta single sign-on

## Creating profiles


```bash
aws-vault exec practicalli-staging-sso -- aws ecr get-login-password
aws-vault exec practicalli-staging-sso -- env | grep AWS
```
