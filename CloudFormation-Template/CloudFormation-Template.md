The Nautilus DevOps team is working on automating infrastructure deployment using AWS CloudFormation. As part of this effort, they need to create a CloudFormation stack that provisions an S3 bucket with versioning enabled.

Create a CloudFormation stack named xfusion-stack using Terraform. This stack should contain an S3 bucket named xfusion-bucket-22466 as a resource, and the bucket must have versioning enabled. The Terraform working directory is /home/bob/terraform. Create the main.tf file (do not create a different .tf file) to accomplish this task.

Solution :
```
resource "aws_cloudformation_stack" "xfusion-stack" {
  name = "xfusion-stack"

  parameters = {
    BucketName = "xfusion-bucket-22466"
  }

  template_body = jsonencode({
    Parameters = {
      BucketName = {
        Type        = "String"
        Default     = "xfusion-bucket-22466"
      }
    }

    Resources = {
      xfusionbucket22466 = {
        Type = "AWS::S3::Bucket"
        Properties = {
          BucketName = {
            "Ref" = "BucketName"
          },
          VersioningConfiguration = {
            "Status" = "Enabled"
          }
        }
      }
    }
  })
}
```