# SIH1748 – Framework for Static Analysis of Vulnerabilities in Android Applications

## 1) Objective
Build a repeatable static-analysis workflow that helps teams detect and fix Android security vulnerabilities early, before release.

## 2) Scope Definition (Preparation)

### Gather Requirements
- Define target artifact(s): source repository, APK, or both.
- Define analysis depth:
  - Manifest/config checks only
  - Source-level checks
  - Dependency and SBOM checks
- Define vulnerability categories in scope:
  - Insecure data storage
  - Hardcoded secrets
  - Insecure API usage
  - Injection and deserialization risks
  - Misconfigured permissions/components
  - Outdated vulnerable dependencies

### Select Tooling Baseline
Use a layered toolchain so one tool’s blind spots are covered by others.

| Layer | Suggested Tools | Purpose |
|---|---|---|
| Android-native checks | Android Lint | Build-time Android-specific security/code quality checks |
| Code quality & security rules | SonarQube, PMD, SpotBugs (FindBugs successor) | Pattern-based static issue detection |
| Mobile-focused scanner | MobSF | APK/source security assessment and consolidated reporting |
| Dependency scanning | OWASP Dependency-Check, Gradle Versions Plugin | Known CVE detection and dependency hygiene |
| Secret scanning | Gitleaks/TruffleHog (optional) | Detect accidental key/token exposure |

## 3) Analysis Workflow

### A. Manual Code Review
Review high-risk modules first (auth, crypto, local storage, networking):
- Hardcoded API keys, tokens, passwords
- Insecure logging of sensitive data
- Improper exception handling leaking internals
- Weak cryptography usage (ECB, custom crypto)
- WebView misuse and unsafe JavaScript bridges

### B. Automated Static Analysis
Run tools in CI and locally:
1. Android Lint (project-aware checks)
2. SonarQube/PMD/SpotBugs (rule-based analysis)
3. MobSF static scan (APK and/or source)

Normalize outputs into a unified schema:
- File / component
- Rule ID
- Severity (Critical/High/Medium/Low)
- Confidence
- Evidence snippet
- Recommended fix

## 4) Configuration Security Review

### AndroidManifest.xml
Check for:
- `android:exported="true"` where not required
- Over-privileged permissions (`READ_SMS`, `WRITE_EXTERNAL_STORAGE`, etc.)
- Unprotected activities/services/providers
- Insecure intent filters and task affinity misuse
- Cleartext traffic enabled without necessity

### Build and Signing Configuration (Gradle)
Check for:
- Debuggable release builds
- Insecure ProGuard/R8 configuration
- Inconsistent minSdk/targetSdk security posture
- Signing config exposure in build scripts
- Dynamic dependency versions (`+`) causing non-reproducible builds

## 5) Dependency and Third-Party Library Analysis
- Generate dependency inventory (SBOM preferred).
- Identify vulnerable libraries and transitive dependencies.
- Enforce policy:
  - No critical CVEs in release branch
  - Time-bound remediation SLA for high/medium issues
- Track replacement plan for unmaintained libraries.

## 6) Reporting Model

Each scan cycle should produce:
1. Executive summary (risk posture, trend)
2. Detailed findings with evidence
3. Severity-prioritized remediation backlog
4. Compliance and policy violations
5. Delta from previous scan (new, fixed, reopened)

### Suggested Prioritization Matrix
- **Critical**: RCE, auth bypass, severe data exposure, exploitable exported components
- **High**: Sensitive data leakage, insecure crypto in production paths, vulnerable core dependencies
- **Medium**: Misconfigurations with limited exploitability
- **Low**: Hardening and best-practice deviations

## 7) Mitigation and Remediation Process

For each vulnerability:
1. Assign owner and due date based on severity.
2. Apply secure coding/configuration fix.
3. Add/adjust rule to prevent recurrence.
4. Re-scan and verify closure.
5. Document lessons learned in secure coding guidelines.

## 8) CI/CD Integration Blueprint
- Run fast checks on pull requests (Lint + lightweight rules).
- Run full scan nightly or on release branches (MobSF + dependency scan + full rule sets).
- Fail build when:
  - New Critical findings are introduced
  - High findings exceed defined threshold
- Publish reports as artifacts and notify responsible teams.

## 9) Expected Outcomes
- Early vulnerability detection in development lifecycle
- Improved secure coding quality and consistency
- Increased developer security awareness
- Reduced production exploitation risk

## 10) Deliverables for Minor Project
- Reproducible scanning pipeline
- Rule catalog and risk taxonomy
- Sample vulnerable app test cases and validation results
- Final report with metrics (finding density, MTTR, reopened rate)
