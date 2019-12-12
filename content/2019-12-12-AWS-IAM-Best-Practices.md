---
date: 2019-12-12
title: "AWS IAM (Identity Access Management) Best Practices"
cover: "https://unsplash.it/400/300/?random?BoldMage"
categories: 
    - AWS
    - Security
tags:
    - programming
    - stuff
    - other
---

I have recently been reviewing AWS IAM best practices, I absolutely recommend you take a look at these to ensure that you understand both the concepts of how Amazon use IAM to secure its resources and how to make your tenancy as secure as possible.

These best practices could be used for your AWS instance, or even many of the best practices could be used across multiple cloud providers.

[Lock Away Your AWS Account Root User Access Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#lock-away-credentials)


Ensure that you don’t have programmatic access set up with your Root account, unless you absolutely need to. If you absolutely need to make sure that you rotate it regularly to decrease the impact of compromise.

Never share any access to your Root account, make sure that you create individual IAM Users.

Create Individual IAM Users
You can give each user to your tenancy their own IAM account. You can use this to give accounts specific access or permissions.

Use Groups to Assign Permissions to IAM Users
Instead of defining permissions for individual users, it’s easier to set up groups that map to job functions. This makes it much easier to manage – think AD security groups.

The flow would look like this:

Create group that relates to a job function i.e Developer
Define the relevant permissions for that group i.e can spin up EC2 instances
Assign IAM users to the group
Grant Least Privilege
It’s best to follow the security policy of granting permissions to only perform the task required. This is much simpler than setting up permissions that are too lenient then trying to tighten them up later.

Get Started Using Permissions with AWS Managed Policies
To simplify you getting set up with permissions for your users, AWS have set up a number of Managed policies that cover common use cases. AWS managed policies for job functions can span multiple services and align with common job functions in the IT industry.

Use Customer Managed Policies Instead of Inline Policies
A recommendation is to user Managed Policies instead of inline policies. An inline policy is one that is assigned to a specific user. An advantage of this is that you can view all of your Managed Policies in once place and attach these policies to users or groups.

If you have an inline policy, there is a simple way you can convert this to a managed policy.

Use Access Levels to Review IAM Permissions
You must regularly review your policies to ensure that they are still relevant and doing what you want them to do. You can manage policies for example to give a subset of users to list and read from S3 buckets. You potentially however would not want these users to have write permissions which would enable them to potentially write to or delete S3 buckets.

Configure a Strong Password Policy for Your Users
You can use IAM to define custom password policies for your users to ensure that a strong password is required and that they are cycled regularly.

Enable MFA for Privileged Users
As covered in a previous post, this should be essential for the root account and any Admin accounts that have ‘root’ access. I’d recommend setting this up as one of the first steps when you create your tenancy or another super user. It’s easy to do and you can download the Google Authenticator app to act as your token for free.

Use Roles for Applications That Run on Amazon EC2 Instances
For applications that run on EC2 instances in a secure way it is recommended to use Roles. Roles have their own set of permissions but it is not classed as a user or group. Roles have their own set of secure credentials that are automatically rotated for you.

Use Roles to Delegate Permissions
Instead of sharing permissions between accounts, you can use IAM Roles.

Do Not Share Access Keys
This is incredibly important, do not share your access keys and do not display them in your apps in plain text.

Rotate Credentials Regularly
Rotate your IAM Account passwords and access keys regularly, if either becomes compromised this will limit how long your accounts become vulnerable. You can set up policies to manage this for you and your users.

Remove Unnecessary Credentials
Remove credentials that are not needed, be explicit about which accounts need console access and those that need programmatic access. This reduces the likelihood of an account becoming compromised.

Use Policy Conditions for Extra Security
To add an extra level of security you can add extra conditions, such as only allow access from specific IP addresses or only access between certain times of the day.

Monitor Activity in Your AWS Account
Use and review logged activities in your AWS account. The log files show the time and date of actions, the source IP for an action, which actions failed due to inadequate permissions, and more.

Video Presentation About IAM Best Practices
This clip, albeit a few years old is very good in explaining the best practices and putting them into context. So well worth a watch.