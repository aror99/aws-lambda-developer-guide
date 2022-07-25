# Create a function defined as a container image<a name="gettingstarted-images"></a>

In this getting started exercise, you create a function defined as a container image\. First, you use the Docker CLI to create a container image for your function code, and then use the Lambda console to create a function from the container image\.

**Topics**
+ [Prerequisites](#gettingstarted-images-prereq)
+ [Create the container image](#gettingstarted-images-package)
+ [Upload the image to the Amazon ECR repository](#gettingstarted-create-upload)
+ [Update the user permissions](#gettingstarted-images-permissions)
+ [Create a Lambda function defined as a container image](#gettingstarted-images-function)
+ [Invoke the Lambda function](#get-started-invoke-function)
+ [Clean up](#gettingstarted-image-cleanup)

## Prerequisites<a name="gettingstarted-images-prereq"></a>

To complete the following steps, you need a command line terminal or shell to run commands\. Commands and the expected output are listed in separate blocks:

```
aws --version
```

You should see the following output:

```
aws-cli/2.0.57 Python/3.7.4 Darwin/19.6.0 exe/x86_64
```

For long commands, an escape character \(`\`\) is used to split a command over multiple lines\.

On Linux and macOS, use your preferred shell and package manager\. On Windows 10, you can [install the Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10) to get a Windows\-integrated version of Ubuntu and Bash\.

This exercise uses Docker CLI commands to create the container image\. To install the Docker CLI, see [Get Docker](https://docs.docker.com/get-docker) on the Docker Docs website\.

## Create the container image<a name="gettingstarted-images-package"></a>

AWS provides a set of base images in the Amazon Elastic Container Registry \(Amazon ECR\)\. In this getting started exercise, we use the Node\.js base image to create a container image\. For more information about base images, see [ AWS base images for Lambda](runtimes-images.md#runtimes-images-lp)\.

In the following commands, replace `123456789012` with your AWS account ID\.

**To create an image using the AWS Node\.js 14 base image**

1. On your local machine, create a project directory for your new function\.

1. Create a file named `app.js` in your project directory\. Add the following code to `app.js`:

   ```
   exports.handler = async (event) => {
     // TODO implement
     const response = {
         statusCode: 200,
         body: JSON.stringify('Hello from Lambda!'),
     };
     return response;
   };
   ```

1. Use a text editor to create a new file named `Dockerfile` in your project directory\. Add the following content to `Dockerfile`:

   ```
   FROM public.ecr.aws/lambda/nodejs:14
   
   # Copy function code  
   COPY app.js ${LAMBDA_TASK_ROOT}
   
   # Set the CMD to your handler
   CMD [ "app.handler" ]
   ```

1. Build your Docker image\. From your project directory, run the following command:

   ```
   docker build -t hello-world .
   ```

1. \(Optional\) AWS base images include the Lambda runtime interface emulator, so you can test your function locally\. 

   1. Run your Docker image\. From your project directory, run the `docker run` command:

      ```
      docker run -p 9000:8080 hello-world:latest
      ```

   1. Test your Lambda function\. In a new terminal window, run a `curl` command to invoke your function:

      ```
      curl -XPOST "http://localhost:9000/2015-03-31/functions/function/invocations" -d '{}'
      ```

## Upload the image to the Amazon ECR repository<a name="gettingstarted-create-upload"></a>

1. Authenticate the Docker CLI to your Amazon ECR registry\.

   ```
   aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 123456789012.dkr.ecr.us-east-1.amazonaws.com
   ```

1. Create a repository in Amazon ECR using the `create-repository` command\.

   ```
   aws ecr create-repository --repository-name hello-world --image-scanning-configuration scanOnPush=true --image-tag-mutability MUTABLE
   ```

1. Tag your image to match your repository name using the `docker tag` command\. 

   ```
   docker tag  hello-world:latest 123456789012.dkr.ecr.us-east-1.amazonaws.com/hello-world:latest
   ```

1. Deploy the image to Amazon ECR using the `docker push` command\. 

   ```
   docker push 123456789012.dkr.ecr.us-east-1.amazonaws.com/hello-world:latest
   ```

## Update the user permissions<a name="gettingstarted-images-permissions"></a>

Make sure that the permissions for the IAM user or role that creates the function contain the AWS managed policies `GetRepositoryPolicy` and `SetRepositoryPolicy`\. For information about user permissions to access images in the Amazon ECR repository, see [ Amazon ECR permissions](configuration-images.md#configuration-images-permissions)

For example, use the IAM console to create a role with the following policy:

```
{
"Version": "2012-10-17",
"Statement": [
  {
  "Sid": "VisualEditor0",
  "Effect": "Allow",
  "Action": ["ecr:SetRepositoryPolicy","ecr:GetRepositoryPolicy"],
  "Resource": "arn:aws:ecr:<region>:<account>:repository/<repo name>/"
  }
]
}
```

## Create a Lambda function defined as a container image<a name="gettingstarted-images-function"></a>

Use the Lambda console to create a function defined as a container image\.

**To create the function with the console**

1. Open the [Functions page](https://console.aws.amazon.com/lambda/home#/functions) on the Lambda console\.

1. Choose **Create function**\.

1. Choose the **Container image** option\.

1. Under **Basic information**, do the following:

   1. For **Function name**, enter **my\-function**\.

   1. For **Container image URI**, enter the URI of the Amazon ECR image that you created previously\.

1. Choose **Create function**\.

Lambda creates your function and an [execution role](lambda-intro-execution-role.md) that grants the function permission to upload logs\. Lambda assumes the execution role when you invoke your function, and uses the execution role to create credentials for the AWS SDK and to read data from event sources\.

