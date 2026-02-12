The Nautilus DevOps team is enhancing infrastructure automation and needs to provision a Security Group using Terraform with specific configurations.

For this task, create an AWS Security Group using Terraform with the following requirements:

The Security Group name xfusion-sg should be stored in a variable named KKE_sg.
Note:

1. The configuration values should be stored in a variables.tf file.

2. The Terraform script should be structured with a main.tf file referencing variables.tf.
   The Terraform working directory is /home/bob/terraform.

Solution :

1. Create variables.tf file

```
variable "KKE_sg" {
  description = "The name of the Security Group"
  type        = string
  default     = "xfusion-sg"
}
```

2. Create main.tf file

```
resource "aws_security_group" "this" {
  name        = var.KKE_sg
  description = "Security group for xfusion environment"

  # Ingress rule: Allow SSH access
  ingress {
    description = "Allow SSH"
    from_port   = 22
    to_port     = 22
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }

  # Egress rule: Allow all outbound traffic
  egress {
    from_port   = 0
    to_port     = 0
    protocol    = "-1"
    cidr_blocks = ["0.0.0.0/0"]
  }

  tags = {
    Name = var.KKE_sg
  }
}
```
