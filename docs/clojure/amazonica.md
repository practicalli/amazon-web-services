# Amazonica

!!! WARNING "Very Rough Draft"

![Amazonica logo](https://github.com/mcohen01/amazonica/blob/master/claws.png?raw=true){align=right loading=lazy}

A comprehensive Clojure client for the entire [Amazon AWS API][1], essentially a wrapper acound the Java client library for AWS.

[![amazonica](https://circleci.com/gh/mcohen01/amazonica.svg?style=shield)](https://app.circleci.com/pipelines/github/mcohen01/amazonica)


!!! WARNING "Examples in Amazonica project readme not working"


## Project Dependency

Add amazonica as a project dependency, to either a Clojure CLI or Leiningen project.

=== "Clojure CLI"
    ```clojure title="deps.edn"
    amazonica/amazonica {:mvn/version "0.3.165"}
    ```

=== "Leiningen"
    ```clojure title="project.clj"
    [amazonica "0.3.165"]
    ```


## Basic example

```clojure
(ns com.example
  (:require [amazonica.aws.ec2 :as aws-ec2]))

(aws-ec2/describe-instances)

(aws-ec2/create-snapshot
  :volume-id   "vol-8a4857fa"
  :description "snapshot for testing")
```

Amazonica uses the Java client library to support the complete set of remote service calls implemented by each of the service-specific AWS client classes (e.g. AmazonEC2Client, AmazonS3Client, etc.)

- [AWS Javadocs][2]. 
- [cljdoc function references][25] 

Reflection is used to create idiomatically named Clojure Vars in the library namespaces corresponding to the AWS service. 

camelCase Java methods become lower-case, hyphenated Clojure functions. 


!!! EXAMPLE "Create snapshot of running EC2 instance"
    ```clojure
    (aws-ec2/create-snapshot
      :volume-id "vol-8a4857fa"
      :description "my_new_snapshot")
    ```

aws-ec2/create-snapshot delegates to [createSnapshot()][3] method of AmazonEC2Client. 

Java methods that take a parameter, e.g. [CreateSnapshotRequest][4] have their bean properties exposed via mutators and can be supplied as key-value pairs passed as arguments to the Clojure function.

All of the AWS Java APIs (except S3) follow this pattern, either having a single implementation method that takes an AWS Java bean as its only argument, or being overloaded and having a no-arg implementation. 

The corresponding Clojure function will either require key-value pairs as arguments, or be variadic and allow a no-arg invocation.

AmazonEC2Client's [describeImages()][7] method is overloaded and can be invoked either with no args or with a [DescribeImagesRequest][8]. 

Clojure invocation 

```clojure
(aws-ec2/describe-images)
```

or

```clojure
(aws-ec2/describe-images
  :owners ["self"]
  :image-ids ["ami-f00f9699" "ami-e0d30c89"])
```


??? INFO "Supported Services"
    AWS services supported by Amazonica
    * Amplify
    * API Gateway
    * AppConfig
    * Application Insights
    * App Mesh
    * Augmented AI
    * [Autoscaling](#autoscaling)
    * Austocaling Plans
    * Backup
    * [Batch](#batch)
    * Budgets
    * Certificate Manager
    * CloudDirectory
    * [CloudFormation](#cloudformation)
    * [CloudFront](#cloudfront)
    * [CloudSearch](#cloudsearch)
    * [CloudSearchV2](#cloudsearchv2)
    * [CloudSearchDomain](#cloudsearchdomain)
    * [CloudWatch](#cloudwatch)
    * [CloudWatchEvents](#cloudwatchevents)
    * CodeBuild
    * CodeCommit
    * [CodeDeploy](#codedeploy)
    * CodePipeline
    * CodeStar
    * Cognito
    * [CognitoIdentityProviders](#cognitoidentityproviders)
    * [Comprehend](#comprehend)
    * Compute Optimizer
    * Config
    * Connect
    * CostAndUsageReport
    * CostExplorer
    * DatabaseMigrationService
    * [DataPipeline](#datapipeline)
    * Data Exchange
    * Data Sync
    * Dax
    * Detective
    * DeviceFarm
    * DirectConnect
    * Directory
    * DLM
    * DocDB
    * [DynamoDBV2](#dynamodbv2)
    * [EC2](#ec2)
    * [EC2InstanceConnect](#ec2instanceconnect)
    * [ECR](#ecr)
    * [ECS](#ecs)
    * [ElastiCache](#elasticache)
    * [ElasticBeanstalk](#elasticbeanstalk)
    * ElasticFileSystem
    * [ElasticLoadBalancing](#elasticloadbalancing)
    * [ElasticMapReduce](#elasticmapreduce)
    * [Elasticsearch](#elasticsearch)
    * [ElasticTranscoder](#elastictranscoder)
    * Event Bridge
    * [Forecast](#forecast)
    * Fraud Detector
    * GameLift
    * [Glacier](#glacier)
    * Global Accelerator
    * Glue
    * GreenGrass
    * Groundstation
    * GuardDuty
    * [IdentityManagement](#identitymanagement)
    * Image Builder
    * ImportExport
    * [IoT](#iot)
    * Kafka
    * Kendra
    * [Kinesis](#kinesis)
    * [Kinesis Analytics](#kinesisanalytics)
    * [KinesisFirehose](#kinesisfirehose)
    * Kinesis Video Streams with WebRTC (Signaling Channels)
    * [KMS](#kms)
    * Lake Formation
    * [Lambda](#lambda)
    * Lex
    * Lightsail
    * [Logs](#logs)
    * MachineLearning
    * Macie
    * Managed Blockcahin
    * MechanicalTurk
    * MediaConvert
    * MediaLive
    * MediaPackage
    * MediaStore
    * MigrationHub
    * Mobile
    * MQ
    * MSK (Managed Kafka)
    * [OpsWorks](#opsworks)
    * Personalize
    * [Pinpoint](#pinpoint)
    * Pricing
    * Polly
    * QLDB
    * Quicksight
    * RDS
    * [Redshift](#redshift)
    * Rekognition
    * [Route53](#route53)
    * [Route53Domains](#route53domains)
    * [S3](#s3)
    * Sagemaker
    * Secrets Manager
    * Security Hub
    * Security Token
    * ServerMigration
    * ServiceCatalog
    * Service Discovery
    * Shield
    * [SimpleDB](#simpledb)
    * [SimpleEmail](#simpleemail)
    * [SimpleSystemsManager](#SimpleSystemsManager)
    * [SimpleWorkflow](#simpleworkflow)
    * Snowball
    * [SNS](#sns)
    * [SQS](#sqs)
    * [StepFunctions](#stepfunctions)
    * StorageGateway
    * Support
    * Textract
    * Timestream
    * Transcribe
    * Transfer
    * Translate
    * WAF
    * Workspaces
    * XRay
