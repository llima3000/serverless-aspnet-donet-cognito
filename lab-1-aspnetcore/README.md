# Lab 0: Creating the AspNetCore applicatoin

The steps in this lab will create a new AWS lambda AspNetCore to act as your main website. We will also install all the required nuget packages and add/change the code for the workshop.


## Step 1: using dotnet cli to create a new project


1. Open a shell command or a Powershell command prompt.
2. Verify that you have the Serverless templates by typing:
   ```
   dotnet new
   ```
3. Make sure you find templates names starting with *Lambda*. In case you can't see then, please check the requirements of this workshop.
4. Create the WebApp project using the following command:
   ```
   dotnet new serverless.AspNetCoreWebApp --name WebApp
   ```
5. You now have a directory called WebApp with a C# project template for AspNetCore application.

### Opening your project at VSCode

1. Open VSCode. Go to File -> *Open Folder* and select the WebApp folder created on the previous step. It will load all the sub-directories and files for you.

   <img src="../images/vscodewebapp.png" width="250"/>

### Install nuget packages

1. Right-cling on the WebApp directory that sits below of src directory and select *Open in Terminal*.

   <img src="../images/vscodeterminal.png" width="450"/>

2. At VSCOde terminal window install all the nuget packages by typing:

   <img src="../images/vscodenuget.png" width="450"/>

3. Add all these packages:
   ```
   dotnet add package Newtonsoft.Json
   dotnet add package AWSSDK.Lambda
   dotnet add package Amazon.Lambda.Core
   dotnet add package AWSSDK.Extensions.NETCore.Setup
   dotnet add package AWSSDK.CognitoIdentityProvider
   dotnet add package AWS.Logger.Core
   dotnet add package Amazon.Lambda.APIGatewayEvents
   dotnet add package AspNetCore.DataProtection.Aws.S3 -v 2.0.2
   dotnet add package AWSXRayRecorder
   ```
4. You can verify if all the packages were installed by looking at the WebApp.csproj
   ```
   cat WebApp.csproj
   ```
5. At the terminal windows, let's confirm that our code compiles with no errors
   ```
   dotnet publish -c Release
   ```

### Change the project files

***You have now completed this module and can move onto [module 4](./Module4.md).***
