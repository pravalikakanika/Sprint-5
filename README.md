
![image](https://github.com/user-attachments/assets/78fcf178-08ea-4cf8-8d09-a74b47f406e9)


# Documentation for TerraGrunt

|**Author**        | **created on**       | **Version** |**Last edited on**| **Review Level**   | **Reviewer**      |
|---------------|------------|---------|--------|--------|----------------------|
| Pravalika Kanikarapu  | July 01  | v1.0|   July 01  | Pre-Reviewer   | Priyanshu            |
| Pravalika Kanikarapu  |  |  |   | L0             | Priyanka     |
| Pravalika Kanikarapu  |      |      |         | L1             | Rishabh Sharma       |
| Pravalika Kanikarapu  |      |      |         | L2             | Piyush Upadhyay      |


# Table of Contents

- [Terragrunt](#terragrunt)
- [Purpose](#purpose)
- [Features](#features)
- [Directory Structure](#directory-structure)
- [Usage Examples](#usage-examples)
- [Prerequisites](#prerequisites)
- [Best Practices](#best-practices)
- [Conclusion](#conclusion)
- [Contact Information](#contact-information)
- [References](#references)


# Terragrunt

Terragrunt is a thin wrapper for Terraform that provides extra tools for keeping your Terraform configurations DRY (Don't Repeat Yourself), managing remote state, and working with multiple Terraform modules across environments and regions.


# Purpose

Terragrunt helps solve common challenges with Terraform at scale by:
- Keeping Terraform code DRY via shared configurations.
- Automating remote state configuration.
- Managing module dependencies.
- Structuring environments and infrastructure layering.
- Simplifying workflows across multiple modules.



# Features

| Feature                  | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| **DRY Configurations**   | Reduce duplication in your Terraform code.                                  |
| **Multiple Environments**| Manage different configurations for different environments with ease.       |
| **Remote State**         | Automatically configure Terraform remote state storage.                     |
| **Built-in Locking**     | Use state locking to prevent concurrent updates to the same resources.      |
| **Dependency Management**| Automatically manage dependencies between your Terraform modules.           |


# Directory Structure

```text
infrastructure-live/
├── terragrunt.hcl                     # Root config (common settings)
├── prod/
│   ├── terragrunt.hcl                 # Prod-specific config
│   ├── us-east-1/
│   │   ├── terragrunt.hcl             # Region config
│   │   └── app/
│   │       └── terragrunt.hcl         # Module config
├── staging/
│   ├── terragrunt.hcl
│   └── us-east-1/
│       └── app/
│           └── terragrunt.hcl
```

# Usage Examples

## Basic Configuration

```hcl
locals {
  region = "us-east-1"
}

terraform {
  source = "git::https://github.com/org/terraform-modules.git//app"
}

inputs = {
  environment = "prod"
  region      = local.region
}
```

## Remote State Setup
```
remote_state {
  backend = "s3"
  config = {
    bucket         = "tf-state-bucket"
    key            = "prod/app/terraform.tfstate"
    region         = "us-east-1"
    encrypt        = true
    dynamodb_table = "tf-locks"
  }
}
```

## Module Dependencies
```
dependencies {
  paths = [
    "../vpc",
    "../database"
  ]
}
```

## Common Commands
```
terragrunt init
terragrunt plan
terragrunt apply
terragrunt run-all plan
terragrunt run-all apply
```



# Prerequisites

| Requirement                           | Description                                                                 |
|---------------------------------------|-----------------------------------------------------------------------------|
| Terraform                             | Installed from [terraform.io](https://www.terraform.io/downloads)          |
| Terragrunt                            | Installed from [terragrunt.io](https://terragrunt.gruntwork.io/)           |
| Cloud Provider CLI                    | Properly configured (e.g., AWS CLI with credentials and region)            |
| Remote State Backend                  | S3 bucket and DynamoDB table or equivalent setup for state and locking     |
| Git Access                            | Access to remote Git repositories if using modules from Git sources        |
| Terraform Knowledge                   | Familiarity with Terraform modules, variables, and workflow concepts       |


# Best Practices

| Best Practice                                      | Description                                                                 |
|---------------------------------------------------|-----------------------------------------------------------------------------|
| Root `terragrunt.hcl`                             | Centralize remote state and shared settings                                |
| Environment and Region Separation                 | Isolate configurations by env (prod/staging) and region                    |
| Versioned Modules                                  | Use Git tags or SHAs when referencing Terraform modules                    |
| Avoid Duplication                                 | Use `include`, `locals`, and shared files to reduce repetition             |
| Use Relative Paths                                | Improves portability across machines and environments                      |
| Secure Sensitive Data                             | Store secrets in environment variables or external secret managers         |
| Lock and Version State Backends                   | Prevent accidental drift or overwrite                                      |
| Cautious Use of `run-all`                         | Limit use in production; prefer targeted `apply` commands                  |
| Document Workflows                                | Help teams understand usage patterns and directory layout                  |

# Conclusion
Terragrunt enhances Terraform's capabilities by simplifying configuration management, enforcing structure, and reducing repetition. When used correctly, it enables teams to scale their infrastructure provisioning workflows efficiently across multiple environments and regions with consistency and control.

#  Contact Information


| Name       | Email Address                |
|------------|------------------------------|
| Pravalika  | kanikarapu.pravalika.snaatak@mygurukulam.co|



# References

| Links | Descriptions | 
|--------|------------|
| Terragrunt Documentation  | https://terragrunt.gruntwork.io/docs/  | 

