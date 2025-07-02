
![image](https://github.com/user-attachments/assets/42055118-3f18-4860-8739-99ded9c10443)

# Terragrunt Proof of Concept (POC) 

|**Author**        | **created on**       | **Version** |**Last edited on**| **Review Level**   | **Reviewer**      |
|---------------|------------|---------|--------|--------|----------------------|
| Pravalika Kanikarapu  | July 02  | v1.0|   July 03  | Pre-Reviewer   | Priyanshu            |
| Pravalika Kanikarapu  |  |  |   | L0             | Priyanka     |
| Pravalika Kanikarapu  |      |      |         | L1             | Rishabh Sharma       |
| Pravalika Kanikarapu  |      |      |         | L2             | Piyush Upadhyay      |


# Table of Contents

- [Overview](#overview)
- [Significance](#significance)
- [Prerequisites](#prerequisites)
- [Directory structure](#directory-structure)
- [Step-by-Step Guide](#step-by-step-guide)
- [Conclusion](#conclusion)
- [Contact Information](#contact-information)
- [References](#references)


  
# Overview

This document outlines the Proof of Concept (PoC) implementation of Terragrunt, a tool that provides extra features for managing Terraform configurations. The goal of this PoC is to demonstrate the capabilities of Terragrunt in simplifying the management of infrastructure as code.

# Significance
Terragrunt enhances Terraform by enabling the use of DRY (Don't Repeat Yourself) principles, facilitating easier management of multiple environments, and providing a way to keep configurations organized. This PoC aims to validate these benefits in a real-world scenario, showcasing how Terragrunt can streamline infrastructure management.


# Prerequisites

Before running this TerraGrunt POC, make sure the following tools are installed on your system:

| **Tool**    | **Version**        | **Purpose**                                |
|--------------|--------------------|--------------------------------------------|
| Terraform    | v1.1 or newer      | Infrastructure provisioning                |
| TerraGrunt   | v0.45 or newer     | Wrapper for Terraform modules              |
| AWS CLI      | Latest             | Configure AWS credentials                  |

>  **Note:** You must configure AWS credentials using `aws configure` before running Terraform or TerraGrunt.



## Directory structure

The project follows a specific directory structure to organize Terraform configurations and modules. Below is the directory structure used in this PoC:

```
terragrun-poc/
├── terraform-modules/
│   └── s3-bucket/
│       ├── main.tf
│       ├── outputs.tf
│       └── variables.tf
└── live/
    └── dev/
        └── terragrunt.hcl

```
#### Description of Directories

### `terraform-modules/s3-bucket/`
Reusable Terraform module that defines an AWS S3 bucket.

- **`main.tf`** — Contains resource definitions (e.g., S3 bucket resource).
- **`variables.tf`** — Defines input variables (e.g., bucket name, region).
- **`outputs.tf`** — Defines output values (e.g., bucket ARN, domain name).
### `live/dev/`
Environment-specific configuration for `dev` environment.

- **`terragrunt.hcl`** — TerraGrunt configuration file that:
  - Points to the reusable Terraform module (`terraform-modules/s3-bucket`).
  - Passes environment-specific inputs (e.g., bucket name).
  - Defines local environment variables.


# Step-by-Step Guide

## 1. Add Terraform module code
### terraform-modules/s3-bucket/main.tf
```
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}

provider "aws" {
  region = var.region
}

resource "aws_s3_bucket" "example" {
  bucket        = var.bucket_name
  force_destroy = true
}
```

### terraform-modules/s3-bucket/variables.tf
```
variable "bucket_name" {
  description = "Name of the S3 bucket"
  type        = string
}

variable "region" {
  description = "AWS region"
  type        = string
  default     = "us-east-1"
}
```
### terraform-modules/s3-bucket/outputs.tf
```
output "bucket_arn" {
  description = "ARN of the bucket"
  value       = aws_s3_bucket.example.arn
}

output "bucket_domain_name" {
  description = "Bucket domain name"
  value       = aws_s3_bucket.example.bucket_domain_name
}
```

## 2. Add TerraGrunt configuration

### live/dev/terragrunt.hcl
```
terraform {
  source = "../../terraform-modules/s3-bucket"
}

inputs = {
  bucket_name = "pravalika-terragrunt-poc-dev"
  region      = "us-east-1"
}

locals {
  env = "dev"
}
```

## 3. Navigate to the environment directory
```
cd terragrun-poc/live/dev
```

## 4. Initialize

![image](https://github.com/user-attachments/assets/be05d4cc-2de5-4984-8cd0-5c556a640a24)

## 5. Validate

![image](https://github.com/user-attachments/assets/3fdd772b-a406-41ae-ad6d-ebbcd03ff189)

## 6. Plan

![image](https://github.com/user-attachments/assets/901d51a9-ace5-48be-aa4d-273804275ac2)

## 7. Apply

![image](https://github.com/user-attachments/assets/6b368c3a-cd63-4fb3-8f08-da57a5a835fe)

## 8. Verify outputs

![image](https://github.com/user-attachments/assets/2ed2b55a-8312-4213-b7d6-043e72ab72a4)


##  Check in AWS console

- Go to S3 service.

- Verify the bucket named pravalika-terragrunt-poc-dev exists.


![image](https://github.com/user-attachments/assets/11fd128e-5241-4a8a-a2fb-0ef69cf0aed5)


## Conclusion

The PoC successfully demonstrates the advantages of using Terragrunt for managing Terraform configurations. By implementing a structured approach, Terragrunt simplifies infrastructure management, enhances code reuse, and facilitates better organization across multiple environments.

#  Contact Information


| Name       | Email Address                |
|------------|------------------------------|
| Pravalika  | kanikarapu.pravalika.snaatak@mygurukulam.co|


# References

| Links | Description      |
|-----  |--------------------------|
| https://terragrunt.gruntwork.io/docs/getting-started/configuration/ | Terragrunt configuration file |
| https://terragrunt.gruntwork.io/docs/community/support/ | Community Support | 
| https://terragrunt.gruntwork.io/docs/#reference | Reference |
