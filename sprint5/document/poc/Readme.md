# Terragrunt Proof of Concept (POC)

<div align="center">
    <img width="600" height="300" alt="Terraform" src="https://miro.medium.com/v2/resize:fit:500/1*7VMuUNxs8-a0CQnYlS1XDA.png">
</div>


## **Author Information**
| Last Updated | Version | Author          | Comment         | Reviewer     |
|--------------|---------|------------------|------------------|--------------|
| 02-07-2025   | V1.0    | Durgesh Sharma   | Internal Review  | Pritam       |
| 08-07-2025   | V2.0    | Durgesh Sharma   | L0               | Shreya       |
| 10-07-2025   | V3.0    | Durgesh Sharma   | L1               | Abhishek V   |

## Table of Contents

1. [Introduction](#1-introduction)  
2. [Directory Structure](#2-directory-structure)  
3. [Create a Module (e.g. ec2 module)](#3-create-a-module-eg-ec2-module)  
4. [Terragrunt Files](#4-terragrunt-files)  
5. [Terragrunt Commands & Output](#5-terragrunt-commands--output)  
   - [5.1 `terragrunt init`](#51-terragrunt-init)  
   - [5.2 `terragrunt validate`](#52-terragrunt-validate)  
   - [5.3 `terragrunt plan`](#53-terragrunt-plan)  
   - [5.4 `terragrunt apply`](#54-terragrunt-apply)  
   - [5.5 Created Instance](#55-created-instance)  
6. [Conclusion](#6-conclusion)  
7. [Contact](#7-contact)  
8. [References](#8-references)  

---

## 1. Introduction

This POC demonstrates how to use Terragrunt with Terraform for modular and environment-based infrastructure provisioning. It showcases remote state management via S3 and state locking using DynamoDB while deploying an AWS EC2 instance.

---

## 2. Directory Structure

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEieGHM56CSJ5bNLrMKbKHth6wUZd5TJAiuXbSH05nqY8ygGEoinT4PzKpc0NdcqDLA6lkTVFTd5qGKlHD8xz4ZRR96JGq8zlUYSfwc5upQ3YqIKyblYEO2dFWggLZquHkUraxJfbs01AhhESnbkJwmptc3sT-hUGB_sEPQpy-v4uPyO-6xNBDNTarrYOts/s16000/terragrunt%20ds.PNG" width="600"/>

---

## 3. Create a Module (e.g. ec2 module)

### main.tf

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhJ1d_hi4M2JGajQN12zra2XAma-FlBTcPO7u16bVIJSk0zoaqFEOGXq01JR2WUjh2-YasSc_aItPxVqJ7tIT9AbUQPvg5U_bNIZJ0n2CKi71E4caWXkLa0RdHEo7tertS3RgIEe_BvQgf4FvtaLxbTM7Xrmp-U2cmnIB56WTn77VF4ZhCdZZCR1Jp75OU/s16000/main.PNG" width="800" height="400"/>

---

### variable.tf

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjtk56A-x_JxanegKIx814tZzv73yqnuVO83RkT6zLfIs1T8uz2au9h2ZcjKSM1nY1m7ZxDRf4OxIga3lzLreRRY6fRk30OaMJVjikms4GTFsioEeWNhCYBWY_zR3YTXHXvQkPOaRkBdiIUdSxQT0wNpT7MJPeUHA1pSbNP8Ogtpy09v9Zav6Eh6AlEjWo/s16000/variable.PNG" width="800" height="400"/>

---

### output.tf

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgqKm6IZdNWWpTTIrVbWCHZ89kENGWJkGkBmrZtqX3Q8XbqiFVcZ4oZ3nVrwozSDsWJtdea0UcNiWv-eMLTt4EfheiTuTdMWoZTfz4Xz11-cdybdKywxpGBIcaQbL31sgqcuiWNtYr7ZycFQrdFBgiRXZASeiv-r9p0tCeZ6iLXjEFa5xyxu0FdsGRNoKo/s16000/outputmodu.PNG" width="800" height="400"/>

---

## 4. Terragrunt Files

### root.hcl

<img src="https://blogger.googleusercontent.com/img/a/AVvXsEhZEdpNu4TMMeU-XxbjdZxPMkcSKId9aUJwc6PJAHPknQvtgiDOXDqznW-UOCvya0KiVkbzrmpuUQ5l7b9aRrMgMWkB-OFXeFgOkYgNzcSlMFLCaGxKu9GqLIXpfHkXSVdwuODjl-KA06LBkAZr_MKQ70pwsIC5RCCASTO0LSpNXacFHXuArC48bvKPi1Y=s16000" width="800" height="400"/>

---

### env/dev/ec2/terragrunt.hcl

<img src="https://blogger.googleusercontent.com/img/a/AVvXsEjNeFBWkptq44yUKOR7fxTBJoeyG_MsNxIGMlLrJWsKry5MjCpXz8iMZMe2l7wS4yoJknZlx--kzZZQVDr2r50xhWsFnXY2FMP3uGdu_TM6_q4NWuTz_t-SlMCfvRFXNscvnFGlvrANOzfsb2V9a8-6mxioXVIawvoCYLITAR1AZFwguF5OFGe1Z6_deTI=s16000" width="800" height="400"/>

---

## 5. Terragrunt Commands & Output

> Change the directory to `env/dev/ec2` to deploy terragrunt.hcl of dev environment.  
> Follow [Step 5](https://github.com/snaatak-Downtime-Crew/Documentation/tree/main/common_stack/operating_system/ubuntu/sop/commoncommands#1-basic-system-commands) to change the directory and then run Terragrunt commands.

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEifYS1p-WmsW0F8VK1iYQrCP5EG0kbm_Bxw_MnegUvQa1Ogy2TZNF6J2qxMLbwsUf9qhQ4KhCS1sKkRSvN-f358pJAUwdQ7TnbwgwEW-m461CgiQADCv-NQrsZK3bdHMvlIr_H1QgL8FdSvxcIWCyEgmrvOZWUwd4G6kl2DAfl8lUqpgEW0Keou2GubN64/s16000/cd.PNG" width="800" height="400"/>

---

### 5.1 `terragrunt init`

> Initializes Terraform backend configuration and downloads necessary provider plugins.

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjICjqYdDDBuBP_-Rz2VRvsNgN6PfDI2tO2vjvd2Y-QeEAvLZx7zmCtfRLnTzIOUS4ykgmjZqVPtleAmGqpiPWIquYzJKwttXikW7jaoj9QZ8yX2G2RynRqQcLSZi66bS5q-bHMZ-BQ0Jdk6RyGpPhSs-XNY8sgGVaRYJ5SDy-eLkzXEYzzjefUIxFoEXA/s16000/terrainit.PNG" width="800" height="400"/>

---

### 5.2 `terragrunt validate`

> Checks whether the Terraform configuration files are syntactically valid.

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiOcjUF4vaC1jomcZBLMMVSNJew3IdyhgiQ7ql4dxl8HO-27CCo9ImFFzBqC3OeEqwWmWT4HGJToPW-NXLDu7h_IZOkUCiwlvoegMDHgKrztm5dls_br4iov3LKexwSGro4bkcH9Hy4MTT1F2ywTigUoYHMVWpoK52L9jA6nKhIgdaGiLebfQ2ZLNIHXFI/s16000/terravalidate.PNG" width="800" height="400"/>

---

### 5.3 `terragrunt plan`

> Generates an execution plan showing what actions Terraform will take.

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjYfEIdbRwhSNDVhOCjgomFi3JD5AT4llFGRKkbujC2rhdOtLqA9_fkHbRkJo05_1kAcdvyzGzkO3LeZwV8g6eFcgczfLsGHOKSrH_v15R5u6BefbpEMqvoOZdhiHkbqH5c3pv_8z_8nPZb-L6hG4aeUlKOj0g5hKKIPrPH_J6LmD34NQguPRSRp2_tG3o/s16000/terraplan.PNG" width="800" height="400"/>

---

### 5.4 `terragrunt apply`

> Applies the Terraform configuration to create or update infrastructure.

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgnfYCbI_9olR7tsi2NuN8b7Cl3MSamcr74IzpywV8kuiXxnO60tlizLXgB8PNJ1S_Aj7DxKxey0I8naPHM0kAcT8PWlcATkKvQwIrNrd-HfOKU3ZRm5Oub3w4OCWZHgUTJxlTUl0V3bh3Hf8gD8prV2raHCeMoPgZPUk3HlqOOuQx5sROM_wtydA1fQOw/s16000/terraapplyt.PNG" width="800" height="400"/>

---

### 5.5 Created Instance

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgcLaFXcprq0PyDEtHA5OwPd7ul3LiASXR8E54ZQStNKQJKthHV9lPz-3khl9FMLESvtSkei8IWKMMPp9evf6L_bmOQZTIBhUp_j3FHeeULFM7xeVENFXO_klzkBSBqsmBRbpn1Ksrun97EweFSjdYEIl4eksWhXciK5tiH_J7iS1R_MHJQ6dxeAO0CxRE/s16000/terraec2.PNG" width="800" height="400"/>

---

## 6. Conclusion

Terragrunt enhances Terraform by enabling DRY configurations, automating backend setups, managing complex dependencies, and facilitating multi-environment infrastructure. For teams managing large infrastructure footprints, Terragrunt is a must-have layer to organize and streamline Terraform usage beyond expectations.

---

## 7. Contact

| Name           | Email Address                                  |
|----------------|-------------------------------------------------|
| Durgesh Sharma | durgesh.sharma.snaatak@mygurukulam.co          |

---

## 8. References

| Reference                                                             | Description                  |
|----------------------------------------------------------------------|------------------------------|
| [Terragrunt Docs](https://terragrunt.gruntwork.io/)                 | Official Terragrunt Docs     |
| [Terraform Docs](https://developer.hashicorp.com/terraform/docs)    | Official Terraform Docs      |
