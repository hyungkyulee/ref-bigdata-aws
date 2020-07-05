# ref-bigdata-aws
Big Data Analytics with AWS Glue and Athena

## Pre-requisites
Serverless Analytics can only work on the below regions at the moment
1) Ohio (us-east-2)
2) Oregon (us-west-2)

## Dev environment
### AWS CloudFormation for RDS Aurora DB
1) AWS Console -> check the region (e.g. Ohio) -> CloudFormation
2) Create Stack -> create template in designer -> YAML on the Template tab -> Open on the 'File' menu on the top-left corner -> local file -> select the xxx.yml template for your design -> Validate Template (check box on the menu) -> Back to Create Stack (e.g. cloud icon on the menu) -> s2 url selected automatically -> Next
3) Put Stack Name -> My IP address (put the public ip address - e.g. WAN IP) with the post-fix '/32' -> default username/password (auradmin / auradmin123) -> next -> create stack (finish) 
4) the stack should be on the status : Create_complete

   - [example] 
   - AuroraClusterEndPoint (outputs on the stack) : ref-aurora-stack-auroracluster-1hgvnca4aayge.cluster-c90s2gyc1jpa.us-east-2.rds.amazonaws.com
   - AuroraDBUsername : a***d***
   - AuroraDBPassword : *ur****n*2*

5) Check the relations created by CloudFormation
   - database : rds -> database -> find out the aurora DB named with CloudFormation stack name
   - storage : s3 -> cf driven formation like cf-templateds-xxx 
   - security group : EC2 -> security groups
   - Network IF : EC2 -> Network & Security -> network interfaces
   - VPC : VPC -> your VPCs -> check the overview

### AWS CloudFormation for Glue
1) Service -> CloudFormation -> Stacks -> Create stack -> choose 'Template is ready' -> select 'upload a template file' -> upload the 'GlueStack.yml'
2) Specify Details of Stack
   - Stack Name : ref-glue-stack
   - AuroraStackName : ref-aurora-stack
     (* Please enter the name of the CloudFormation stack that was used to deploy the RDS Aurora MySQL resource.)
   - DatabasePath : sakila/%
     (* Schema Path for crawling the database and table schemas. DBname/% for crawling all the tables in the DB)
   - S2DestinationBucketName : uniquebucketnamedestination

3) Option : leave everything as it is.
4) Review : check the disclaimer 'I acknowledge that AWS CloudFormation might create IAM resources.'
   (* if you didn't check this box, we have to create our own IAM role and spend a lot of time to set this)
