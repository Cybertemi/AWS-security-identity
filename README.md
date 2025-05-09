🛡️ AWS Security & Identity Mini Project

✅ Overview
This project demonstrates key Identity and Access Managements (IAM) tasks in AWS, focusing on best practices around user permissions, MFA setup, and role-based access using custom policies.

🔐 Step 1: Create IAM User with Restricted Permissions
Created a new IAM user named "Angel"

Attached the AmazonS3ReadOnlyAccess managed policy

Verified the user cannot perform write or admin actions on S3 or other services


🔑 Step 2: Set Up Multi-Factor Authentication (MFA)
Enabled MFA for the limited-user account

Used the Google Authenticator app to scan the QR code

Successfully tested sign-in with MFA enabled


🎯 Step 3: Create and Attach Custom Policy to IAM Role
Created a new IAM role named ec2-read-only 

Defined and attached a custom policy allowing:

AmazonEC2ReadOnlyAccess

Verified that the role cannot start/stop EC2 instances


📄 Custom IAM Policy attached to IAM role
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:Describe*",
                "ec2:GetSecurityGroupsForVpc"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": "elasticloadbalancing:Describe*",
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "cloudwatch:ListMetrics",
                "cloudwatch:GetMetricStatistics",
                "cloudwatch:Describe*"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": "autoscaling:Describe*",
            "Resource": "*"
        }
    ]
}

🎓 Lessons Learned
Importance of least privilege access in IAM

How MFA enhances account security

Flexibility of custom IAM policies and roles