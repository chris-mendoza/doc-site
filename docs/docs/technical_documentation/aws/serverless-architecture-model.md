## Serverless Architecture Model

The AWS Serverless Application Model (AWS SAM) is a toolkit that improves the developer experience of building and running serverless applications on AWS. AWS SAM consists of two primary parts:

1. AWS SAM template specification – An open-source framework that you can use to define your serverless application infrastructure on AWS.

2. AWS SAM command line interface (AWS SAM CLI) – A command line tool that you can use with AWS SAM templates and supported third-party integrations to build and run your serverless applications.

### Installation

#### Download AWS SAM
`wget -O aws-sam-cli-linux-x86_64.zip https://github.com/aws/aws-sam-cli/releases/latest/download/aws-sam-cli-linux-x86_64.zip`

#### Unzip AWS SAM
`unzip aws-sam-cli-linux-x86_64.zip -d sam-installation`

#### Install AWS SAM with sudo
`sudo ./sam-installation/install`

#### Check AWS SAM version after install

`sam --version`

#### Create directory and Initialize it with `sam`

`mkdir sam-hello-world`

`sam init`

#### Build application

`sam build`

### Useful Links

<https://github.com/aws/aws-sam-cli-app-templates>