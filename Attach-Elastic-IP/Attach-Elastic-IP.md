The Nautilus DevOps team has been creating a couple of services on AWS cloud.
They have been breaking down the migration into smaller tasks, allowing for better control, risk mitigation, and optimization of resources throughout the migration process.

Recently they came up with requirements mentioned below. There is an instance named nautilus-ec2 and an elastic-ip named nautilus-ec2-eip in us-east-1 region. Attach the nautilus-ec2-eip elastic-ip to the nautilus-ec2 instance using Terraform only. The Terraform working directory is /home/bob/terraform. Update the main. tf file (do not create a separate •tf (file) to attach the specified Elastic IP to the instance).

Solution :

1.  Check for the state of Elastic IP

```
terraform state show aws_eip.ec2_eip
```

2.  Add association to eip resource

```
resource "aws_eip" "ec2_eip" {
...
 instance                  = aws_instance.ec2.id
...
}
```
