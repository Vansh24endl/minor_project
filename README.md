# Android Static Analysis Framework

### Detecting Vulnerabilities in Android Applications

A research-oriented framework designed to perform **static security analysis on Android applications**.
The system scans APK files and application code to detect insecure configurations, unsafe API usage, and known vulnerability patterns **without executing the application**.

The goal is to help developers and security analysts **identify security risks early in the development lifecycle.**

---

## What This Project Does

This framework performs automated security checks on Android applications by:

• Extracting and analyzing APK files
• Inspecting AndroidManifest permissions
• Detecting insecure API usage
• Identifying hardcoded secrets and risky configurations
• Generating structured vulnerability reports

---

## Development Roadmap

The project follows a **12-week structured development cycle** used in the minor project program.

| Week | Focus                                      |
| ---- | ------------------------------------------ |
| 1    | Project understanding & problem definition |
| 2    | Functional modeling (Use Case Diagram)     |
| 3    | Domain modeling & class diagrams           |
| 4    | System interaction & sequence diagrams     |
| 5    | Architecture design                        |
| 6-8  | Core framework implementation              |
| 9-10 | Testing and vulnerability validation       |
| 11   | Documentation                              |
| 12   | Final review & submission                  |

---

## Project Architecture

The repository is organized **feature-wise**, making the framework modular and scalable.

```id="1tzpyr"
project-root
│
├── docs
│   ├── weekly-reports
│   ├── uml-diagrams
│   └── documentation
│
├── src
│   ├── apk-analyzer
│   ├── manifest-parser
│   ├── vulnerability-detector
│   ├── rule-engine
│   └── report-generator
│
├── data
│   └── vulnerability-rules
│
└── README.md
```

Each module is responsible for a specific part of the static analysis pipeline.

---

## System Actors

Security Analyst
Runs vulnerability scans and reviews reports.

Admin
Manages detection rules and vulnerability datasets.

---

## Core Components

**APK Analyzer**
Extracts application structure from APK files.

**Manifest Parser**
Analyzes AndroidManifest.xml for risky permissions.

**Vulnerability Detector**
Scans code patterns to identify insecure practices.

**Rule Engine**
Applies predefined vulnerability rules.

**Report Generator**
Produces structured vulnerability reports.

---

## Tech Stack

Java / Python
Android SDK Tools
Git & GitHub
Jira (task tracking)
UML (system modeling)

---

## Vision

To create a lightweight static analysis framework that helps developers detect Android security vulnerabilities **before deployment**.

---

## Author

Vansh Dhumal
