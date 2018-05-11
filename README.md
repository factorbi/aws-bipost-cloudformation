# Link your AWS Account WIP

Follow these instructions to link your AWS Account and RDS Aurora instance to Bipost API.

**IMPORTANT NOTICE: Many settings suggested here are for testing purposes. If you are to use the following AWS services for production you may want to follow your company policies and understand how to use AWS security according to your needs.**

## Don't have an AWS account?

Not familiar with AWS or just want to skip creating AWS releated services? Write us.

1. Create an AWS account [here](https://portal.aws.amazon.com/billing/signup#/start)

![Screenshot](img/aws-screenshot.png?raw=true "Screenshot")

2. AWS usually makes an automated verification phone call, we suggest to provide a land line.
3. Provide payment information.
4. Select Basic Support (free plan).
5. Check if you can open RDS Dashboard, by searching under AWS services.
6. Congrats you have an AWS account!


## Check closest AWS Region to you location

[cloudping.info](http://cloudping.info/)


Click the above link and hit HTTP Ping and look for the lowest latency.

Maybe you want to try this at different times of the day.

Take note of the closest region.


![Cloudping](img/CloudPing.png?raw=true "Cloudping")



-------

## Get Canonical User ID from your IAM Home

Put Instructions here.

## Create AWS Assets 



You can launch this CloudFormation stack in your account in your closest AWS Region:

| AWS Region | Short name | | 
| -- | -- | -- |
| US East (Ohio) | us-east-2 | [![cloudformation-launch-button](img/launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=us-east-2#/stacks/new?stackName=Production&templateURL=https://s3.amazonaws.com/bipost-cloudformation/Aurora-RDS-bipost.template) |
| US East (N. Virginia) | us-east-1 | [![cloudformation-launch-button](img/launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=Production&templateURL=https://s3.amazonaws.com/bipost-cloudformation/Aurora-RDS-bipost.template) |
| US West (N. California) | us-west-2 | [![cloudformation-launch-button](img/launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=Production&templateURL=https://s3.amazonaws.com/bipost-cloudformation/Aurora-RDS-bipost.template) |
| US West (Oregon) | us-west-1 | [![cloudformation-launch-button](img/launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=us-west-1#/stacks/new?stackName=Production&templateURL=https://s3.amazonaws.com/bipost-cloudformation/Aurora-RDS-bipost.template) |
| Canada (Central) | ca-central-1 | [![cloudformation-launch-button](img/launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=ca-central-1#/stacks/new?stackName=Production&templateURL=https://s3.amazonaws.com/bipost-cloudformation/Aurora-RDS-bipost.template) |
| EU (Paris) | eu-west-3 | [![cloudformation-launch-button](img/launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=eu-west-3#/stacks/new?stackName=Production&templateURL=https://s3.amazonaws.com/bipost-cloudformation/Aurora-RDS-bipost.template) |
| EU (London) | eu-west-2 | [![cloudformation-launch-button](img/launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=eu-west-2#/stacks/new?stackName=Production&templateURL=https://s3.amazonaws.com/bipost-cloudformation/Aurora-RDS-bipost.template) |
| EU (Ireland) | eu-west-1 | [![cloudformation-launch-button](img/launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=Production&templateURL=https://s3.amazonaws.com/bipost-cloudformation/Aurora-RDS-bipost.template) |
| EU (Frankfurt) | eu-central-1 | [![cloudformation-launch-button](img/launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=eu-central-1#/stacks/new?stackName=Production&templateURL=https://s3.amazonaws.com/bipost-cloudformation/Aurora-RDS-bipost.template) |
| Asia Pacific (Seoul) | ap-northeast-2 | [![cloudformation-launch-button](img/launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-2#/stacks/new?stackName=Production&templateURL=https://s3.amazonaws.com/bipost-cloudformation/Aurora-RDS-bipost.template) |
| Asia Pacific (Tokyo) | ap-northeast-1 | [![cloudformation-launch-button](img/launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/new?stackName=Production&templateURL=https://s3.amazonaws.com/bipost-cloudformation/Aurora-RDS-bipost.template) |
| Asia Pacific (Sydney) | ap-southeast-2 | [![cloudformation-launch-button](img/launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/new?stackName=Production&templateURL=https://s3.amazonaws.com/bipost-cloudformation/Aurora-RDS-bipost.template) |
| Asia Pacific (Singapore) | ap-southeast-1 | [![cloudformation-launch-button](img/launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=Production&templateURL=https://s3.amazonaws.com/bipost-cloudformation/Aurora-RDS-bipost.template) |
| Asia Pacific (Mumbai) | ap-south-1 |  [![cloudformation-launch-button](img/launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=ap-south-1#/stacks/new?stackName=Production&templateURL=https://s3.amazonaws.com/bipost-cloudformation/Aurora-RDS-bipost.template) |
| South America (São Paulo) | sa-east-1 |  [![cloudformation-launch-button](img/launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=sa-east-1#/stacks/new?stackName=Production&templateURL=https://s3.amazonaws.com/bipost-cloudformation/Aurora-RDS-bipost.template) |

# Create the Cloudformation Stack

* From AWS Cloudformation Console, Click Next Step on blue button.
* Set a Stack Name example bipostrds.
* For the BucketName Parameter  insert the newly S3 bucket name that we provided over email.
* Insert a secure password, must be at least 8 characters containing letters, numbers and symbols.
* Insert the database Admin Username example: root
* DBInstanceClass: for testing purposes select the smallest available, currently t2.small.
* Environment: set the purpose of the stack.
* Public Subnet CIDR, Public Subnet CIDR,  VPCCIDR : you can customize the subnet address space if multiple environments are needed; otherwise use, the recomended.
* SubnetsAZ: Select two availability zones to create the resources.
* Click Next Step, blue button twice.
* Check "I acknowledge that AWS CloudFormation might create IAM resources" in the bottom of the window.

![Capabilities](img/Capabilities.png?raw=true)

* Click Next Step, blue button and wait for completion. 



# What you will deploy

Use this  to automatically set up the following environment on AWS:

1. A virtual private cloud (VPC) configured across two Availability Zones, with two public subnet provisioned in each Availability Zone
2. An internet gateway to allow access from the internet to the public subnets.*
3. An AWS Identity and Access Management (IAM) user with fine-grained permissions for access to S3 from the Aurora Database.
4. Appropriate security group for database access restricted to only necessary protocol and port.
5. Networking and Route configuration.
6. Database Parameter Group with the needed settings
7. Aurora Database cluster
8. Aurora Database Cluster Parameter Group with the needed settings
9. AWS Aurora Instance.

## License

Copyright (c) 2018 Factor BI

Licensed under MIT [License](LICENSE.md)

