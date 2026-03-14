# Android Static Analysis Framework (SIH1748)

A practical framework for **static analysis of vulnerabilities in Android applications**.

This repository aligns with the SIH1748 problem statement:
> Creating a Framework for Static Analysis of Vulnerabilities in Android Applications.

## What this repository now contains

- A structured end-to-end framework for Android static security analysis
- Tooling guidance (Lint, MobSF, SonarQube, PMD, SpotBugs, dependency scanners)
- A repeatable workflow for preparation, scanning, reporting, and remediation
- A CI/CD integration blueprint for continuous vulnerability governance

## Main document

- `docs/SIH1748_static_analysis_framework.md`

This document details:
1. Preparation and scope definition
2. Manual and automated code review flow
3. Manifest and Gradle configuration analysis
4. Third-party dependency vulnerability analysis
5. Reporting and severity prioritization
6. Mitigation and remediation lifecycle
7. CI/CD enforcement strategy

## Goal

Enable teams to detect and fix Android security issues **before deployment**, improving both code quality and production security posture.
