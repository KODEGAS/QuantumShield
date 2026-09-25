# QuantumShield

## A Post-Quantum Secure Cloud-Native Healthcare Platform

> **QuantumShield** is a research-oriented cloud-native healthcare platform that investigates the practical integration of **Post-Quantum Cryptography (PQC)** into a distributed, FHIR-based healthcare system using modern API management, event-driven architecture, Kubernetes, and cloud-native platform engineering.

---

## Table of Contents

* [Overview](#overview)
* [Problem Statement](#problem-statement)
* [Project Aim](#project-aim)
* [Objectives](#objectives)
* [Key Features](#key-features)
* [System Architecture](#system-architecture)
* [Architecture Components](#architecture-components)
* [Healthcare Data Model](#healthcare-data-model)
* [Event-Driven Processing](#event-driven-processing)
* [Post-Quantum Cryptography](#post-quantum-cryptography)
* [Hybrid Cryptography](#hybrid-cryptography)
* [Security Architecture](#security-architecture)
* [Microservices](#microservices)
* [Technology Stack](#technology-stack)
* [Repository Structure](#repository-structure)
* [Application Workflow](#application-workflow)
* [Kubernetes Architecture](#kubernetes-architecture)
* [OpenChoreo Integration](#openchoreo-integration)
* [Observability](#observability)
* [Performance Evaluation](#performance-evaluation)
* [Research Questions](#research-questions)
* [Project Scope](#project-scope)
* [Development Roadmap](#development-roadmap)
* [Getting Started](#getting-started)
* [Configuration](#configuration)
* [Security Considerations](#security-considerations)
* [Testing](#testing)
* [Benchmarking](#benchmarking)
* [Expected Outcomes](#expected-outcomes)
* [Limitations](#limitations)
* [Contributing](#contributing)
* [Research Context](#research-context)
* [License](#license)

---

# Overview

Healthcare systems process extremely sensitive information, including:

* Patient identities
* Medical observations
* Diagnoses
* Prescriptions
* Clinical history
* Appointments
* Healthcare-provider information

As healthcare platforms increasingly adopt distributed and cloud-native architectures, protecting this information requires security mechanisms that address both current and emerging threats.

One significant long-term concern is the potential impact of sufficiently powerful quantum computers on currently deployed public-key cryptographic algorithms.

QuantumShield investigates how **Post-Quantum Cryptography (PQC)** can be integrated into a modern healthcare platform while maintaining:

* Healthcare interoperability
* API security
* Scalability
* Availability
* Observability
* Performance
* Cloud-native deployment
* Migration compatibility

The platform uses **HL7 FHIR**, **Go**, **Next.js**, **PostgreSQL**, **WSO2 API Manager**, **Siddhi**, **Kubernetes**, and **OpenChoreo**, with **ML-KEM** and **ML-DSA** forming the primary PQC research components.

---

# Problem Statement

Modern healthcare applications increasingly depend on:

* Distributed services
* REST APIs
* Cloud infrastructure
* Third-party integrations
* Real-time event processing

This creates several engineering and security challenges.

The platform must provide:

1. Protection of healthcare data during transmission and storage.
2. Strong authentication and authorization for distributed APIs.
3. Real-time processing of healthcare events.
4. Scalable and resilient cloud-native deployment.
5. Protection against future cryptographic threats.
6. A practical migration path toward post-quantum cryptography.

The central research problem is:

> **How can post-quantum cryptography be incorporated into a cloud-native healthcare platform while maintaining interoperability, scalability, security, and acceptable performance?**

QuantumShield addresses this problem through a working prototype and controlled experimental evaluation.

---

# Project Aim

The primary aim of QuantumShield is to:

> **Design and implement a cloud-native healthcare platform that investigates the practical integration of post-quantum cryptography with FHIR-based APIs and Kubernetes-based infrastructure.**

The project also evaluates the architectural and performance implications of using post-quantum cryptographic mechanisms compared with conventional cryptographic mechanisms.

---

# Objectives

## 1. Healthcare Data Platform

Develop a healthcare backend using the **HL7 FHIR** standard.

Initial resources include:

* `Patient`
* `Practitioner`
* `Observation`
* `Appointment`

---

## 2. Full-Stack Application

Develop a web application allowing authorized users to:

* Manage patients
* Create observations
* View observations
* Manage appointments
* Monitor alerts
* Inspect security information
* Inspect audit events

---

## 3. API Management

Integrate **WSO2 API Manager** to provide:

* Authentication
* Authorization
* API security policies
* Rate limiting
* API versioning
* Monitoring
* Controlled access to backend services

---

## 4. Event-Driven Processing

Implement real-time processing of healthcare events using **Siddhi**.

Example:

```text
Blood Pressure Observation
          │
          ▼
        Event
          │
          ▼
       Siddhi
          │
          ▼
   Pattern Detection
          │
          ▼
        Alert
```

The system can identify predefined patterns such as repeated abnormal observations within a specific time window.

---

## 5. Post-Quantum Cryptography

Investigate the integration of:

* **ML-KEM** — key establishment
* **ML-DSA** — digital signatures

The project focuses on understanding how these mechanisms can be incorporated into a distributed application architecture rather than simply adding a cryptographic library.

---

## 6. Kubernetes Deployment

Containerize and deploy the platform using Kubernetes.

The deployment investigates:

* Deployments
* Services
* ConfigMaps
* Secrets
* Ingress
* Health checks
* Resource limits
* Horizontal Pod Autoscaling
* Network Policies

---

## 7. Cloud-Native Platform Engineering

Investigate **OpenChoreo** as a developer platform for building and deploying services on Kubernetes.

Target workflow:

```text
Source Code
     │
     ▼
   Build
     │
     ▼
Container Image
     │
     ▼
 OpenChoreo
     │
     ▼
 Kubernetes
     │
     ▼
Running Application
```

---

## 8. Performance Evaluation

Compare conventional, post-quantum, and hybrid cryptographic approaches using measurable characteristics including:

* Key generation time
* Signing time
* Verification time
* Key size
* Signature size
* Ciphertext size
* CPU consumption
* Memory consumption
* Network overhead
* Request latency

The experiments are intended to be conducted under controlled conditions.

---

# Key Features

| Feature                | Description                                          |
| ---------------------- | ---------------------------------------------------- |
| FHIR Healthcare Data   | Standardized healthcare resource representation      |
| Patient Management     | Create and manage patient information                |
| Medical Observations   | Record healthcare observations                       |
| Appointment Management | Manage healthcare appointments                       |
| API Management         | Centralized API security and governance              |
| OAuth2/OIDC            | Identity and access management                       |
| RBAC                   | Role-based authorization                             |
| Event Processing       | Real-time healthcare event analysis                  |
| Alerting               | Detection of predefined healthcare patterns          |
| ML-KEM                 | Post-quantum key establishment research              |
| ML-DSA                 | Post-quantum digital signature research              |
| Hybrid Cryptography    | Classical + PQC migration investigation              |
| Kubernetes             | Container orchestration and scaling                  |
| OpenChoreo             | Cloud-native developer platform                      |
| Observability          | Metrics, logs, traces, and health monitoring         |
| Benchmarking           | Cryptographic and application performance evaluation |
| Audit Logging          | Tracking sensitive healthcare operations             |

---

# System Architecture

The high-level architecture consists of a web application, API management layer, healthcare microservices, database, event-processing layer, security layer, and Kubernetes platform.

```text
                         ┌─────────────────────┐
                         │      Next.js         │
                         │    Web Client        │
                         └──────────┬──────────┘
                                    │
                               HTTPS / OIDC
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │     WSO2 APIM       │
                         │                     │
                         │ Authentication      │
                         │ Authorization       │
                         │ Rate Limiting       │
                         │ API Security        │
                         │ API Versioning      │
                         │ Monitoring          │
                         └──────────┬──────────┘
                                    │
                  ┌─────────────────┼─────────────────┐
                  │                 │                 │
                  ▼                 ▼                 ▼
          ┌─────────────┐   ┌─────────────┐   ┌─────────────┐
          │   Patient   │   │ Observation │   │ Appointment │
          │   Service   │   │   Service   │   │   Service   │
          │     Go      │   │     Go      │   │     Go      │
          └──────┬──────┘   └──────┬──────┘   └──────┬──────┘
                 │                 │                 │
                 └─────────────────┼─────────────────┘
                                   │
                                   ▼
                            ┌──────────────┐
                            │  PostgreSQL  │
                            └──────┬───────┘
                                   │
                                Events
                                   │
                                   ▼
                            ┌──────────────┐
                            │    Siddhi    │
                            │    Event     │
                            │  Processing  │
                            └──────┬───────┘
                                   │
                                   ▼
                            ┌──────────────┐
                            │ Alert Service│
                            └──────────────┘


             ┌──────────────────────────────────────┐
             │          Security Layer              │
             │                                      │
             │  ML-KEM │ ML-DSA │ OAuth2/OIDC      │
             │  TLS    │ Hybrid Cryptography       │
             └──────────────────────────────────────┘

             ┌──────────────────────────────────────┐
             │         Platform Layer              │
             │                                      │
             │ Kubernetes │ OpenChoreo             │
             │ Autoscaling │ Observability          │
             └──────────────────────────────────────┘
```

The architecture separates healthcare functionality, API governance, event processing, cryptographic experimentation, and platform infrastructure.

---

# Architecture Components

## Frontend

**Next.js + TypeScript**

Responsible for:

* Healthcare user interface
* Patient management
* Observation management
* Appointment management
* Alert visualization
* Security information
* Audit-event visualization

---

## API Management

**WSO2 API Manager**

Acts as the controlled entry point for backend APIs.

Responsibilities include:

* Authentication
* Authorization
* Rate limiting
* API policies
* API versioning
* Monitoring
* Controlled service access

---

## Backend Services

Backend services are implemented using **Go**.

Initial services include:

```text
Patient Service
Observation Service
Appointment Service
Alert Service
```

---

## Database

**PostgreSQL**

Stores application and healthcare resource information.

The system uses synthetic healthcare data for development and experimentation.

---

## Event Processing

**Siddhi**

Processes healthcare events and detects predefined patterns.

Example:

```text
Observation
     │
     ▼
Event
     │
     ▼
Siddhi Pattern
     │
     ▼
Detected Event
     │
     ▼
Alert Service
```

---

# Healthcare Data Model

QuantumShield uses FHIR-based healthcare resources.

## Patient

```text
Patient
├── Identifier
├── Name
├── Date of Birth
├── Gender
└── Contact Information
```

## Observation

Initial observation types include:

* Blood Pressure
* Heart Rate
* Temperature
* Blood Glucose
* Oxygen Saturation

These observations are represented using FHIR resources.

## Appointment

Appointments provide scheduling information associated with healthcare users and patients.

---

# Event-Driven Processing

Healthcare observations generate events that can be analyzed by Siddhi.

For example:

```text
Patient P001
     │
     ├── 140 mmHg
     │
     ├── 150 mmHg
     │
     └── 160 mmHg
             │
             ▼
      Siddhi Event Engine
             │
             ▼
    3 abnormal observations
       within 10 minutes
             │
             ▼
 HighRiskObservationDetected
             │
             ▼
       Alert Service
             │
             ▼
          Web UI
```

The event-processing component is intended to detect meaningful predefined patterns in healthcare observations in real time.

---

# Alert System

The Alert Service consumes detected events and generates alerts.

Example:

```text
Patient: P001

Alert:
Repeated abnormal blood pressure readings

Severity:
High

Detected:
2026-09-24 12:30
```

Alerts can then be exposed through the web interface.

---

# Post-Quantum Cryptography

PQC is a central research component of QuantumShield.

The project focuses on two primary mechanisms.

## ML-KEM

**ML-KEM** is investigated for key establishment.

Conceptually:

```text
Client
   │
   │ ML-KEM Key Establishment
   ▼
Server
   │
   ▼
Shared Secret
```

---

## ML-DSA

**ML-DSA** is investigated for digital signatures.

Conceptually:

```text
Healthcare Event
       │
       ▼
   ML-DSA Sign
       │
       ▼
 Signed Event
       │
       ▼
 Verification
```

The project evaluates how PQC mechanisms can coexist with conventional cryptographic mechanisms during a migration period.

---

# Hybrid Cryptography

QuantumShield investigates three approaches:

### Classical

```text
Classical Cryptography
```

### Post-Quantum

```text
Post-Quantum Cryptography
```

### Hybrid

```text
Classical Cryptography
          +
Post-Quantum Cryptography
```

The objective is to experimentally investigate the trade-offs associated with each approach rather than assuming that a single approach is universally optimal.

---

# Security Architecture

Security is implemented across multiple layers.

```text
                         SECURITY
                            │
             ┌──────────────┼──────────────┐
             │              │              │
             ▼              ▼              ▼
         Identity       API Security       Data
             │              │              │
        OAuth2/OIDC      WSO2 APIM      Encryption
        RBAC             Rate Limits    PostgreSQL
                         Policies
             │
             ▼
       PQC Security
             │
        ┌────┴────┐
        │         │
      ML-KEM    ML-DSA
```

Security controls include:

* OAuth2/OIDC
* RBAC
* API security policies
* Rate limiting
* TLS
* Data protection
* ML-KEM experimentation
* ML-DSA experimentation
* Hybrid
