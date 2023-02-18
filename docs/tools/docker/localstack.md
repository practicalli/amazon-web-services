# Local stack

![LocalStack](https://localstack.cloud/images/landing/laptop_stacks.svg#only-dark){align=right loading=lazy style="height:150px;width:150px"}

[LocalStack](https://github.com/localstack/localstack) is a cloud service emulator that runs in a single container on your laptop or in your CI environment. With LocalStack, you can run your AWS applications or Lambdas entirely on your local machine without connecting to a remote cloud provider! Whether you are testing complex CDK applications or Terraform configurations, or just beginning to learn about AWS services, LocalStack helps speed up and simplify your testing and development workflow.

LocalStack supports a growing number of AWS services, like AWS Lambda, S3, Dynamodb, Kinesis, SQS, SNS, and many more! The Pro version of LocalStack supports additional APIs and advanced features. You can find a comprehensive list of supported APIs on our ballot_box_with_check Feature Coverage page.

LocalStack also provides additional features to make your life as a cloud developer easier! Check out LocalStack's Cloud Developer Tools for more information.


=== "LocalStack CLI"
    Start localstack in a Docker image using the LocalStack cli

    ```shell
     % localstack start -d
    ```

    The output should look similar to

    ```shell
        / /   ____  _________ _/ / ___// /_____ ______/ /__
       / /   / __ \/ ___/ __ `/ /\__ \/ __/ __ `/ ___/ //_/
      / /___/ /_/ / /__/ /_/ / /___/ / /_/ /_/ / /__/ ,<
     /_____/\____/\___/\__,_/_//____/\__/\__,_/\___/_/|_|
    
     💻 LocalStack CLI 1.4.0
    
    [20:22:20] starting LocalStack in Docker mode 🐳
    [20:22:21] detaching
    ```

=== "Docker"
    
    ```shell
    docker run --rm -it -p 4566:4566 -p 4510-4559:4510-4559 localstack/localstack
    ```
