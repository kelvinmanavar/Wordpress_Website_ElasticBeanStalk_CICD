# Wordpress_Website_ElasticBeanStalk_CICD

Step1: Create ElasticBeanStalk Environment

# Configure environment

1. select Web server environment
2. Enter Application name
3. Enter Application name | Optional if you will not give name then it will automatically generate name.
4. Select Platform as per your requirement like our requirement is PHP.
5. Select sample application code.
6. Select preset as Single instance (free tier eligible).

# Configure service access

1. select Create and use new service role.
2. Select EC2 key pair for access your ec2 instance if you don't have then create it from console.
3. Create EC2 instance profile Role with below permissions:
   AmazonEC2RoleforAWSCodeDeploy | AWSCodeDeployFullAccess | AWSCodePipeline_FullAccess.

# Virtual Private Cloud (VPC)

1. Select VPC
2. Public IP address enable
3. select subnets

# Configure instance traffic and scaling - optional

1. Root volume type [General purpose SSD]
2. Auto scaling group: Single Instance or as per requirement
3. Fleet: On demand
4. Architecture: x86_64
5. Instance types: t2.micro [as per requirement]

# Configure updates, monitoring, and logging - optional

1. Health reporting: Enhanced
2. Application deployments: All at once

# Platform software

1. Container options
   Proxy server: Nginx
2. Document root: /wordpress

# Review and Create.

Step2: Deploy your code to your Github Repository.

Step3: AWS code pipeline setup:

1. Create pipeline
   Give Pipeline name
   New service Role select
2. Add source stage: Github version 2
3. Setup connection with github
   select Repository name
   select Branch name
   Output artifact format: CodePipeline default
   4 Skip Build Stage
4. Add deploy stage: AWS elastic beanstalk select
   select Application name
   select Environment name

# review and Create.

Step4: Create RDS database in same VPC

1. Make sure that you have given name of database, username, password.
2. We require username, password, database name, host name [RDS Endpoint]

# Setup RDS connection with website:

1. Go to your repository and go inside wordpress folder.
2. Edit wp-config-sample.php file with username, password, database name, host name.
3. Push code into git repository.
4. When you push code your pipeline will run automatically.

Step5: Go to Elastic Beanstalk environment and clik on domain.
Now setup your website.

===============================Thank You===============================
