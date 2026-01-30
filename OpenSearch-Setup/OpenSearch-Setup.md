The Nautilus DevOps team needs to set up an Amazon OpenSearch Service domain to store and search their application logs. The domain should have the following specification:

1. The domain name should be datacenter-es.

2. Use Terraform to create the OpenSearch domain. The Terraform working directory is /home/bob/terraform. Create the main.tf file (do not create a different .tf file) to accomplish this task.

Solution :

```
resource "aws_opensearch_domain" "datacenter-es" {
  domain_name    = "datacenter-es"
}
```
