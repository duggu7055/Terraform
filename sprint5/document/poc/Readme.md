# Terragrunt Proof of Concept (POC)

## Table of Contents

1. [Introduction](#1-introduction)  
2. [Directory Structure](#2-directory-structure)  
3. [Terragrunt Files](#3-terragrunt-files)  
4. [Terragrunt Commands & Output](#4-terragrunt-commands--output)  
   - [4.1 `terragrunt init`](#41-terragrunt-init)  
   - [4.2 `terragrunt plan`](#42-terragrunt-plan)  
   - [4.3 `terragrunt apply`](#43-terragrunt-apply)  
   - [4.4 `terragrunt destroy`](#44-terragrunt-destroy)  
   - [4.5 `terragrunt output`](#45-terragrunt-output)  

## 1. Introduction

This POC demonstrates how to use Terragrunt with Terraform for modular and environment-based infrastructure provisioning. It showcases remote state management via S3 and state locking using DynamoDB while deploying an AWS EC2 instance.

## 2. Directory Structure

