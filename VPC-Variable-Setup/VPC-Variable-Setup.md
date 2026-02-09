The Nautilus DevOps team is automating VPC creation using Terraform to manage networking efficiently. As part of this task, they need to create a VPC with specific requirements.

For this task, create an AWS VPC using Terraform with the following requirements:

The VPC name datacenter-vpc should be stored in a variable named KKE_vpc.

The VPC should have a CIDR block of 10.0.0.0/16.

Note:

The configuration values should be stored in a variables.tf file.

The Terraform script should be structured with a main.tf file referencing variables.tf.

Solution :

1. Create a variables.tf file

```
variable "KKE_vpc" {
  type = string
  default = "datacenter-vpc"
}

```

2. Create main.tf file

```
resource "aws_vpc" "datacenter-vpc" {
  cidr_block       = "10.0.0.0/16"

  tags = {
    Name = var.KKE_vpc
  }
}
```
