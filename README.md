# IAM Role & Policy Management#

 Introduction:

AWS Identity and Access Management(IAM) allows securec control over AWS resources by defining permissions using IAM roles and policies.This project focuses on creating IAM users,roles and policies to enforce least-privilege access,ensuring security and compliance.

# Steps to Implement IAM Role & Policy Management

 Step 1:Create an IAM User
 1. Login to AWS Console-->Go to IAM.
 2. Click Users--->Add User.
 3. Enter a Username and enable Programmatic Access(for CLI/API)
 4. Click Next:Permissions and Attach existing policies directly.
 5. Choose Administrator Access(or create a custom policy)
 6. Click Next-->Review-->Create User.
 7. Download the Access Key ID and Secret Access Key.

Step 2:Create a custom IAM Policy
1. In the IAM Console,navigate to Policies-->Create Policy

Select JSON and define a custom policy(ex:S3 Read-Only Access):
json

{
"Version":
"Statement":[
{
"Effect":"Allow",
"Action":"s3:ListBucket",
"Resource":
},
{
"Effect":"Allow",
"Action":"s3:GetObject",
