
# Cloud Formation Static Site

This repository contains CloudFormation templates for hosting a static site, setting up monitoring, and deploying shared features for static site stacks.

It enables having the static site code managed in Github. Whenever a commit & push is done into that repository, it's gonna be detected by CodeCommit pipeline and distributed to relevant S3 bucket and CloudFront distribution.

## Templates

### 1. `Main.yml`

This template is for hosting a static site. It sets up the following:
- Connection to an existing GitHub repository.
- Pipeline for deploying repository content into an S3 bucket.
- CloudFront distribution creation from the S3 content.

**Prerequisites**:
- Certificate in AWS Certificate Manager (us-east-1 region) if required.
- GitHub connection in AWS CodeCommit.

### 2. `Monitoring.yml`

This template creates resources for monitoring a specific project or website. It includes:
- Creation of SNS topic and subscription.
- Setup of CloudWatch alarms and Lambda functions for monitoring up to 5 URLs.

### 3. `SharedFeatures.yml`

This template deploys shared features for static site stacks such as:
- Lambda for CloudFront distribution invalidation.
- Lambda for S3 bucket cleanup.

## Deployment

To deploy these templates:
1. Navigate to the AWS CloudFormation console.
2. Create a new stack for each template.
3. Provide the necessary parameters as prompted.
4. Review and create the stack.

## Usage

After deployment, the static site will be hosted on AWS with the specified configurations. The monitoring setup will alert you via email notifications based on the CloudWatch alarms. The shared features support the overall functionality of the static site and its maintenance.
