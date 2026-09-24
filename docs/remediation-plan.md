# Remediation Plan

## Remediated Findings

### SEC-001 — Insecure Shared-Link Access Control
- **Severity:** High
- **Status:** Remediated
- **Remediation:** Secured shared report links using unpredictable random tokens, expiry controls, and authorization checks.
- **Validation:** Verified that unauthorized users cannot access protected shared reports.

### SEC-002 — Weak Protection of Share Passwords
- **Severity:** High
- **Status:** Remediated
- **Remediation:** Passwords are protected using secure hashing instead of storing them in plaintext.
- **Validation:** Verified that plaintext share passwords are not stored.

### SEC-003 — Container Excessive Privileges
- **Severity:** High
- **Status:** Remediated
- **Remediation:** The container now runs as a non-root user. Container privileges are restricted using:
  - `allowPrivilegeEscalation: false`
  - `readOnlyRootFilesystem: true`
  - Dropping all Linux capabilities
  - `seccompProfile: RuntimeDefault`
- **Validation:** Docker image and Kubernetes deployment configuration were reviewed.

## Dependency Findings

### Dependency Vulnerabilities
- **Status:** Pending scan validation
- **Action:** Run `pip-audit` against `app/requirements.txt`.
- **Remediation:** Upgrade only dependencies reported as vulnerable by the scan.
- **Validation:** Run `pip-audit` again after remediation and confirm the finding is resolved.

## Deferred Findings

No findings are marked as deferred at this stage.

## Validation

The following security checks will be executed after remediation:

- Bandit SAST scan
- pip-audit dependency scan
- Trivy container scan
- Trivy IaC scan
- Helm lint