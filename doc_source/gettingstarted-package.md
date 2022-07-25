# Lambda deployment packages<a name="gettingstarted-package"></a>

Lambda supports two types of deployment packages: container images and \.zip file archives\.

**Topics**
+ [Container images](#gettingstarted-package-images)
+ [\.zip file archives](#gettingstarted-package-zip)
+ [Layers](#gettingstarted-package-layers)
+ [Using other AWS services to build a deployment package](#gettingstarted-package-awsother)

## Container images<a name="gettingstarted-package-images"></a>

For more information about Lambda container images, see [Using container images with Lambda](lambda-images.md)\.

## \.zip file archives<a name="gettingstarted-package-zip"></a>

A \.zip file archive includes your application code and its dependencies\. 

You can upload a \.zip file as your deployment package using the Lambda console, AWS Command Line Interface \(AWS CLI\), or to an Amazon Simple Storage Service \(Amazon S3\) bucket\.


### Using the AWS CLI<a name="gettingstarted-package-zip-cli"></a>

You can upload a \.zip file as your deployment package using the AWS Command Line Interface \(AWS CLI\)\. For language\-specific instructions, see the following topics\.

------
#### [ Node\.js ]

[Deploy Node\.js Lambda functions with \.zip file archives](nodejs-package.md) 

------
#### [ Python ]

 [Deploy Python Lambda functions with \.zip file archives](python-package.md) 

------
#### [ Java ]

 [Deploy Java Lambda functions with \.zip or JAR file archives](java-package.md) 

------

### Using Amazon S3<a name="gettingstarted-package-zip-cli"></a>

You can upload a \.zip file as your deployment package using Amazon Simple Storage Service \(Amazon S3\)\. For more information, see [Using other AWS services to build a deployment package](#gettingstarted-package-awsother)\.

## Layers<a name="gettingstarted-package-layers"></a>

If you deploy your function code using a \.zip file archive, you can use Lambda layers as a distribution mechanism for libraries, custom runtimes, and other function dependencies\. Layers enable you to manage your in\-development function code independently from the unchanging code and resources that it uses\. You can configure your function to use layers that you create, layers that AWS provides, or layers from other AWS customers\.

You do not use layers with container images\. Instead, you package your preferred runtime, libraries, and other dependencies into the container image when you build the image\.

For more information about layers, see [Creating and sharing Lambda layers](configuration-layers.md)\.

## Using other AWS services to build a deployment package<a name="gettingstarted-package-awsother"></a>

The following section describes other AWS services you can use to package dependencies for your Lambda function\.


### Deployment packages over 50 MB<a name="gettingstarted-package-s3"></a>

If your deployment package is larger than 50 MB, we recommend uploading your function code and dependencies to an Amazon S3 bucket\.

