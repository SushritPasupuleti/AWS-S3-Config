# AWS S3 Config

 Setting up AWS S3 for public access (ex: allow upload of pics and access to them for all)

## Generate Keypairs

> `Account` > `My Security Credentials` > `Access keys (access key ID and secret access key)` > `Create New Access Key`

Download the CSV File.

Example: 

| name | value |
| --- | --- |
| AWSAccessKeyId | Value |
| AWSSecretKey | Value |

These keys are necessary for access to all AWS Resources from aws-sdk

## Ensure Bucket Settings

Ensure that Block Public Access options are all disabled

## Bucket Policy

```json
{
    "Version": "2008-10-17",
    "Id": "Policy-id",
    "Statement": [
        {
            "Sid": "",
            "Effect": "Allow",
            "Principal": {
                "AWS": "*"
            },
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::bucket-name/*",
            "Condition": {}
        }
    ]
}
```

Replace `bucket-name` in `Statement.Resource` with your bucket name.

## CORS

```json
[
    {
        "AllowedHeaders": [
            "*"
        ],
        "AllowedMethods": [
            "GET",
            "HEAD",
            "POST",
            "PUT"
        ],
        "AllowedOrigins": [
            "*"
        ],
        "ExposeHeaders": []
    }
]
```