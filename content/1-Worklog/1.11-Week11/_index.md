---
title: "Week 11 Worklog"
date: 2026-07-20
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

# Week 11 Worklog (13/07/2026 – 19/07/2026)

#### 1. Weekly Objectives
- Configure the Maven Shade Plugin for optimized packaging.
- Remove unnecessary dependencies from the deployment package.
- Generate an optimized `backend-0.0.1-SNAPSHOT.jar` to reduce AWS Lambda Cold Start time.

#### 2. Technical Activities Summary
This week focused on optimizing the deployment package for the GearStore backend application. I configured the **maven-shade-plugin** to generate a lightweight executable JAR while excluding unnecessary libraries and duplicate resources. The generated `backend-0.0.1-SNAPSHOT.jar` was analyzed to verify its contents and ensure compatibility with AWS Lambda. In addition, I evaluated the package size and applied optimization techniques to reduce Lambda Cold Start latency and improve deployment efficiency.

#### 3. Task Breakdown & Schedule

| Day | Task Activity | Status | Reference / Tool |
| :---: | :--- | :---: | :--- |
| **Mon** | Configure the Maven Shade Plugin for optimized packaging | Complete | Apache Maven Documentation |
| **Tue** | Remove unused libraries and duplicate resources | Complete | IntelliJ IDEA |
| **Wed** | Generate the `backend-0.0.1-SNAPSHOT.jar` package | Complete | Maven |
| **Thu** | Analyze the JAR file size and verify dependencies | Complete | Project Source Code |
| **Fri** | Review deployment package and evaluate Cold Start optimization | Complete | AWS Documentation |

#### 4. Key Deliverables & Outcomes
- **Completed Deliverables**: Successfully configured the Maven Shade Plugin, generated the optimized deployment JAR, removed unnecessary dependencies, and verified the deployment package for AWS Lambda.
- **Skill Acquisition**: Improved knowledge of Maven packaging optimization, dependency management, executable JAR generation, and AWS Lambda Cold Start performance optimization.