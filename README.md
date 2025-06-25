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


provider "aws" {
region = "us-east-1"
}

resource "aws_iam_user" "sai_user" {
  name = "sai_user"
}

resource "aws_iam_group" "sai_group" {
  name = "sai_group"
}

resource "aws_iam_policy" "policy_for_iamuser" {
  name = "DevS3ReadOnlyAccess"
  description = "Read-only access to S3"
  policy = jsonencode({
    Version = "2012-10-17"
    Statement = [{
        Action = ["s3:Get*","s3:List*"],
        Effect = "Allow",
        Resource = "*"
    }]
  })
}

resource "aws_iam_policy_attachment" "user_policy" {
    name = "attach-user-policy"
    users = [aws_iam_user.sai_user]
    policy_arn = aws_iam_policy.policy_for_iamuser.arn
  
}
