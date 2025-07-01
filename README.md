

![image](https://github.com/user-attachments/assets/d333aeb6-2758-4c43-afdf-cc2dcd29cd45)


# Terraform Unit Test Documentation

|**Author**        | **created on**       | **Version** |**Last edited on**| **Review Level**   | **Reviewer**      |
|---------------|------------|---------|--------|--------|----------------------|
| Pravalika Kanikarapu  | July 01  | v1.0|   July 01  | Pre-Reviewer   | Priyanshu            |
| Pravalika Kanikarapu  |  |  |   | L0             | Priyanka     |
| Pravalika Kanikarapu  |      |      |         | L1             | Rishabh Sharma       |
| Pravalika Kanikarapu  |      |      |         | L2             | Piyush Upadhyay      |

# Table of Contents

- [Introduction](#introduction)
- [Purpose](#purpose)
- [Terraform Unit Testing Tools](#terraform-unit-testing-tools)
- [Setup Steps](#setup-steps)
  - [Terratest](#terratest)
  - [kitchen-terraform](#kitchen-terraform)
- [Usage Examples](#usage-examples)
  - [Terratest Example](#terratest-example)
  - [kitchen-terraform Example](#kitchen-terraform-example)
- [Conclusion](#conclusion)
- [Contact Information](#--contact-information)
- [Reference](#--reference)


# Introduction
This documentation provides a comprehensive overview of Terraform unit testing, including tools like Terratest and kitchen-terraform, setup instructions, usage examples, and best practices. By integrating these tests into your development and CI/CD workflows, you can significantly improve the reliability, security, and scalability of your infrastructure code.



# Purpose
Terraform unit testing ensures that individual Terraform modules and components work as expected in isolation. These tests validate the logic, structure, and outputs of Terraform code before deploying infrastructure, helping catch bugs early and improve code reliability.


# Terraform Unit Testing Tools

| Tool               | Language | Provides                              | Capabilities                                                                 |
|--------------------|----------|----------------------------------------|------------------------------------------------------------------------------|
| [Terratest](https://terratest.gruntwork.io/)         | Go       | Real infrastructure testing using Go test framework | - Deploys actual resources<br>- Validates infrastructure behavior<br>- End-to-end module testing |
| [kitchen-terraform](https://newcontext-oss.github.io/kitchen-terraform/) | Ruby     | Test Kitchen integration for Terraform       | - Isolates modules using Test Kitchen lifecycle<br>- Supports InSpec for validation<br>- Compliance and configuration testing |


# Setup Steps

## Terratest
A Go-based testing framework that deploys real infrastructure to validate Terraform code.

Use [Terratest](https://terratest.gruntwork.io/) to write automated tests for your Terraform code in Go.

### 1. Install Go

Download and install Go from the official site:  
 https://go.dev/dl/

### 2. Set Up Go Project

```bash
mkdir terraform-test
cd terraform-test
go mod init terraform-test
```

### 3. Install Terratest Module
```
go get github.com/gruntwork-io/terratest/modules/terraform
```

### 4. Write Test File
Create a file main_test.go.

### 5. Run the Test
```
go test -v
```

## kitchen-terraform

A Ruby-based tool that uses Test Kitchen to isolate and test Terraform modules.

[kitchen-terraform](https://newcontext-oss.github.io/kitchen-terraform/) integrates Terraform with [Test Kitchen](https://kitchen.ci/) to test infrastructure code.

### 1. Install Ruby

Download and install Ruby from the official site:  
https://www.ruby-lang.org/

### 2. Install Bundler

```bash
gem install bundler
```
### 3. Create a Gemfile
```
# Gemfile
source 'https://rubygems.org'
gem 'kitchen-terraform'
```
### 4. Install Dependencies
```
bundle install
```
### 5. Create .kitchen.yml
Define driver, provisioner, verifier, and platforms.

### 6. Run Tests
```
kitchen test
```
This will:

- Initialize Terraform

- Apply your configuration

- Run InSpec tests

- Destroy the resources

# Usage Examples

## Terratest Example
```
package test

import (
  "testing"
  "github.com/gruntwork-io/terratest/modules/terraform"
  "github.com/stretchr/testify/assert"
)

func TestTerraformModule(t *testing.T) {
  terraformOptions := &terraform.Options{
    TerraformDir: "../module-path",
  }

  defer terraform.Destroy(t, terraformOptions)
  terraform.InitAndApply(t, terraformOptions)

  output := terraform.Output(t, terraformOptions, "output_name")
  assert.Equal(t, "expected_value", output)
}
```

## kitchen-terraform Example
### .kitchen.yml:
```
driver:
  name: terraform

provisioner:
  name: terraform

verifier:
  name: terraform

platforms:
  - name: local

suites:
  - name: default
    verifier:
      systems:
        - name: example
          controls:
            - example
```

test/integration/default/controls/example.rb:

```
control 'example' do
  describe output('output_name') do
    its('value') { should eq 'expected_value' }
  end
end
```

# Conclusion
Terraform unit testing helps catch infrastructure code issues early, increases confidence in deployments, and supports modular and scalable infrastructure development. Tools like Terratest and kitchen-terraform offer developers the flexibility to test in real or simulated environments using familiar programming and configuration languages. Integrating these testing practices into your CI/CD pipeline ensures higher quality and reliability in your infrastructure as code.

#  Contact Information


| Name       | Email Address                |
|------------|------------------------------|
| Pravalika  | kanikarapu.pravalika.snaatak@mygurukulam.co|



#  Reference

| **Link**                                                                 | **Description**                                      |
|--------------------------------------------------------------------------|------------------------------------------------------|
| [Terratest](https://terratest.gruntwork.io/)| Official documentation site for Terratest .|
| [kitchen-terraform ](https://newcontext-oss.github.io/kitchen-terraform/)| Official documentation site for kitchen-terraform .|


