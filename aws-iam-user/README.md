# AWS CLI – IAM User Creation, Policy Management and Programmatic Access

## Project Overview

This project demonstrates hands-on experience managing AWS Identity and Access Management (IAM) users, permissions, and programmatic authentication using the AWS Command Line Interface (CLI) and Windows PowerShell.

The objective was to create an IAM user, assign an AWS-managed read-only policy, configure dedicated CLI credentials, and validate access to Amazon S3 while applying the principle of least privilege.

## Technologies Used

- Amazon Web Services (AWS)
- AWS Identity and Access Management (IAM)
- AWS Command Line Interface (CLI)
- AWS Security Token Service (STS)
- Amazon S3
- Windows PowerShell
- Git and GitHub

## Project Objectives

1. Authenticate to AWS using the AWS CLI.
2. Create and verify an IAM user.
3. Attach an AWS-managed IAM policy.
4. Verify the policy attachment.
5. Configure programmatic access using a dedicated AWS CLI profile.
6. Validate authentication with AWS STS.
7. Test Amazon S3 read-only access.
8. Apply least-privilege and credential security practices.

## Project Implementation

### Step 1: Verify AWS CLI Authentication

Verified initial AWS CLI authentication using AWS Security Token Service (STS).

```powershell
aws sts get-caller-identity
```

This command identifies the AWS account and IAM principal associated with the default CLI credentials.

### Step 2: Create an IAM User

Created an IAM user named `cloud-engineer-lab` using AWS CLI.

```powershell
aws iam create-user --user-name cloud-engineer-lab
```

IAM users do not automatically receive permissions when created.

### Step 3: Verify IAM User Creation

Listed IAM users and retrieved the new user's details.

```powershell
aws iam list-users
aws iam get-user --user-name cloud-engineer-lab
```

These commands confirm that the IAM user exists in the AWS account.

### Step 4: Attach an IAM Policy

Attached the AWS-managed `AmazonS3ReadOnlyAccess` policy to the IAM user.

```powershell
aws iam attach-user-policy --user-name cloud-engineer-lab --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```

This policy provides read-only access to supported Amazon S3 resources and operations, without granting S3 write or delete permissions.

### Step 5: Verify IAM Policy Attachment

Verified the attached AWS-managed policy.

```powershell
aws iam list-attached-user-policies --user-name cloud-engineer-lab
```

**Verified output:**

```json
{
  "AttachedPolicies": [
    {
      "PolicyName": "AmazonS3ReadOnlyAccess",
      "PolicyArn": "arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess"
    }
  ]
}
```

This confirms the policy attachment. Effective permissions are separately tested using the IAM user's credentials.

### Step 6: Configure IAM Programmatic Access

Created a new access key for the `cloud-engineer-lab` user through the AWS Management Console.

Configured a dedicated AWS CLI profile using Windows PowerShell.

```powershell
aws configure --profile cloud-engineer-lab
```

**Configuration:**

- AWS CLI profile: `cloud-engineer-lab`
- Default region: `us-east-2`
- Default output format: `json`
- Authentication: IAM access key credentials

Credentials were stored locally in the AWS CLI credentials file and excluded from the GitHub repository.

### Step 7: Verify Programmatic Authentication

Used AWS Security Token Service to validate the IAM user's credentials.

```powershell
aws sts get-caller-identity --profile cloud-engineer-lab
```

**Verification result:**

Successfully authenticated as:

```text
arn:aws:iam::909392366817:user/cloud-engineer-lab
```

This confirmed that the IAM user's access credentials were valid and that the dedicated AWS CLI profile was configured correctly.

### Step 8: Verify Amazon S3 Read-Only Access

Tested S3 bucket listing using the dedicated IAM user profile.

```powershell
aws s3 ls --profile cloud-engineer-lab
```

**Verified output:**

```text
2026-11-12 11:59:47 otega-cloud-lab-2026
```

Successfully listed an existing S3 bucket using the IAM user's credentials.

This demonstrates that programmatic authentication and the tested S3 listing permission were functioning correctly.

## Security Best Practices

This project reinforced the following IAM security principles:

- **Least Privilege:** Assigned `AmazonS3ReadOnlyAccess` rather than administrator permissions.
- **Identity Management:** Created a dedicated IAM user for the lab.
- **Access Control:** Used an AWS-managed IAM policy to define permitted actions.
- **Credential Security:** Kept access keys and secret access keys out of GitHub.
- **Profile Separation:** Used a named CLI profile to separate lab credentials from administrator credentials.
- **Permission Verification:** Validated authentication and S3 access with AWS CLI commands.
- **Credential Lifecycle:** Replaced invalid access keys and verified the new credentials.
- **Temporary Credentials:** Recognized that IAM roles and short-lived credentials are preferred for production environments.

## Resource Cleanup

After completing the lab, remove unused credentials and IAM resources to reduce security risk.

### 1. List Existing Access Keys

```powershell
aws iam list-access-keys --user-name cloud-engineer-lab
```

### 2. Delete Access Keys

After identifying the key to remove, run:

```powershell
aws iam delete-access-key --user-name cloud-engineer-lab --access-key-id YOUR_ACCESS_KEY_ID
```

### 3. Detach the IAM Policy

```powershell
aws iam detach-user-policy --user-name cloud-engineer-lab --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```

### 4. Delete the IAM User

```powershell
aws iam delete-user --user-name cloud-engineer-lab
```

These are optional cleanup instructions. Perform them only when the lab resources are no longer required. Other attached resources or credentials may also need removal before IAM user deletion.

## Key Learning Outcomes

Through this project, I developed and validated practical skills in:

- AWS IAM user lifecycle management
- AWS CLI-based identity administration
- IAM policy attachment and verification
- AWS CLI named profile configuration
- Programmatic authentication using AWS STS
- Amazon S3 read-only permission validation
- Access key lifecycle management
- Least-privilege cloud security practices
- Secure cloud credential handling

## Conclusion

This project demonstrates hands-on implementation of AWS IAM identity management, policy-based authorization, and programmatic access using AWS CLI and Windows PowerShell.

By creating a dedicated IAM user, attaching the `AmazonS3ReadOnlyAccess` policy, configuring a named CLI profile, and validating S3 bucket listing, I successfully demonstrated foundational AWS cloud identity and access security capabilities.

These skills are relevant to Cloud Security Engineering, Identity and Access Management (IAM), Cloud Engineering, and DevSecOps.

---

**Project Category:** Cloud Security | AWS IAM | Identity and Access Management | AWS CLI

**Learning Program:** Soleyman Cloud Engineering Academy

**Project Status:** Completed and Verified