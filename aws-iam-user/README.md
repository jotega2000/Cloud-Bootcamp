\# AWS CLI – IAM User Creation and Policy Management



\## Project Overview



This project demonstrates how to manage AWS Identity and Access Management (IAM) users and permissions using the AWS Command Line Interface (CLI).



The objective is to create an IAM user, assign an AWS-managed policy, and verify the user's permissions while applying the principle of least privilege.



\## Technologies Used



\- Amazon Web Services (AWS)

\- AWS Identity and Access Management (IAM)

\- AWS CLI

\- Windows PowerShell

\- Amazon S3

\- Git and GitHub



\## Project Objectives



1\. Authenticate to AWS using the AWS CLI.

2\. Create a new IAM user.

3\. Verify successful user creation.

4\. Attach an AWS-managed IAM policy.

5\. Verify the assigned permissions.

6\. Understand IAM access control and least-privilege security.



\## Project Implementation



\### Step 1: Verify AWS CLI Authentication



Verified AWS CLI authentication using AWS Security Token Service (STS).



```bash

aws sts get-caller-identity

```



This command retrieves the AWS account ID and the identity associated with the current CLI credentials.



\### Step 2: Create an IAM User



Created an IAM user named `cloud-engineer-lab` using the AWS CLI.



```bash

aws iam create-user --user-name cloud-engineer-lab

```



This command creates an IAM identity without automatically assigning permissions.



\### Step 3: Verify IAM User Creation



Listed IAM users to confirm successful creation.



```bash

aws iam list-users

```



Verified the specific IAM user:



```bash

aws iam get-user --user-name cloud-engineer-lab

```



\### Step 4: Attach an IAM Policy



Attached the AWS-managed `AmazonS3ReadOnlyAccess` policy to the IAM user.



```bash

aws iam attach-user-policy --user-name cloud-engineer-lab --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess

```



This policy grants read-only access to Amazon S3 resources.



The policy allows supported S3 read and listing operations without granting write or delete permissions.



\### Step 5: Verify IAM Policy Attachment



Verified the attached policy using:



```bash

aws iam list-attached-user-policies --user-name cloud-engineer-lab

```



Expected output:



```json

{

&#x20; "AttachedPolicies": \[

&#x20;   {

&#x20;     "PolicyName": "AmazonS3ReadOnlyAccess",

&#x20;     "PolicyArn": "arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess"

&#x20;   }

&#x20; ]

}

```



This confirms the managed policy is attached to the IAM user. It does not independently test the user's effective permissions.



\## Security Best Practices



This project reinforces several important IAM security principles:



\- \*\*Least Privilege:\*\* Grant only the permissions required to perform authorized tasks.

\- \*\*Identity Management:\*\* Create and manage individual IAM identities.

\- \*\*Access Control:\*\* Use IAM policies to define permissions.

\- \*\*Permission Verification:\*\* Validate policy attachments using AWS CLI commands.

\- \*\*Credential Security:\*\* Avoid exposing access keys or secrets in source control.

\- \*\*Resource Cleanup:\*\* Remove unused IAM users and credentials after completing lab exercises.



\## Optional: Programmatic Access



IAM access keys can be created when programmatic access is specifically required.



```bash

aws iam create-access-key --user-name cloud-engineer-lab

```



Long-term access keys should be avoided where temporary credentials or IAM roles can be used instead.



\*\*Security Note:\*\* Never commit AWS access keys, secret access keys, or sensitive authentication information to GitHub.



\## Resource Cleanup



Detach the IAM policy:



```bash

aws iam detach-user-policy --user-name cloud-engineer-lab --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess

```



Delete the IAM user:



```bash

aws iam delete-user --user-name cloud-engineer-lab

```



Any access keys or other IAM resources associated with the user must be removed before deletion.



\## Key Learning Outcomes



Through this project, I developed practical understanding of:



\- AWS IAM user lifecycle management

\- AWS CLI-based identity administration

\- IAM policy attachment and verification

\- Amazon S3 access permissions

\- Least-privilege access control

\- Cloud identity security best practices



\## Conclusion



This project provides foundational hands-on experience with AWS Identity and Access Management through command-line administration.



The exercise demonstrates how IAM users and policies work together to control access to AWS resources.



These skills are relevant to Cloud Security Engineering, Identity and Access Management (IAM), and DevSecOps.



\---



\*\*Project Category:\*\* Cloud Security | AWS IAM | Identity and Access Management



\*\*Learning Program:\*\* Soleyman Cloud Engineering Academy

