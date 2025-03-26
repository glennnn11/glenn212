# Assignment 2.12

# Lambda Function and S3 Bucket Configuration

## 1. Purpose of the Execution Role on the Lambda Function:
The execution role is an AWS IAM role that the Lambda function assumes during its execution. It defines the permissions that the Lambda function has when interacting with other AWS services or resources. In this case, the role is to grant the Lambda function permission to access S3, read files from the S3 bucket, and perform other necessary actions like uploading files, logging to CloudWatch, etc.

## 2. Purpose of the Resource-Based Policy on the Lambda Function:
A resource-based policy is applied directly to the Lambda function and defines who (which AWS services or accounts) can invoke the Lambda function. The resource-based policy ensures that S3 has the appropriate permissions to trigger the function.

## 3. Lambda Function Needs to Upload a File into an S3 Bucket:
If the Lambda function needs to upload a file into an S3 bucket, it requires permission to perform the PutObject operation on the target S3 bucket.

### Execution Role Update:
The execution role needs to be updated to include the permission to upload files to the target S3 bucket. This can be achieved by adding the following permission to the role:
- **Action**: s3:PutObject
- **Resource**: The ARN of the specific S3 bucket and path (e.g., arn:aws:s3:::your-bucket-name/*)

### Resource-Based Policy Update:
The **execution role** handles the required permissions for uploading files to S3. In this case, no new resource-based policy is needed because the Lambda function is already the target of the S3 event trigger. The Lambda function's resource-based policy will ensure that S3 can invoke the function, but this does not directly affect the Lambda's ability to upload files. 
