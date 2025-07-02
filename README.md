
|**Author**        | **created on**       | **Version** |**Last edited on**| **Review Level**   | **Reviewer**      |
|---------------|------------|---------|--------|--------|----------------------|
| Pravalika Kanikarapu  |July 02  | v1.0|   July 03  | Pre-Reviewer   | Priyanshu            |
| Pravalika Kanikarapu  |  |  |   | L0             | Priyanka     |
| Pravalika Kanikarapu  |      |      |         | L1             | Rishabh Sharma       |
| Pravalika Kanikarapu  |      |      |         | L2             | Piyush Upadhyay      |


# What is Unit Testing in Terraform

Unit tests in Terraform help ensure that individual resources and modules perform correctly.

For more information related refer this link [Terraform Unit Test Documentation](https://github.com/Cloud-NInja-snaatak/Documentation/tree/kanika-SCRUM-571/IAC-unit-test/terraform/doc)

# Objective
Demonstrate Terraform unit testing on a sample Terraform module with successful test execution. The POC includes:

- Sample Terraform module

- Unit tests (syntax and logic verification)

- Automated test execution and verification

# Pre-requisites

| **Binary**  | **Description**                                |
|-------------|-----------------------------------------------|
| **Go**      | Programming language used for Terratest       |
| **Terraform** | Infrastructure as code tool                   |
| **AWS CLI** | AWS Command Line Interface (Optional)         |
| **Terratest** | Testing framework for Terraform              |


# Installation Steps for Terratest

## Step 1. Update your package list
![image](https://github.com/user-attachments/assets/e284b0a1-dddb-4d3c-813f-bc560f8bcfce)

## Step 2. Install Go using the package manager

```
sudo apt install golang-go
```
![image](https://github.com/user-attachments/assets/f621d812-bd22-48fe-b6bb-467eab885cf0)

![image](https://github.com/user-attachments/assets/aae73438-ff05-424a-a92a-951623a2a1bc)

## Step 3. Verify the installation

```
go version
```
![image](https://github.com/user-attachments/assets/64aa4d20-171d-401a-ad20-f24520142542)


## Step 4. Terrafrom installation

![image](https://github.com/user-attachments/assets/561b32f6-5de1-4fbe-8945-1434e41262c5)

## Step 5. create test file

![image](https://github.com/user-attachments/assets/3b0d8213-370b-423d-92b8-41eb7a1358f1)

## Step 6. test file script

## Step 7. Run Terratest
```
cd test
go mod init test
go get github.com/gruntwork-io/terratest/modules/terraform
go get github.com/stretchr/testify/assert
go test -v
```

# Conclusion
The purpose of this Proof of Concept was to evaluate Terratest as a tool for automating Infrastructure as Code (IaC) testing. It demonstrated the feasibility and effectiveness of validating Terraform configurations and ensuring infrastructure reliability before deployment.


#  Contact Information


| Name       | Email Address                |
|------------|------------------------------|
| Pravalika  | kanikarapu.pravalika.snaatak@mygurukulam.co|



#  Reference

| **Link**                                                                 | **Description**                                      |
|--------------------------------------------------------------------------|------------------------------------------------------|
| [Terratest](https://medium.com/@a.warkhade98/testing-your-infrastructure-as-code-using-terratest-3b1f774336ce)| Documentation followed from this link .|
| [Terratest Working](https://blog.nashtechglobal.com/getting-started-with-terratest/)|Terratest Working .|




