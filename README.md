
---

# AWS IAM Cloud Security Project

## Project Overview

This project focuses on **AWS Identity and Access Management (IAM)**, enabling secure management of resources within an AWS environment. 

### What is AWS IAM?

AWS IAM allows you to manage access levels for users and services interacting with your AWS resources. This project highlights IAM's practical applications, such as:

- Managing permissions with JSON-based IAM policies.
- Organizing resources with tags for effective management.
- Testing user access through IAM user roles and groups.

---

## Key Features

### 1. **JSON IAM Policies**

- Created and tested custom IAM policies.
- Allowed specific actions like starting, stopping, and describing EC2 instances tagged as "development."
- Denied actions like creating or deleting tags for any EC2 instance.

Example Policy:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ec2:StartInstances",
        "ec2:StopInstances",
        "ec2:DescribeInstances"
      ],
      "Resource": "arn:aws:ec2:region:account-id:instance/*",
      "Condition": {
        "StringEquals": {
          "ec2:ResourceTag/Env": "development"
        }
      }
    },
    {
      "Effect": "Deny",
      "Action": "ec2:CreateTags",
      "Resource": "arn:aws:ec2:region:account-id:instance/*"
    }
  ]
}
```

### 2. **Tags for Resource Management**

- Implemented tags like `Env` with values `production` and `development` for easy differentiation of environments.
- Utilized tags to streamline cost management and automate policies.

### 3. **IAM Users and Groups**

- Configured IAM users and user groups for streamlined permission management.
- Attached policies to user groups, ensuring consistency and ease of access management.

### 4. **Testing Policies**

- Successfully tested policies by simulating user actions:
  - Stopping a **development** instance succeeded as per the policy.
  - Stopping a **production** instance resulted in an "Access Denied" error.

### 5. **Account Alias**

- Created an account alias for simplified AWS Management Console login URLs.

---

## Lessons Learned

- **Value of Tags**: Tags are not just for organization but also help manage costs and automate workflows effectively.
- **IAM Policy Testing**: Testing is critical to ensuring policies function as intended, avoiding unintended permissions or restrictions.

---

## Resources


- **AWS IAM Documentation**: [Learn about AWS IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/).

