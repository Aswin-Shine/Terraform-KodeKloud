The Nautilus DevOps team is presently immersed in data migrations, transferring data from on-premise storage systems to AWS S3 buckets. They have recently received some data that they intend to copy to one of the S3 buckets.

S3 bucket named nautilus-cp-3611 already exists. Copy the file /tmp/nautilus.txt to s3 bucket nautilus-cp-3611 using Terraform. The Terraform working directory is /home/bob/terraform. Update the main.tf file (do not create a separate .tf file) to accomplish this task.

Solution :

1. Add this to main.tf file

```
resource "null_resource" "aws_cli" {
  provisioner "local-exec" {
    command = "aws s3 cp /tmp/nautilus.txt s3://nautilus-cp-3611/nautilus.txt"
  }
}

```

2. To check data is copied paste this to the terminal

```
aws s3 ls s3://nautilus-cp-3611

```
