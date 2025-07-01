
# Shared Library for Terraform Wrapper Code Execution

## Table of Contents
1. [Introduction](#introduction)
2. [Why Use This Library](#why-use-this-library)
3. [What This Library Does](#what-this-library-does)
4. [Prerequisites](#prerequisites)
5. [Supported Functions](#supported-functions)
6. [Inputs and Outputs](#inputs-and-outputs)
7. [Jenkins Usage Example](#jenkins-usage-example)
8. [Conclusion](#conclusion)

---

## Introduction
This shared library streamlines Terraform workflows in Jenkins, enabling efficient execution of common operations like initialization, validation, planning, application, and destruction of infrastructure.

---

## Why Use This Library
| Feature               | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| Simplified Execution  | Abstracts the repetitive Terraform CLI commands into reusable functions.   |
| Consistency           | Enforces a standard way of executing Terraform commands across projects.   |
| Ease of Integration   | Designed to work seamlessly with Jenkins pipelines, reducing complexity.   |
| Error Handling        | Built-in mechanisms for handling errors during Terraform execution.        |

---

## What This Library Does
| Function   | Description                                                                              |
|------------|------------------------------------------------------------------------------------------|
| `init`     | Initializes the working directory containing Terraform configuration files.             |
| `validate` | Validates the Terraform files for syntax errors and logical issues.                     |
| `plan`     | Creates an execution plan to preview changes without applying them.                     |
| `apply`    | Applies the changes defined in the Terraform configuration to your infrastructure.       |
| `destroy`  | Destroys the infrastructure managed by Terraform.                                       |

---
## Prerequisites
| Requirement             | Details                                                                 |
|--------------------------|-------------------------------------------------------------------------|
| Terraform Installed      | Ensure Terraform is installed on the Jenkins agent nodes.             |
| Jenkins Configuration    | Shared library configured in Jenkins, Necessary credentials and environment variables set up. |
| Proper Permissions       | Ensure that the user executing Terraform commands has appropriate permissions to manage infrastructure. |

---

## Supported Functions
| Function   | Description                                | Inputs                                      | Outputs                       |
|------------|--------------------------------------------|--------------------------------------------|-------------------------------|
| `init`     | Prepares the working directory for Terraform operations by downloading plugins and initializing the backend. | Path to the Terraform configuration directory, Backend configuration (optional). | Initialization status.         |
| `validate` | Validates the configuration files for errors. | Path to the Terraform configuration directory. | Validation status.            |
| `plan`     | Generates an execution plan for the changes defined in the configuration files. | Variables file path (optional), Plan output file name (optional). | Plan details.                 |
| `apply`    | Applies the changes to the infrastructure as per the configuration files. | Variables file path (optional), Auto-approve flag (optional). | Apply status.                 |
| `destroy`  | Destroys all resources managed by Terraform. | Variables file path (optional), Auto-approve flag (optional). | Destruction status.           |

---

## Inputs and Outputs
| Type    | Name               | Description                                                    |
|---------|--------------------|----------------------------------------------------------------|
| Input   | `terraformConfigDir` | Path to the directory containing Terraform configuration files. |
| Input   | `varsFilePath`       | Path to the Terraform variables file (optional).              |
| Input   | `planOutputFile`     | Name of the file to store the execution plan (optional).      |
| Input   | `autoApprove`        | Flag to automatically approve actions without prompting for confirmation (optional). |
| Output  | `executionStatus`    | Status of the operation (e.g., success, failure).             |
| Output  | `outputLogs`         | Logs generated during the Terraform execution.                |

---



## Jenkins Usage Example

### Jenkinsfile
```groovy
@Library('terraform-shared-library') _

def terraformUtils = new org.example.terraformUtils()
def environmentHelper = terraformEnvironment

pipeline {
    agent any
    parameters {
        string(name: 'ACTION', defaultValue: 'plan', description: 'Terraform action (init, validate, plan, apply, destroy)')
        string(name: 'VARS_FILE', defaultValue: '', description: 'Path to .tfvars file (optional)')
    }
    stages {
        stage('Setup') {
            steps {
                script {
                    // Get config directory for dev environment
                    env.CONFIG_DIR = environmentHelper('dev')
                }
            }
        }
        stage('Terraform Execution') {
            steps {
                script {
                    def configDir = "${env.WORKSPACE}/${env.CONFIG_DIR}"
                    if (params.ACTION == 'init') {
                        terraformUtils.init(configDir)
                    } else if (params.ACTION == 'validate') {
                        terraformUtils.validate(configDir)
                    } else if (params.ACTION == 'plan') {
                        terraformUtils.plan(configDir, params.VARS_FILE ?: null)
                    } else if (params.ACTION == 'apply') {
                        terraformUtils.apply(configDir, params.VARS_FILE ?: null, true)
                    } else if (params.ACTION == 'destroy') {
                        terraformUtils.destroy(configDir, params.VARS_FILE ?: null, true)
                    } else {
                        error "Invalid action: ${params.ACTION}"
                    }
                }
            }
        }
    }
}


```

## Conclusion

The shared library for Terraform wrapper code execution simplifies and standardizes Terraform operations in Jenkins pipelines. By utilizing reusable functions such as init, validate, plan, apply, and destroy, it ensures efficient, consistent, and error-free management of infrastructure as code. This library is an essential tool for teams looking to streamline their CI/CD processes and enhance productivity.


