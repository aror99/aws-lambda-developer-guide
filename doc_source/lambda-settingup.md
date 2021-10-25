# OK

# Setting up with Lambda<a name="lambda-settingup"></a>

## AWS CLI<a name="lambda-settingup-awscli"></a>

To set up the AWS CLI, see the following topics in the *AWS Command Line Interface User Guide*\.
+ [Installing, updating, and uninstalling the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html)
+ [Configuring the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html)

To verify that the AWS CLI is configured correctly, run the `list-functions` command to see a list of your Lambda functions in the current AWS Region\.

```
aws lambda list-functions
```

## AWS SAM<a name="lambda-settingup-awssam"></a>

The AWS Serverless Application Model \(AWS SAM\) is an extension for the AWS CloudFormation template language that lets you define serverless applications at a higher level\. AWS SAM abstracts away common tasks such as function role creation, making it easier to write templates\. AWS SAM is supported directly by AWS CloudFormation, and includes additional functionality through the AWS CLI and AWS SAM CLI\.

For more information about AWS SAM templates, see the [AWS SAM specification](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-specification.html) in the *AWS Serverless Application Model Developer Guide*\.

## AWS SAM CLI<a name="lambda-settingup-samcli"></a>

The AWS SAM CLI is a separate command line tool that you can use to manage and test AWS SAM applications\. In addition to commands for uploading artifacts and launching AWS CloudFormation stacks that are also available in the AWS CLI, the AWS SAM CLI provides commands for validating templates and running applications locally in a Docker container\. You can use the AWS SAM CLI to build functions deployed as \.zip file archives or container images\.

To set up the AWS SAM CLI, see [Installing the AWS SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install.html) in the *AWS Serverless Application Model Developer Guide*\.


## Code authoring tools<a name="lambda-settingup-author"></a>

The following table lists the languages that Lambda supports, and the tools and options that you can use with them\.


****  

| Language | Tools and options for authoring code | 
| --- | --- | 
| Node\.js |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/lambda/latest/dg/lambda-settingup.html)  | 
| Java |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/lambda/latest/dg/lambda-settingup.html)  | 
| C\# |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/lambda/latest/dg/lambda-settingup.html)  | 
| Python |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/lambda/latest/dg/lambda-settingup.html)  | 
| Ruby |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/lambda/latest/dg/lambda-settingup.html)  | 
| Go |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/lambda/latest/dg/lambda-settingup.html)  | 
| PowerShell |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/lambda/latest/dg/lambda-settingup.html) | 
