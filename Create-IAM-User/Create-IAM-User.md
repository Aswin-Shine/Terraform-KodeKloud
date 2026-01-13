When establishing infrastructure on the AWS cloud, Identity and Access Management (IAM) is among the first and most critical services to configure. IAM facilitates the creation and management of user accounts, groups, roles, policies, and other access controls. The Nautilus DevOps team is currently in the process of configuring these resources and has outlined the following requirements:

For this task, create an IAM user named iamuser_mark using terraform. The Terraform working directory is /home/bob/terraform. Create the main.tf file (do not create a different .tf file) to accomplish this task.

Solution :

```
resource "aws_iam_user" "iamuser_mark" {
  name = "iamuser_mark"
  tags = {
    Name = "iamuser_mark"
  }
}
```

Check :

```
aws iam get-user --user-name iamuser_mark
```

It will show something like this :

```
{
    "User": {
        "Path": "/",
        "UserName": "iamuser_mark",
        "UserId": "4ft1qy573213tphcjha5",
        "Arn": "arn:aws:iam::000000000000:user/iamuser_mark",
        "CreateDate": "2026-01-07T22:07:13.742923Z",
        "Tags": [
            {
                "Key": "Name",
                "Value": "iamuser_mark"
            }
        ]
    }
}
```
