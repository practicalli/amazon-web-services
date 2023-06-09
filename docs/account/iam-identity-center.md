# IAM Identity Center

!!! WARNING "Email confirmation may not arrive"
    Dont wait for an email to say that the Identity Center is ready, it may never come.  Practicalli never recieved an email.

IAM Identity Center can manage accounts and provide credentials to enable access to AWS services.

Use Identity Center to manage IAM user accounts and groups in its own directory.  Or use accounts managed via an external identity provider, e.g.

- Microsoft Active Directory Domain Services
- Okta Universal Directory
- Microsoft Azure AD

[:globe_with_meridians: AWS Docs - IAM Identity Center - Getting Started](https://docs.aws.amazon.com/singlesignon/latest/userguide/getting-started.html){target=_blank .md-button}

??? INFO "IAM Identity Center is has no charge"

??? INFO "IAM Identity Center replaces the AWS Single Sign-on service"

<!--
AWS Blurb
AWS IAM Identity Center makes it easy to centrally manage access to multiple AWS accounts and provide users with single sign-on access to all their assigned accounts from one place. With IAM Identity Center, you can create and manage user identities in IAM Identity Center or easily connect to your existing SAML 2.0 compatible identity provide
-->

## Requirements

AWS Organisation is required for IAM Identity Center. An Organisation can be created when enabling the AWS IAM Identity Center

Existing IAM accounts should be well within [:globe_with_meridians: quota limits](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-quotas.html#reference_iam-quotas-entities){target=_blank .md-button}

## Enable IAM Identity Center

Sign in to AWS Management Console using the Root user account

Search for and select the IAM Identity Center

![AWS Management Console - search for IAM Identity Service](){loading=lazy}

Select **Enable** button on the IAM Identity Center page

![AWS IAM Identity Service - enable button](){loading=lazy}

IAM Identity Center requires AWS Organizations.

![AWS IAM Identity Service - organisation required](){loading=lazy}

Select **Create AWS organization** or choose and existing organisation

![AWS IAM Identity Service - organisation required](){loading=lazy}

AWS Organizations automatically sends a verification email to the address that is associated with your management account. There might be a delay before you receive the verification email. Verify your email address within 24 hours.

### Choose your identity source

Your identity source in IAM Identity Center defines where your users and groups are managed. You can choose one of the following as your identity source:

Identity Center directory – When you enable IAM Identity Center for the first time, it is automatically configured with an Identity Center directory as your default identity source. This is where you create your users and groups, and assign their level of access to your AWS accounts and applications.

## Integrate with AWS CLI

Sign-in using the credentials defined in IAM Identity Center or external identity provider

Use Named role profiles in AWS CLI configuration to run commands in desired accounts and roles.

AWS CLI manages short-term credentials automatically so developers can start in and stay in the CLI securely without interruption, and run long running scripts

[Configure AWS CLI for AWS IMA Identity Center](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-sso.html){target=_blank .md-button}
[Integrate AWS CLI with IAM Identity Center](https://docs.aws.amazon.com/singlesignon/latest/userguide/integrating-aws-cli.html){target=_blank .md-button}

## Terminology

- Workforce identities: human users

[AWS IAM Identity Center quotas](https://docs.aws.amazon.com/singlesignon/latest/userguide/limits.html){target=_blank .md-button}

Not relevant for IAM Identity Center

!!! HINT "AWS Resources Search"
    Type /Resources (forward slash) to focus search results on resources such as EC2 instances, S3 buckets, and more.
