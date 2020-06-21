# ref-bigdata-aws
Big Data Analytics with AWS Glue and Athena

## Pre-requisites
Serverless Analytics can only work on the below regions at the moment
1) Ohio (us-east-2)
2) Oregon (us-west-2)

## Dev environment
### AWS CloudFormation
1) AWS Console -> check the region (e.g. Ohio) -> CloudFormation
2) Create Stack -> create template in designer -> YAML on the Template tab -> Open on the 'File' menu on the top-left corner -> local file -> select the xxx.yml template for your design -> Validate Template (check box on the menu) -> Back to Create Stack (e.g. cloud icon on the menu) -> s2 url selected automatically -> Next
3) Put Stack Name -> My IP address (put the public ip address - e.g. WAN IP) with the post-fix '/32' -> default username/password (auradmin / auradmin123) -> next -> create stack (finish) 
4) the stack should be on the status : Create_complete

e.g. 
AuroraClusterEndPoint (outputs on the stack) : ref-aurora-stack-auroracluster-1hgvnca4aayge.cluster-c90s2gyc1jpa.us-east-2.rds.amazonaws.com
AuroraDBUsername : auradmin
AuroraDBPassword : auradmin123

5) Check the RDS data created by CloudFormation
  rds -> database -> find out the aurora DB named with CloudFormation stack name

6) check the S3 bucket created by CloudFormation
  s3 -> cf driven formation like cf-templateds-xxx 
