As part of the data migration process, the Nautilus DevOps team is actively creating several S3 buckets on AWS. They plan to utilize both private and public S3 buckets to store the relevant data. Given the ongoing migration of other infrastructure to AWS, it is logical to consolidate data storage within the AWS environment as well.

Create a public S3 bucket named xfusion-s3-22546 using Terraform.

Ensure the bucket is accessible publicly once created by setting the proper ACL.

The Terraform working directory is /home/bob/terraform. Create the main.tf file (do not create a different .tf file) to accomplish this task.

Solution :

```
resource "aws_s3_bucket" "xfusion-s3-22546" {
  bucket = "xfusion-s3-22546"

  tags = {
    Name        = "xfusion-s3-22546"
  }
}

resource "aws_s3_bucket_public_access_block" "xfusion-s3-22546" {
  bucket = aws_s3_bucket.xfusion-s3-22546.id

  block_public_acls       = false
  block_public_policy     = false
  ignore_public_acls      = false
  restrict_public_buckets = false
}

resource "aws_s3_bucket_acl" "xfusion-s3-22546" {
  depends_on = [
    aws_s3_bucket_public_access_block.xfusion-s3-22546
  ]
  bucket = aws_s3_bucket.xfusion-s3-22546.id
  acl    = "public-read"
}
```

Check :

```
aws s3api get-public-access-block --bucket xfusion-s3-22546

```

It will show something like this :

```
{
    "PublicAccessBlockConfiguration": {
        "BlockPublicAcls": true,
        "IgnorePublicAcls": true,
        "BlockPublicPolicy": true,
        "RestrictPublicBuckets": true
    }
}
```
