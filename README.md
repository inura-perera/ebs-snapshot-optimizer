# AWS EBS Snapshot Cleaner

## Overview

AWS EBS Snapshot Cleaner is an automated solution designed to help optimize your AWS storage costs by identifying and deleting stale EBS snapshots that are no longer associated with any active EC2 instances. This project leverages AWS Lambda and Boto3 to periodically clean up unnecessary snapshots, ensuring efficient use of your AWS resources.

## Features

- **Automated Snapshot Cleanup:** Utilizes AWS Lambda to automatically find and delete stale EBS snapshots.
- **Active Instance Verification:** Checks each snapshot to ensure it is not associated with any active EC2 instance before deletion.
- **Cost Optimization:** Reduces AWS storage costs by removing unnecessary snapshots.

## Prerequisites

- AWS Account
- AWS Lambda
- IAM role with the necessary permissions
- AWS SDK for Python (Boto3)

## IAM Role Permissions

Ensure the IAM role associated with the Lambda function has the following permissions:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ec2:DescribeSnapshots",
        "ec2:DescribeInstances",
        "ec2:DescribeVolumes",
        "ec2:DeleteSnapshot"
      ],
      "Resource": "*"
    }
  ]
}
```

## Setup and Deployment

### Step 1: Create the IAM Role
1. Go to the IAM console.
2. Create a new role with the above policy.
3. Attach the role to your Lambda function.

### Step 2: Create the Lambda Function
1. Open the AWS Lambda Console.
2. Create a new Lambda function.
3. Choose Python as the runtime.
4. Copy and paste the Lambda function code into the Lambda function editor.

### Step 3: Configure the Lambda Function
1. Set up a CloudWatch Events rule to trigger the Lambda function on a schedule (e.g., daily or weekly).
2. Test the Lambda function to ensure it works correctly.

## Testing
1. Manually create some EBS snapshots and ensure they are not attached to any active EC2 instances.
2. Trigger the Lambda function manually or wait for the scheduled event.
3. Verify that the stale snapshots are deleted.

## Future Improvements
- Add notifications using SNS to alert administrators when snapshots are deleted.
- Integrate with a monitoring dashboard to provide insights into cost savings.
- Implement additional filters to fine-tune which snapshots should be deleted.

## Contributing
Contributions are welcome! Please fork the repository and submit a pull request with your changes.
