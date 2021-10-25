# OK

# What is AWS Lambda?<a name="welcome"></a>

 [Lenguajes que soporte Lambda](lambda-runtimes.md)\.

**Topics**
+ [Lambda features](#features)
+ [Getting started with Lambda](#welcome-first-time-user)

## Lambda features<a name="features"></a>

The following key features help you develop Lambda applications that are scalable, secure, and easily extensible:

**Concurrency and scaling controls**  
[Concurrency and scaling controls](invocation-scaling.md) such as concurrency limits and provisioned concurrency give you fine\-grained control over the scaling and responsiveness of your production applications\.

**Functions defined as container images**  
Use your preferred [container image](lambda-images.md) tooling, workflows, and dependencies to build, test, and deploy your Lambda functions\.

**Code signing**  
[Code signing](configuration-codesigning.md) for Lambda provides trust and integrity controls that let you verify that only unaltered code that approved developers have published is deployed in your Lambda functions\.

**Lambda extensions**  
You can use [Lambda extensions](runtimes-extensions-api.md) to augment your Lambda functions\. For example, use extensions to more easily integrate Lambda with your favorite tools for monitoring, observability, security, and governance\.

**Function blueprints**  
A function blueprint provides sample code that shows how to use Lambda with other AWS services or third\-party applications\. Blueprints include sample code and function configuration presets for Node\.js and Python runtimes\.

**Database access**  
A [database proxy](configuration-database.md) manages a pool of database connections and relays queries from a function\. This enables a function to reach high concurrency levels without exhausting database connections\.

**File systems access**  
You can configure a function to mount an [Amazon Elastic File System \(Amazon EFS\) file system](configuration-filesystem.md) to a local directory\. With Amazon EFS, your function code can access and modify shared resources safely and at high concurrency\.

## Getting started with Lambda<a name="welcome-first-time-user"></a>

If you are a first\-time user of Lambda, we recommend that you start with the following topics to help you learn the basics:

1. **Read the [Lambda product overview](http://aws.amazon.com/lambda/) and explore the [Lambda getting started](http://aws.amazon.com/lambda/getting-started/) page\.**

1. **To create and test a Lambda function using the Lambda console, try the [console\-based getting started exercise](getting-started.md)\.** This exercise teaches you about the Lambda programming model and other concepts\.

1. **If you are familiar with container image workflows, try the getting started exercise to [create a Lambda function defined as a container image](gettingstarted-images.md)\.**


