# Practicalli Amazon Web Services (AWS)

Amazon web services are an ever increasing and evolving set of Cloud services to support a wide range of deployment requirements for custom software services.  AWS also includes a growing number of off-the-shelf services, especially in the realm of data science.

> Practicalli content focuses on tools and services the team has used for commercial projects, so will not cover all services offered

??? HINT "Localstack provides AWS services locally"
    Use [Localstack](https://docs.localstack.cloud/getting-started) instead of creating an account if only using the services locally.

    Localstack [implements many of the AWS services](https://docs.localstack.cloud/references/coverage/), although some services are only commercially available


## Getting Started

=== "Personal projects"
    [:fontawesome-solid-book-open: Setup Root and IAM accounts](accounts/)

    - Find a valid credit / debit card needed to create the account (temporary $1 charge)
    - Create a root account for to administer the overall AWS account
    - Create an IAM account with Management Console login for working with AWS services
    - Create an IAM account for services to access AWS (non-login)

=== "Commercial projects"
    Ask the AWS administrator within the organisation to create an IAM user fs

    Specify the access required or identify a colleague that has the same AWS access required

[:fontawesome-solid-book-open: Install AWS CLI version 2](/amazon-web-services/tools/aws-cli/)

[:fontawesome-solid-book-open: Configure access via the IAM account](/amazon-web-services/tools/aws-cli/#create-local-configuration)

[Start Hacking](clojure/)


## Resources

[Practicalli Books and Videos](https://practical.li){target=_blank .md-button}
[Practicalli YouTube channel](https://youtube.co/practicalli){target=_blank .md-button}

[Getting Started with AWS](https://aws.amazon.com/getting-started/){target=_blank .md-button}
[AWS Developer Center](https://aws.amazon.com/developer/){target=_blank .md-button}

[AWS Regions and Availability Zones map](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/){target=_blank .md-button}

[AWS Region Names](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html#concepts-available-regions){target=_blank .md-button}

[AWS Architecture Center](https://aws.amazon.com/architecture/){target=_blank .md-button}
[Kindle Architecture white-papers](https://www.amazon.co.uk/s?i=digital-text&rh=p_27%3AAmazon+Web+Services){target=_blank .md-button}


## Navigate the book

Use the mouse or built-in key bindings to navigate the pages of the book

- ++p++ , ++comma++ : go to previous page
- ++n++ , ++period++ : go to next page

Use the search box to quickly find a specific topic

- ++f++ , ++s++ , ++slash++ : open search dialog
- ++arrow-down++ , ++arrow-up++ : select next / previous result
- ++esc++ , ++tab++ : close search dialog
- ++enter++ : follow selected result


## Sponsor Practicalli

[![Sponsor practicalli-john](https://raw.githubusercontent.com/practicalli/graphic-design/live/buttons/practicalli-github-sponsors-button.png){align=left loading=lazy}](https://github.com/sponsors/practicalli-john/){target=_blank}

All sponsorship recieved is used to maintain and further develop the [Practicalli series of books and videos](https://practical.li/){target=_blank}, although most of the work is still done with my own time and cost.

Thank you to [Cognitect](https://www.cognitect.com/){target=_blank}, [Nubank](https://nubank.com.br/){target=_blank} and a wide range of other [sponsors](https://github.com/sponsors/practicalli-john#sponsors){target=_blank} from the Clojure community for your continued support


## Creative commons license

<div style="width:95%; margin:auto;">
  <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a>
  This work is licensed under a Creative Commons Attribution 4.0 ShareAlike License (including images & stylesheets).
</div>
