# IAM Account



## Create IAM Account

Visit [aws.amazon.com](https://aws.amazon.com/) in a browser.

Sign In via the link in the top navigation bar, or select **Create an AWS Account**

Login using the Root account which is typically used to administrate all other accounts.

Search for  **Identity and Access Management (IAM)**

Select **IAM** > **Users**

Select **Add User**

Step 1:
- Enter user name `jr0cket-cli`
- Select Next

> do not provide access to the AWS management console for programmatic users

Step 2:

- Select **Create Group**
- enter user group name, e.g. `cli-access`
- search for Permission Policies, e.g. `s3`
- select checkbox next to relevant permission, e.g. `AmazonS3FullAccess`
- Select **Next**


Step 3:
- Select **Create User**

View the user to see th user passwork and email instructions for signing into the AWS Management Console (which we didnt select, so that seems to be a generic message)


## Configure CLI Access

- Access Keys for personal AWS Account (you are the owner of the whole account, not for commercial account)
- SSO & IAM Identity Center for commercial accounts

> Most other operations seem redundant


!!! INFO "AWS CloudShell"
    [AWS CloudShell](https://aws.amazon.com/cloudshell/) is a browser-based CLI for running commands.

    Essentially an Amazon Linux environment running in the AWS environment which can be connected to run commands

    assumption: code will need to be run in the Cloudshell environment to use the credentials or use a supported editor - VSCode or IntelliJ


=== "Access Keys"

    Access Keys have a maximum 12 hours lifespan (assumption: can be regenerated via the web console)

    Scroll to **Access Keys** section in IAM user view

    Select Create access keybinding

    Step 1 - Access key best practices and alternatives
    Select **Command Line Interface (CLI)**

    AWS form prompts with alternative recommendation (which should be used instead of this approach)

    !!! WARNING "Alternatives recommended"
        Use [AWS CloudShell](https://aws.amazon.com/cloudshell/), a browser-based CLI, to run commands

        Use the [AWS CLI V2](https://aws.amazon.com/cli/) and [enable authentication through a user in IAM Identity Center (SSO)](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-sso.html)

    Check *I understand the above recommendation and want to proceed to create an access key*


    Step 2 - set description tag:
    Optionally set a tag (maybe this helps search for things or provide some content about how the key is used)

    Select **Create access key**

    Step 3 - retrieve access keys
    Copy the Access Key and Secret access key to somewhere safe, e.g. a local GPG encrypted file

    Keep the page open and open a command line terminal to run the AWS CLI configuration wizard.

    > If running the aws cli config later, create a file called `~/.aws/access-keys.gpg`, add the Access Key and Secret Access Key and encrypt the file, e.g. `SPC a Y e` in spacemace, selecting a GPG key.

    [:globe_with_meridians: Recommended Practices for Access Keys](https://docs.aws.amazon.com/accounts/latest/reference/credentials-access-keys-best-practices.html){target=_blank .md-button}

    !!! WARNING "aws_session_token not required"
        The IAM user should be part of an AWS group and that group should be assigned the relevant service permissions, e.g. `AwsS3FullAccess`

        An AWS group can be created or assigne when creating a new IAM user or anytime after the user is created.
