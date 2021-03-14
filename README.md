# aws iam policies

## Table of Contents
 - [Grant Access To Only One S3 Bucket](#grant-access-to-only-one-s3-bucket)
 - [Allows full EC2 access within a specific Region](#allows-full-ec2-access-within-a-specific-region)
 - [Describe all instances, and stop, start, and terminate only particular instances](#Describe all instances, and stop, start, and terminate only particular instances)


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

# Describe all instances, and stop, start, and terminate only particular instances
 - Describe all instances, and stop, start, and terminate only particular instances
 ```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "ec2:DescribeInstances",
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": [
        "ec2:StopInstances",
        "ec2:StartInstances",
        ec2:TerminateInstances
      ],
      "Resource": [
        "arn:aws:ec2:us-east-1:123456789012:instance/i-1234567890abcdef0",
        "arn:aws:ec2:us-east-1:123456789012:instance/i-0598c7d356eba48d7"
      ]
    }
  ]
}
 ```
