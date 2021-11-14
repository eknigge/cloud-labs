# AWS S3 Bucket Automation

> Hands-on Lab

|                   |                       |
| :---------------- | :-------------------- |
| Cloud Vendor      | **Amazon AWS**   |
| Proficiency Level | **Cloud  Enthusiast** |
| Tags              | ![https://img.shields.io/badge/%20-Automation-blue](https://img.shields.io/badge/%20-Automation-blue) ![https://img.shields.io/badge/%20-S3-blue](https://img.shields.io/badge/%20-S3-blue) |

## Lab Scenario
In this lab, you will create an AWS S3 Bucket using a CloudFormation template and the AWS CLI.

Each exercise below builds upon the previous one. You should start each new exercise from the last step of the previous exercise unless it is explicitly written otherwise.

## What will you learn in this lab?
After completion of this lab, you will be able to:

- Configure AWS CLI on your machine
- Create AWS resource using CloudFormation template

## Prerequisites
To complete this lab, you will need the following:

- Reliable internet connection
- AWS access key

## Lab Instructions

### Exercise #1: Install and Configure AWS CLI

In this exercise you will install and configure the AWS CLI.

1. Download and install the latest AWS CLI version for your operating system from [this page](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).
2. Configure the AWS CLI by typing the following command in a terminal window:
   ```
   aws configure
   ```
3. Use the following values:
   - *AWS Access Key ID [None]:* `[your_access_key_id]`
   - *AWS Secret Access Key [None]:* `[your_secret_access_key]`
   - *Default region name [None]:* `us-west-2`
   - *Default output format [None]:* `JSON`

If you do not have your access key and secret access key, you will need to contact your instructor since this information is only generated once, and not available for future viewing.
#### Exercise Summary
At this point, you have learned how to install and configure AWS CLI on your machine.

### Exercise #2: Create an AWS S3 Bucket Using CloudFormation Template

In this exercise you will create an AWS S3 bucket using CloudFormation template.

1. Download the [template.yaml](template.yaml) to a folder on your local machine.
2. Deploy the CloudFormation template using the following command:
   ```
   aws cloudformation deploy --template-file template.yaml --parameter-overrides Email=[your_email_address] Name=[your_first_and_last_name] Initials=[your_initials] --stack-name [your_initials]-stack
   ```
3. Sign into the AWS Management console at [https://aws.amazon.com/console/](https://aws.amazon.com/console/) using your AWS credentials.
4. Go to the S3 service and validate that your S3 bucket is created.

#### Exercise Summary
At this point, you have learned how to deploy an AWS S3 bucket using a CloudFormation template.

## Help improve this lab

[![Lab Issues](https://img.shields.io/github/issues/crimsonpinnacle/cloud-labs)](https://github.com/CrimsonPinnacle/cloud-labs/issues/new?assignees=toddysm&labels=new+lab&template=bug_template.md&title=) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CrimsonPinnacle/cloud-labs/pulls)