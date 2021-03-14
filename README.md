# aws iam policies

## Table of Contents
 - [Grant Access To Only One S3 Bucket](#grant-access-to-only-one-s3-bucket)
 - [Allows full EC2 access within a specific Region](#allows-full-ec2-access-within-a-specific-region)


# Grant Access To Only One S3 Bucket
 - Grant full access to only one S3 Bucket and list all Buckets for users
 ```json
 {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                        "s3:GetBucketLocation",
                        "s3:ListAllMyBuckets"
                      ],
            "Resource": "arn:aws:s3:::*"
        },
        {
            "Effect": "Allow",
            "Action": "s3:*",
            "Resource": [
                "arn:aws:s3:::YOUR-BUCKET",
                "arn:aws:s3:::YOUR-BUCKET/*"
            ]
        }
    ]
}
 ```
 
# Allows full EC2 access within a specific Region
 - allows full EC2 access within a specific Region
 ```json
 {
     "Version": "2012-10-17",
     "Statement": [
         {
             "Action": "ec2:*",
             "Resource": "*",
             "Effect": "Allow",
             "Condition": {
                 "StringEquals": {
                     "ec2:Region": "REGION-CODE"
                 }
             }
         }
     ]
 }
```
