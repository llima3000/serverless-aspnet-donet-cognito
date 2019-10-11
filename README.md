## Build and monitor a secure Serverless app powered by AspNetCore WebApp with Amazon Cognito and x-Ray

In this workshop you'll deploy a serverless web application based on AspNetCore that leverages the Amazon Cognito Hosted UI for sign-up and sign-in. During the sign-in process, the AspNetCore application receives the JWT token from Amazon Cognito, processed by the standard DotNetCore OpenIdConnect library. The AspNetCore of this workshop uses [Razor Pages](https://docs.microsoft.com/en-us/aspnet/core/razor-pages/) for processing the views. The AspNetCore will interface with serverless dotnet backend via a RESTful web service call. The backened RESTful API is exposed via Amazon API Gateway, which is integrated with the same Amazon Cognito that issued the JWT token for the AspNetCore, for authentication enforcement.  

See the diagram below for a depiction of the complete architecture.

![AspNetCore WebApp Architecture](images/diagram.jpeg)

## Initial environment setup

### Prerequisites

#### Laptop Machine

**Before you start reading all the Pre-requisites, there is an option to execute a [Cloudformation script](cfn-templates/webdevbox.yml) that installs all the software required for you into a EC2 Windows Server for the Lab. This is a perfect option if you don't have much time to prepare or if you are lazy to install all the software required.**

A laptop with Wi-Fi running Microsoft Windows and Mac OS X with the following softwares installed:
- An Internet browser such as Chrome, Firefox, Safari, or Edge.
- The AWSCLI for [Windows](https://docs.aws.amazon.com/cli/latest/userguide/install-windows.html) or [Mac](https://docs.aws.amazon.com/cli/latest/userguide/install-macos.html)
- The Long Term Support (LTS) [.NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version supported by [AWS Lambda for .NET Core](https://github.com/aws/aws-lambda-dotnet) installed. Links for downloading the supported version for [Windows](https://download.visualstudio.microsoft.com/download/pr/29f92590-ac92-45f0-99e8-e60c767dc4e9/ddc1014a788613364b5308d6c49db3db/dotnet-sdk-2.1.801-win-x64.exe) or [Mac](https://download.visualstudio.microsoft.com/download/pr/3998e58a-46dd-4f9c-a0e2-d17309de20fb/d694ddf3d8f99e8dee928e0b46f15084/dotnet-sdk-2.1.802-osx-x64.pkg)
  - It is possible to execute non-LTS .NET Core on AWS, as per this [blog](https://aws.amazon.com/blogs/developer/announcing-amazon-lambda-runtimesupport/). For simplicity, this workshop is based on the LTS .NET Core version.
- AWS extensions for the dotnet CLI.
  - After have installed dotnet in your machine execute the following program:
  ```
    dotnet tool install -g Amazon.Lambda.Tools
  ```
- [Docker for Windows](https://docs.docker.com/docker-for-windows/install/) or [Docker Desktop for Mac](https://docs.docker.com/docker-for-mac/install/)
- AWS SAM CLI
  - [Windows](https://github.com/awslabs/aws-sam-cli/releases/latest/download/AWS_SAM_CLI_64_PY3.msi)
  - Mac recommends installing AWS SAM CLI via [brew](https://brew.sh/). By following the commands:
  ```
    brew tap aws/tap
    brew install aws-sam-cli
  ```
- You favorite IDE for C# (VisualStudio or VSCode is recommended)
- An AWS account. You will create AWS resources including IAM roles during the workshop.
- An EC2 key pair created in the AWS region you are working in.




- This workshop can be run in any of AWS regions: US East (N. Virginia), US East (Ohio), US West (Oregon), Asia Pacific (Singapore) and EU (Ireland).
