## Table of Contents

- [Introduction](#introduction)
- [Project Directory Structure](#project-directory-structure)
- [Terraform Code (terraform)](#terraform-code-terraform)
- [Shared Library Wrapper (Wrapper.groovy)](#shared-library-wrapper-wrappergroovy)
- [Jenkinsfile](#jenkinsfile)
- [How to Run the POC](#how-to-run-the-poc)
- [Conclusion](#conclusion)
- [Contact Information](#contact-information)
- [References](#references)

## Introduction

This Proof of Concept (POC) demonstrates the use of a Jenkins Shared Library to simplify and standardize the execution of Terraform CLI commands such as `init`, `validate`, `plan`, `apply`, and `destroy`. It features a minimal Terraform configuration, a Groovy-based wrapper class, a Jenkinsfile to trigger the execution, and a structured project directory to ensure consistent and repeatable pipeline behavior.

---

## Project Directory Structure

### Repo 1: `terraform-wrapper-code`
This is your project repository that contains the Jenkins pipeline and Terraform configuration.

```

terraform-wrapper-code/
├── Jenkinsfile
├── main.tf
├── terraform.tfvars
├── variables.tf
└── README.md

```


### Repo 2: `shared-library`
This is your Jenkins Shared Library repository, which provides reusable pipeline logic.

```
shared-library/
└── vars/
└── cloudninja/
└── Wrapper.groovy
README.md

```
































































































