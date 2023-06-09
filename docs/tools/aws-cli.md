# AWS Command Line Interface - CLI

The [AWS Command Line Interface (AWS CLI)](https://aws.amazon.com/cli/) is a unified tool to manage your AWS services. With just one tool to download and configure, you can control multiple AWS services from the command line and automate them through scripts.

!!! EXAMPLE "Practicalli dotfiles .aws/config"
    [practicalli/dotfiles .aws/config file](https://github.com/practicalli/dotfiles/blob/main/aws/config) is an example of an AWS Config with profiles and Okta single sign-on

??? INFO "AWS CLI 2 version"
    print the currently installed version
    ```shell
    aws --version
    ```
    The output should be similar to:
    ```shell
    aws-cli/2.11.20 Python/3.11.3 Linux/5.15.0-71-generic exe/x86_64.ubuntu.22 prompt/off
    ```

## Install

Download the relevant install from [AWS Command Line Interface website](https://aws.amazon.com/cli/)


=== "Linux"

    [Install and update guide](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html#cliv2-linux-install){target=_blank .md-button}

    Check the [AWS CLI version 2 changelog](https://raw.githubusercontent.com/aws/aws-cli/v2/CHANGELOG.rst){target=_blank} to see the latest version available.

    > The script will install AWS CLI in `usr/local/` by default, although this can be overriddent with `--bin-dir` and `--install-dir` options on the `aws/install` command.

    Download the install script archive file
    ```shell
    curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
    ```
    Extract the install script, ideally to the local application directory for the user for later updates.
    ```shell
    unzip awscliv2.zip -d ~/.local/apps
    ```
    Run the install script, providing the user password when prompted
    ```shell
    sudo ~/.local/apps/aws/install
    ```

    Update via the `install` script in the extracted awscliv2 archive
    ```shell
    sudo ~/.local/apps/aws/install --bin-dir /usr/local/bin --install-dir /usr/local/aws-cli --update
    ```



## Create local configuration

[Setup AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-quickstart.html){target=_blank .md-button}

> `aws configure` provides a wizard for some kinds of credentials but not all.  `aws configure set` will set specific variables and values

Create an IAM user for programmatic access using a group (create if neccessary) that include the Permission profiles for the services that will be accesses.

Copy the ARN for the IAM user (login as root user if the IAM user does not have web console login - which ideally it should not)

=== "Short Term Credentials"
    [:globe_with_meridians: Authenticating using short-term credentials](https://docs.aws.amazon.com/cli/latest/userguide/cli-authentication-short-term.html){target=_blank .md-button}

    !!! WARNING "Session Token have 12 hours maximum life"

    Create Access Keys in an IAM user to get values for `AWS Access Key ID` and `AWS Secret Access Key`.

    Use the AWS CLI configuration wizard to set up most of the configuration :)

    !!! EXAMPLE "AWS CLI configure short-term credentials"
    ```shell
    aws configure
    ```
    Example ouput
    ```shell
    AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
    AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
    Default region name [None]: us-west-2
    Default output format [None]: json
    ```

    A `default` profile is created in `"~/.aws/config"` with the above values

    Optionally edit the `"~/.aws/config"` file and add additional environment variables and profiles

    DO NOT Create a session token, its not required.


=== "IAM role"

    Profiles which use IAM roles pull credentials from another profile and then apply IAM role permissions.

    `default` is the source profile for credentials and jr0cket-cli borrows the same credentials then assumes a new role.

    Use the aws cli to set specific environment variables for the IAM role.

    ```shell
    aws configure set
    ```
    Example commands
    ```shell
    aws configure set role_arn arn:aws:iam::123456789012:role/defaultrole
    aws configure set source_profile default
    aws configure set role_session_name session_user1
    aws configure set region us-west-2
    aws configure set output json
    ```

=== "IAM Idetity Center"

    Requires a single sign-on token provider, e.g. [Okta](https://developer.okta.com/){target=_blank}, Active Directory, LDAP service, etc.

    ```shell
    aws configure sso
    ```

    Example output
    ```shell
    SSO session name (Recommended): my-sso
    SSO start URL [None]: https://my-sso-portal.awsapps.com/start
    SSO region [None]:us-east-1
    ```

    Attempting to automatically open the SSO authorization page in your default browser.

    There are 2 AWS accounts available to you.
    > DeveloperAccount, developer-account-admin@example.com (111122223333)
      ProductionAccount, production-account-admin@example.com (444455556666)

    Using the account ID 111122223333

    There are 2 roles available to you.
    > ReadOnly
      FullAccess

    Using the role name "ReadOnly"

    CLI default client Region [None]: us-west-2
    CLI default output format [None]: json
    CLI profile name [123456789011_ReadOnly]: user1
    ```

    !!! EXAMPLE "Practicalli dotfiles .aws/config"
        [practicalli/dotfiles .aws/config file](https://github.com/practicalli/dotfiles/blob/main/aws/config-sso-okta){target=_blank} is an example of an AWS Config with profiles and Okta single sign-on


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


## AWS CloudShell

AWS Linux instance running in AWS with pre-configured accounts and tools to provide CLI access to AWS services
