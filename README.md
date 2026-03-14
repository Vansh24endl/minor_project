# Android Static Analysis Framework (SIH1748)

A practical framework for **static analysis of vulnerabilities in Android applications**.

This repository aligns with the SIH1748 problem statement:
> Creating a Framework for Static Analysis of Vulnerabilities in Android Applications.

## Where is the frontend and backend?

You are right to ask this.

The repository now includes dedicated folders:
- `frontend/` → UI/client layer
- `backend/` → API and analysis service layer

At this stage, these folders include starter `README.md` files so implementation can be added cleanly.

## Main framework document

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
