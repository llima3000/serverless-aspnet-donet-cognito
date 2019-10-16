# Lab 1: Creating the AspNetCore applicatoin

The steps in this lab will create a new AWS lambda AspNetCore to act as your main website. We will also install all the required nuget packages and add/change the code for the workshop.


## Step 1: using dotnet cli to create a new project


1. Open a shell command or a Powershell command prompt.
2. Install the AWS extensions for the dotnet CLI.
    ```
    dotnet tool install -g Amazon.Lambda.Tools
    ```
3. Install the Amazon.Lambda.Templates  blueprints by executing the following command :
   ```
   dotnet new -i "Amazon.Lambda.Templates::*"
   ```
4. To see a list of the Lambda templates execute *dotnet new lambda --list*
5. Create the WebApp project executing the following command:
   ```
   dotnet new serverless.AspNetCoreWebApp --name WebApp
   ```
   
6. You now have a directory called WebApp with a C# project template for AspNetCore application.

### Opening your project at VSCode

1. Open VSCode. Go to File -> *Open Folder* and select the WebApp folder created on the previous step. It will load all the sub-directories and files for you.

   <img src="../images/vscodewebapp.png" width="250"/>

### Install nuget packages

1. Right-cling on the WebApp directory that sits below of src directory and select *Open in Terminal*.

   <img src="../images/vscodeterminal.png" width="450"/>

2. At Visual Code terminal window install all the nuget packages by typing:

   <img src="../images/vscodenuget.png" width="450"/>

3. Add all these packages:
   ```
   dotnet add package Newtonsoft.Json -v 12.0.2
   dotnet add package AWSSDK.Lambda -v 3.3.103
   dotnet add package Amazon.Lambda.Core -v 1.1.0
   dotnet add package AWSSDK.Extensions.NETCore.Setup -v 3.3.100
   dotnet add package AWSSDK.S3 -v 3.3.104
   dotnet add package AWSSDK.CognitoIdentityProvider -v 3.3.103
   dotnet add package AWS.Logger.Core -v 1.4.0
   dotnet add package Amazon.Lambda.APIGatewayEvents -v 1.2.0
   dotnet add package AspNetCore.DataProtection.Aws.S3 -v 2.0.2
   dotnet add package AWSXRayRecorder -v 2.7.2
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

1. Open the file *Startup.cs* on VisualCode.
2. Replace its entire content with this [Script.cs](https://gist.github.com/arturlr/26c656f85b0aa9738414c8fdd7feff40)
3. Make sure you project still compiles.
    ```
    dotnet publish -c Release
    ```
4. 



***You have now completed this module and can move onto [module 4](./Module4.md).***
