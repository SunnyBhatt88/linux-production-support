# AWS Troubleshooting

## Overview

This document contains basic AWS troubleshooting steps commonly used in Application and Production Support environments.

The examples cover EC2, S3, IAM, VPC, CloudWatch, RDS, and basic AWS connectivity checks.

## Step 1: Check EC2 Instance Status

Check whether the EC2 instance is running and verify its health status.

Key checks:

* Instance state
* System status checks
* Instance status checks
* CPU utilization
* Network activity
* Disk utilization

Example AWS CLI command:

```bash
aws ec2 describe-instance-status --instance-ids <instance-id>
```

## Step 2: Check EC2 CPU Utilization

High CPU utilization can affect application performance.

Check CPU utilization using Amazon CloudWatch or the AWS Management Console.

Important metrics include:

* CPUUtilization
* NetworkIn
* NetworkOut
* DiskReadOps
* DiskWriteOps

## Step 3: Check Disk Space on EC2

Connect to the Linux EC2 instance and check disk utilization:

```bash
df -h
```

Identify directories consuming significant space:

```bash
du -sh /*
```

Review application logs if the disk is filling up:

```bash
du -sh /var/log/*
```

## Step 4: Check Application Logs

Review application logs when an application running on EC2 is experiencing issues.

```bash
tail -100 application.log
```

Search for errors:

```bash
grep -i "error" application.log
```

Search for exceptions:

```bash
grep -i "exception" application.log
```

## Step 5: Check Security Group Configuration

If an application or API is not accessible, verify the EC2 Security Group.

Check:

* Inbound rules
* Outbound rules
* Required ports
* Source IP or security group
* Protocol

Common ports:

| Port | Purpose    |
| ---- | ---------- |
| 22   | SSH        |
| 80   | HTTP       |
| 443  | HTTPS      |
| 3306 | MySQL      |
| 5432 | PostgreSQL |

Do not open unnecessary ports to the public internet.

## Step 6: Check IAM Permissions

If an AWS service or application receives an `AccessDenied` error, verify IAM permissions.

Check:

* IAM user or role
* Attached policies
* Resource permissions
* AWS account
* Active credentials
* Service-specific permissions

Example:

```bash
aws sts get-caller-identity
```

This command helps identify the AWS identity being used.

## Step 7: Check S3 Access

For S3-related issues, verify:

* Bucket name
* Object key
* IAM permissions
* Bucket policy
* Region
* Encryption configuration

Example:

```bash
aws s3 ls s3://<bucket-name>
```

Do not publish real bucket names, credentials, or customer data in GitHub.

## Step 8: Check CloudWatch Monitoring

CloudWatch can be used to monitor AWS resources and applications.

Useful metrics include:

* CPU utilization
* Network traffic
* Application metrics
* Error counts
* Response time
* Alarm status

Review CloudWatch alarms when investigating production incidents.

## Step 9: Check RDS Connectivity

If an application cannot connect to an RDS database, check:

* RDS instance status
* Database endpoint
* Database port
* Security Group
* Network connectivity
* Subnet configuration
* Application database configuration

For MySQL, the default port is:

```text
3306
```

For PostgreSQL:

```text
5432
```

Never store database usernames, passwords, or connection strings containing credentials in GitHub.

## Step 10: Check VPC and Network Configuration

For connectivity issues, review:

* VPC
* Subnet
* Route table
* Internet Gateway
* NAT Gateway
* Security Group
* Network ACL
* DNS configuration

Verify that the required network path exists between the application and the target service.

## Step 11: AWS CLI Basic Checks

Check the configured AWS identity:

```bash
aws sts get-caller-identity
```

Check the AWS CLI version:

```bash
aws --version
```

List S3 buckets:

```bash
aws s3 ls
```

Describe EC2 instances:

```bash
aws ec2 describe-instances
```

## Step 12: Troubleshooting Approach

1. Understand the reported application or infrastructure issue.
2. Identify the affected AWS resource.
3. Check the resource status.
4. Review CloudWatch metrics and alarms.
5. Check application and system logs.
6. Verify IAM permissions.
7. Check Security Groups and network configuration.
8. Check the relevant AWS service configuration.
9. Identify the probable root cause.
10. Take approved corrective action.
11. Monitor the application or AWS resource after resolution.
12. Document the incident and resolution.

## Resolution

After corrective action, verify that the AWS resource and application are functioning normally.

Monitor:

* Application availability
* CPU utilization
* Error rates
* Network connectivity
* CloudWatch alarms
* Application logs

## Production Support Best Practices

* Follow the organization's change and incident-management process.
* Never expose AWS access keys or secret keys.
* Do not publish passwords or credentials.
* Do not publish real customer or production data.
* Avoid making unauthorized production changes.
* Use least-privilege IAM permissions.
* Monitor AWS resources using CloudWatch.
* Document the root cause and resolution.

## AWS Services Covered

* Amazon EC2
* Amazon S3
* AWS IAM
* Amazon VPC
* Amazon CloudWatch
* Amazon RDS
* AWS CLI

## Skills Demonstrated

* AWS Infrastructure Troubleshooting
* EC2 Support
* IAM Troubleshooting
* S3 Troubleshooting
* VPC and Network Troubleshooting
* CloudWatch Monitoring
* RDS Connectivity Troubleshooting
* Production Support
* Incident Management
* Root Cause Analysis
