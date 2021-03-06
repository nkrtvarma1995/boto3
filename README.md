# boto3
Following is the boto3 learning space and book keeping!

FROM  :   https://boto3.amazonaws.com/v1/documentation/api/latest/index.html

* boto3 is the name of the python module and very helpful now as the python SDK for aws!
* Open service
* it allows you to directy create, modify or delete the AWS resources from your Python scripts!

->  it's complicated in many ways but rich SDK for AWS

->  Boto3 is written on top of "botocore" which is a low level SDK for AWS - API.

-> Compare to botocore,  BOTO3 has a lot of useful methods to automate the AWS services.

*****  BOTOCORE is the basis for the AWS CLI which is also written in PYTHON

****************************************************************************************

INSTALL THE BOTO3 FOR YOUR SYSTEM!  In windows generally, by default BOTO3 will be installed by default when you install the Python

pip install boto3

With boto3 following collected packages will also be installed!

Installing collected packages: jmespath, urllib3, six, python-dateutil, botocore, s3transfer, boto3
Successfully installed boto3-1.16.30 botocore-1.19.30 jmespath-0.10.0 python-dateutil-2.8.1 s3transfer-0.3.3 six-1.15.0 urllib3-1.26.2

******************************************************************************************

CREDENTIALS MANAGEMENT:
----------------------

-> Directly with the service we can provide the AWS credentials during the resource object creation!

-> With above method the CREDENTIALS set will be exposed over the INTERNET during the public REPO's (if opted)

-> So, we can install awscli and configure the credentials which create the credentials file under "${HOME}/.aws/credentials" -  BOTO3 will pickup the credentials from here directly!

******************************************************************************************

CORE CONCEPTS OF BOTO3:
----------------------

 resource				: high level object to access AWS services ( Creating objects / dot operations )
 
 client                 : low-level object to access AWS services ( Any manipulations to the existing object / dictonary operations )
 
 meta     		     	: helps to enter into client object from resource object
 
 session                : object to connect with particular AWS account or IAM user account and initiate a SESSION.
 
 collections            : a tool to iterate and manipulate groups of object resources ( example of "buckets" in s3 resource )
 
 paginators             : automatic paging of responses ( to gatherer the complete info with API calls )
 
 waiters                : a way to block until a certain state has been reached.
 
 
 ******************************************************************************************
 
 Two important steps to write python boto3 scripts for AWS Automation or Provisioning
 ------------------------------------------------------------------------------------
 
 STEP1 :  Create a Session Object   // It represents the authentication before hand to start your aws session and access resources.
 
 STEP2 :  Create a Resource Object or Client object.
 
 
 ******************************************************************************************
 
 CRETION OF A BOTO3 SESSION OBJECT 
 ---------------------------------
 
 * Session stores configaration information (primarily credentials of AWS root account or AWS IAM Useraccount and selected region )
 * allows you to create resources and client objects thereby!
 
 -> With Session Method 
 -> Without Session Method
 
 eg:  ( with session method )
 --
 import boto3
 session_obj = boto3.Session(aws_access_key_id=ACCESS_KEY, aws_secret_access_key=SECRET_KEY, region_name=REGION_NAME)
 #creating a resource
 ec2_obj=session_obj.resource('ec2')
 for instance in ec2_obj.instances.all():
     print(instance)

NEVER HOT CODE CREDENTIALS IN THE SCRIPT. 

session_obj=boto3.Session(profile_name="default")

**********************************************************************************************

MANAGING AWS CREDENTIALS FOR DIFFERENT USERS:
--------------------------------------------

* with the help of profile name we can store multiple users credentials as below

aws configure --profile aws-root

aws configure --profile iam-user-s3

**********************************************************************************************

EXTENDING OUR UNDERSTANDING OF BOTO3  VS   AWS Console
------------------------------------------------------

Browser  -->  Boto3   #import boto3

Login to management Console  -->  Session Object  #  sess_obj = boto3.Session(profile_name="default"

Select a resource from management console  -->  resource object # res_obj=sess_obj.resource('ec2')  

Now we can apply different methods over resource object ( like listing instances, creating new, deleting and so on....)

************************************************************************************************

BOTO3  Services Catalog:
-----------------------

Not every service will have the "resource" service but the "client" service will definitely be [present] acrosss all AWS services.

BOTO3 document for displaying the Service Catalog :  

https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/index.html

************************************************************************************************


 
 
 
 
 
 
 

 
 
 


