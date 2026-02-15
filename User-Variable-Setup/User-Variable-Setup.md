The Nautilus DevOps team is automating IAM user creation using Terraform for better identity management.

For this task, create an AWS IAM User using Terraform with the following requirements:

The IAM User name iamuser_mark should be stored in a variable named KKE_user.
Note:

1. The configuration values should be stored in a variables.tf file.

2. The Terraform script should be structured with a main.tf file referencing variables.tf.
The Terraform working directory is /home/bob/terraform.

Solution : 

1. Creaate variable.tf file 
```
variable "KKE_user" {
  description = "The name of the IAM user to create"
  type        = string
  default     = "iamuser_mark"
}
```

2. Create main.tf file 
```
resource "aws_iam_user" "this" {
  name = var.KKE_user

  tags = {
    Name = var.KKE_user
  }
}

```