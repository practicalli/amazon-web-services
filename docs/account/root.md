# Root account

A root account is used for administration of an Amazon Web Service (AWS) account. This includes management of IAM accounts which are used for day to day work and programmatic (code) access.

??? WARNING "Credit / Debit card required"
    A working credit card is required to setup a root account and AWS will charge the card $1 to verify identity and that the card is legitimate.  This amount will be returned within 3-5 days.

    Apart from the temporary charge, this approach should not incur any charges so long as the account stays within the free plan limits.  Recommend using a digital card that can be set to frozen when not explicitly used as a safety precaution.


## Create root account

Create a root account by [singing up for AWS](https://portal.aws.amazon.com/billing/signup#/start/email)

Enter an email for the root account and a name for the AWS account

![AWS Sign up website](https://github.com/practicalli/graphic-design/blob/live/cloud-services/aws/aws-sign-up-webpage.png?raw=true)

An email is sent to the address entered with a verification code.  Enter the code and select **Verify**

![AWS sign up website - verify code](https://github.com/practicalli/graphic-design/blob/live/cloud-services/aws/aws-sign-up-webpage-confirm-verification-code.png?raw=true)

Generate a secure password for the root account, e.g. using a Password Manager such as NordPass or 1Password

![AWS sign up website - set root account password](https://github.com/practicalli/graphic-design/blob/live/cloud-services/aws/aws-sign-up-webpage-root-password.png?raw=true)

> Save the account password with your favourite password manager


Select **Personal** plan as this account is only used for personal projects & hacking (not cracking).

Complete contact information with your actual details (used when AWS confirms the credit card is legitimate) and confirm the [AWS Customer Agreement](https://aws.amazon.com/agreement/).

![AWS sign up website - contact details](https://github.com/practicalli/graphic-design/blob/live/cloud-services/aws/aws-sign-up-webpage-contact-information.png?raw=true)

Enter details of a valid credit/debit card.  AWS will charge $1 to the card, which will be returned in 3-5 days.

![AWS sign up - billing information](https://github.com/practicalli/graphic-design/blob/live/cloud-services/aws/aws-sign-up-webpage-billing-information.png?raw=true)


**Confirm identity**

> NOTE: do not include spaces in the security code even if they are in the image

Select **Send SMS**

![AWS sign up website - select confirm identity method](https://github.com/practicalli/graphic-design/blob/live/cloud-services/aws/aws-sign-up-webpage-confirm-identity.png?raw=true)


Confirm identity pin number

4 digit code (dont use the 5 digit phone number by mistake)

![AWS sign up website - confirm identity code](https://github.com/practicalli/graphic-design/blob/live/cloud-services/aws/aws-sign-up-webpage-confirm-identity-code.png?raw=true)

Select support plan - **Basic support - Free**

Select **Complete Sign up**

![AWS sign up website - select basic support plan](https://github.com/practicalli/graphic-design/blob/live/cloud-services/aws/aws-sign-up-webpage-support-plan-basic-free.png?raw=true)

Congratulations


An email will be sent to the root account address once the account is ready, which make take a few minutes.

Take a break from the form filling by stretching and taking some deep breaths.

![AWS sign up website - congratulations](https://github.com/practicalli/graphic-design/blob/live/cloud-services/aws/aws-sign-up-webpage-congratulations.png?raw=true)


## Multi-factor authentication

Visit the IAM dashboard and assign Multi-Factor authentication (MFA) to the root user account for additional security.

Select **Assign MFA**

![AWS IAM Dashboard](https://github.com/practicalli/graphic-design/blob/live/cloud-services/aws/aws-management-console-iam-security-credentials-root-user.png?raw=true){loading=lazy}

Specify MFA device name and select MFA device

!!! HINT "Authy Authentication App"
    Practicalli uses the [Authy app](https://authy.com/) to generate Multi-Factor authentication codes for all services

![AWS IAM Dashboard](https://github.com/practicalli/graphic-design/blob/live/cloud-services/aws/aws-management-console-iam-security-credentials-assign-mfa-device.png?raw=true){loading=lazy}

Set up authenticator app

![AWS IAM Dashboard](https://github.com/practicalli/graphic-design/blob/live/cloud-services/aws/aws-management-console-iam-security-credentials-assing-mfa-device-setup.png?raw=true){loading=lazy}

The MFA device is now assigned

![AWS IAM Dashboard](https://github.com/practicalli/graphic-design/blob/live/cloud-services/aws/aws-management-console-iam-security-credentials-assign-mfa-device-confirmation.png?raw=true){loading=lazy}

