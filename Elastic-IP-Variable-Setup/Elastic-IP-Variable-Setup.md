The Nautilus DevOps team is strategizing the migration of a portion of their infrastructure to the AWS cloud. As part of this phased migration approach, they need to allocate an Elastic IP address to support external access for specific workloads.

For this task, create an AWS Elastic IP using Terraform with the following requirement:

The Elastic IP name nautilus-eip should be stored in a variable named KKE_eip. The Terraform working directory is /home/bob/terraform.

Solution :

1. Create a variables.tf file

```
variable "KKE_eip" {
  description = "The name for the Elastic IP"
  type        = string
  default     = "nautilus-eip"
}
```

2. Create main.tf file

```
resource "aws_eip" "nautilus" {
  # Tags help organize and identify your resources in AWS
  tags = {
    Name = var.KKE_eip
  }
}
```
