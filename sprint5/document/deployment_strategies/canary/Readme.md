# Deployment Strategies

<div align="center">
    <img width="600" height="300" alt="Terraform" src="https://spectralops.io/wp-content/uploads/2024/04/Canary-Deployment.jpg">
</div>


## Author Information

| **Last Modified** | **Version** | **Author**        | **Level**            | **Reviewer**         |
|--------------------|-------------|-------------------|----------------------|----------------------|
|                   |   V1        | Durgesh Sharma    | Internal review      | Pritam               |
|                   |             | Durgesh Sharma    | L0 Review            | Shreya Jaiswal       |
|                   |             | Durgesh Sharma    | L1 Review            | Abhishek V           |
|                   |             | Durgesh Sharma    | L2 Review            | Abhishek Dubey       |

---

## Table of Contents
1. [Introduction](#introduction)
2. [Overview of Deployment Strategies](#overview-of-deployment-strategies)
3. [Canary Deployment Strategy](#canary-deployment-strategy)
    - [Why Use Canary Deployment?](#why-use-canary-deployment)
    - [What is Canary Deployment?](#what-is-canary-deployment)
    - [Process Steps](#process-steps)
    - [Benefits](#benefits)
    - [Limitations](#limitations)
    - [When to Use](#when-to-use)
4. [Conclusion](#conclusion)
5. [References](#references)

---

## Introduction

This document provides a comprehensive overview of various deployment strategies used in software development, with a primary focus on **Canary Deployment**. Deployment strategies are critical to delivering new features and updates to users in a reliable and risk-controlled manner. By understanding these strategies, teams can minimize downtime, reduce risk, and improve user experience during software releases.

---

## Overview of Deployment Strategies

| Strategy           | Description                                                                 | Use Case                                         |
|--------------------|-----------------------------------------------------------------------------|--------------------------------------------------|
| Recreate           | Shuts down old version, then deploys the new one                            | Simple apps, downtime acceptable                 |
| Rolling            | Gradually replaces old instances with new ones                              | Web apps needing no downtime                     |
| Blue-Green         | Deploys new version alongside old; traffic switch is instant                | Zero-downtime with rollback safety               |
| Canary             | Releases to a small subset of users first                                   | Risk mitigation and real-user testing            |
| A/B Testing        | Sends traffic to multiple versions simultaneously to test behavior          | Feature testing and behavior analysis            |
| Shadow             | Routes copy of real traffic to new version without affecting users          | Performance and load testing                     |

---

## Canary Deployment Strategy

### Why Use Canary Deployment?

Canary Deployment is used to reduce the **risk of introducing defects** into production environments. Instead of exposing all users to a new release immediately, a **controlled subset** of users gets early access. This enables teams to:

- Detect bugs or regressions early using **real-world traffic**
- Roll back quickly with minimal user impact
- Validate performance and compatibility in production
- Gain confidence before full-scale deployment

This strategy is especially valuable in environments that prioritize **high availability, continuous delivery, and user trust**.

---

### What is Canary Deployment?

**Canary Deployment** is a deployment technique in which a new version of an application is released to a **small subset** of users before rolling it out to the entire infrastructure. It allows teams to **monitor the behavior** of the new release in a real-world scenario with **minimal risk**.

---

### Process Steps

| Step | Description |
|------|-------------|
| 1. Build & Test | Build the new version of the application and run automated tests. |
| 2. Deploy to Canary Environment | Deploy the new version to a small subset (canary group) of servers or users. |
| 3. Monitor Metrics | Monitor system performance, error rates, logs, and user feedback. |
| 4. Decide Rollback or Proceed | If no major issues are found, gradually roll out to more users; else rollback. |
| 5. Full Deployment | Complete the rollout once confidence is high in the new release. |

---

### Benefits

| Benefit | Description |
|--------|-------------|
| Risk Mitigation | Issues are caught early before full rollout. |
| Real-World Testing | New version is validated in real user environments. |
| Faster Feedback | Quick identification of bugs and performance issues. |
| Minimal Downtime | Only a small portion of users are affected if something breaks. |

---

### Limitations

| Limitation | Description |
|------------|-------------|
| Infrastructure Complexity | Requires traffic routing mechanisms (load balancers, service mesh). |
| Monitoring Required | Must have strong observability and alerting systems. |
| Delayed Rollouts | Slower release process compared to full deployment. |
| User Inconsistency | Some users may experience different versions temporarily. |

---

### When to Use

| Use Case | Reason |
|----------|--------|
| Critical Production Systems | Reduces the blast radius of failed releases. |
| High Traffic Applications | Allows load testing in live environment with control. |
| Frequent Feature Releases | Enables agile and safe experimentation. |
| Uncertain New Features | Helps gauge user response and performance before full rollout. |

---

## Conclusion

Deployment strategies play a pivotal role in ensuring that software releases are **safe, reliable, and user-friendly**. Among these, **Canary Deployment** stands out for its ability to balance risk and innovation by allowing **controlled exposure** of new versions to real users. While it introduces complexity in setup and monitoring, the **trade-off is worth it** for teams aiming to maintain high uptime and user satisfaction. By leveraging this strategy effectively, organizations can **deploy confidently** and recover gracefully from unexpected issues.

---

## Contact Information

| **Name**           | **Email Address**                              |
|---------------------|-----------------------------------------------|
| Durgesh Sharma      | durgesh.sharma.snaatak@mygurukulam.co         |

---

## References

| Title | Link |
|-------|------|
| Kubernetes Canary Deployments | [Kubernetes Docs](https://kubernetes.io/docs/concepts/cluster-administration/manage-deployment/#canary-deployments) |
| Canary Releases with Istio | [Istio Documentation](https://istio.io/latest/docs/tasks/traffic-management/canary/) |
| GitLab Canary Deployment Guide | [GitLab Docs](https://docs.gitlab.com/ee/user/project/canary_deployments.html) |
| AWS Canary Deployment with CodeDeploy | [AWS Docs](https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-configurations.html) |
| Canary Testing in Software Engineering | [Martin Fowler Blog](https://martinfowler.com/bliki/CanaryRelease.html) |










