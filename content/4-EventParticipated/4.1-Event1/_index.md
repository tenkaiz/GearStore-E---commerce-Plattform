---
title: "Event 1"
date: 2026-05-23
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Summary Report: "Context Is Everything: Making AI Actually Work for You"

### 1. General Event Overview
- **Topic Title**: *Context Is Everything: Making AI Actually Work for You*.
- **Date**: May 23, 2026.
- **Keynote Speaker**: **Mr. Tinh Truong** - Platform Engineer at **GoTymeX** (Co-organized by AWS Vietnam & AWS Study Group).
- **Attendees**: Over 200 IT, Software Engineering, and Cloud students from universities across Ho Chi Minh City (HUTECH, VNU-HCM US, HCMUT, etc.).

---

### 2. Summary of Technical Content

#### A. The Essence of "Context" in AI-Assisted Engineering
- **Root Cause of AI Inefficiencies**: Inaccurate AI responses stem primarily from **insufficient input context** rather than model flaws. AI behaves like a junior developer newly onboarded into a project — without system architecture documentation, it makes wrong assumptions leading to "Hallucinations".
- **Complete Context Equation**:  
  $$\text{Context} = \text{Goal} + \text{Architecture Situation} + \text{Tech Constraints} + \text{Code Evidence}$$

#### B. The Simple Context Framework
The speaker introduced a structured 4-pillar input framework prior to querying AI:
1. **Goal**: Explicitly define the desired deliverable (e.g., *Write a REST Controller handling product image uploads to AWS S3*).
2. **Relevant Info**: Supply concise DTOs, DynamoDB Entity schemas, or `pom.xml` dependencies while stripping unnecessary noise.
3. **Constraints**: Enforce strict technology stacks (Java 21, Spring Boot 3.3.0), libraries (`software.amazon.awssdk:s3`), and prevent bloated external dependencies.
4. **Success Criteria**: Define code standards (Clean Code, `S3Exception` handling, structured logging).

#### C. 4 Practical AI Project Directions for Students
- **AI Code Reviewer**: Analyzes vulnerability patterns, memory leaks, and backend refactoring opportunities.
- **RAG Document Q&A App**: Intelligent Q&A retrieving insights from academic PDF lecture slides.
- **Personal Knowledge Hub**: Systematizes personal engineering notes for rapid contextual lookup.
- **Automated Test Generator**: Automatically generates Unit Test suites for REST API endpoints.

---

### 3. Personal Insights & Reflections

#### 💡 Shifting Mindset from "Code Generator" to "Context Engine"
- Reflection on **GearStore E-Commerce**: Prior to this workshop, I used generic prompts when coding, causing AI to generate outdated AWS SDK v1 code incompatible with my Java 21 / Spring Boot 3 stack.
- Post-workshop realization: **Context Engineering** is the core capability of future Cloud Engineers. Mastering underlying architecture (Spring Boot, DynamoDB, S3) ensures engineers lead AI rather than passively depending on it.

---

### 4. Practical Experience & Personal Impressions

- **Event Atmosphere**: The workshop was vibrant and engaging at the AWS Vietnam office. The modern setup and warm hospitality from the FCAJ team created an inspiring environment.
- **Key Outcomes**: The event provided cutting-edge technology perspectives, enabled networking with fellow cloud enthusiasts, and offered memorable souvenirs from AWS Vietnam.

---

#### Event Photo

![Student Vũ Hoàng Gia Huy attending AWS event]
