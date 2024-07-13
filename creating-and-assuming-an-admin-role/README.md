# Introduction
In this lab, I am going to create a brand-new IAM Role within your AWS Sandbox account. This IAM Role will be granted Administrator Access permissions within the same account.

## Challenge Objectives
1. Create IAM Role
   * Create a brand-new IAM role named CSAA_AdministratorTest and attach the AWS-managed policy titled `AdministratorAccess`.
   * Copy the [IAM Trust Policy](https://github.com/vineeth-pradhan/aws-workshop/blob/main/creating-and-assuming-an-admin-role/policies/policy.json) from policies/policy.json repo and update `%REPLACE_WITH_ACCOUNT_ID%` with your account ID. This policy will only allow an IAM identity with your user account's ARN to assume the role
   *  The naming convention for this step is critical to avoid conflicts in future steps!

1. Assume the IAM Role
    * After creation, test assumption of the IAM role using the Switch Role console option.

1. Create & Deploy CloudFormation Template of IAM Role
    * After the role is verified to be working, create a new CloudFormation template that mimics the newly created IAM role. This allows for easy future deployment when required.
    * To do this, copy and run the template code for which ever language you choose in Application Composer.
    * [JSON Template Code](https://github.com/vineeth-pradhan/aws-workshop/blob/main/creating-and-assuming-an-admin-role/cf-templates/template.json)

1. When prompted, name the stack `AdministratorAccessRole`
