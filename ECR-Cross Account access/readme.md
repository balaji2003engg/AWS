#Cross Account ECR image access to the lambda

1. Assume that ECR repo exists in acount1 and lambda exists in the account2. Example Amazon ECR repository cross-account policy and need to attach  the policy to the ECR 

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "CrossAccountPermission",
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::111111111111:root"
      },
      "Action": [
        "ecr:BatchGetImage",
        "ecr:GetDownloadUrlForLayer"
      ]
    },
    {
      "Sid": "LambdaECRImageCrossAccountRetrievalPolicy",
      "Effect": "Allow",
      "Principal": {
        "Service": "lambda.amazonaws.com"
      },
      "Action": [
        "ecr:BatchGetImage",
        "ecr:GetDownloadUrlForLayer"
      ],
      "Condition": {
        "StringLike": {
          "aws:sourceARN": "arn:aws:lambda:us-east-1:111111111111:function:*"
        }
      }
    }
  ]
}

2. Attach the below policy to the lambda 
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "ECR Repository Access Permissions",
      "Effect": "Allow",
      "Action": [
        "ecr:GetDownloadUrlForLayer",
        "ecr:BatchGetImage"
      ],
      "Resource": "arn:aws:ecr:us-east-1:222222222222:repository/hello-repository"
    }
  ]
}

```

Reference link  https://repost.aws/knowledge-center/lambda-ecr-image
```

Reference : 
https://repost.aws/knowledge-center/lambda-ecr-image
