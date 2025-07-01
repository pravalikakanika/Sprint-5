# Document for terraform drift

|**Author**        | **created on**       | **Version** |**Last edited on**| **Review Level**   | **Reviewer**      |
|---------------|------------|---------|--------|--------|----------------------|
| Pravalika Kanikarapu  | July 01  | v1.0|   July 01  | Pre-Reviewer   | Priyanshu            |
| Pravalika Kanikarapu  |  |  |   | L0             | Priyanka     |
| Pravalika Kanikarapu  |      |      |         | L1             | Rishabh Sharma       |
| Pravalika Kanikarapu  |      |      |         | L2             | Piyush Upadhyay      |



# Purpose
Terraform unit testing ensures that individual Terraform modules and components work as expected in isolation. These tests validate the logic, structure, and outputs of Terraform code before deploying infrastructure, helping catch bugs early and improve code reliability.

# Tools

### 1. Terratest
- Go-based testing framework for Terraform.
- Supports infrastructure testing using actual apply/destroy cycles.
- Enables assertions on resource properties and outputs.

### 2. kitchen-terraform
- Ruby-based testing framework using Test Kitchen and InSpec.
- Useful for validating infrastructure state post-deployment.
- Integrates with Terraform for convergence and verification.















#  Contact Information


| Name       | Email Address                |
|------------|------------------------------|
| Pravalika  | kanikarapu.pravalika.snaatak@mygurukulam.co|



#  Reference

| **Link**                                                                 | **Description**                                      |
|--------------------------------------------------------------------------|------------------------------------------------------|
| [TerraformDrift](https://spacelift.io/blog/terraform-drift-detection)| Documentation followed from this link .|

