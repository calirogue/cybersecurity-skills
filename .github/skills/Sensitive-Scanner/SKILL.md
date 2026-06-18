---
name: scan-sensitive-data
description: Scans a repository for PII, PHI, and statutory compliance risks (FTC, DMCA, CFAA). Rates findings using NIST FIPS 199. Use before any commit, PR, or public release.
---

# Sensitive Data & Compliance Scanner

Scans a repo for PII, PHI, and code patterns that create FTC, DMCA, or CFAA exposure. Rates findings using **NIST FIPS 199** per **NIST SP 800-122**.

## NIST Ratings

| Rating | Impact |
|--------|--------|
| **HIGH** | Severe/catastrophic — identity theft, financial loss, legal liability |
| **MODERATE** | Serious — reputational, employment, or regulatory harm |
| **LOW** | Limited — minor risk in isolation |

Raise one level if: data belongs to a minor, 10+ distinct records in one file, combined with another identifier, or file is in a public-facing directory.

## PII / PHI Scan Patterns (run all in parallel)

| Group | Pattern | Base Rating |
|-------|---------|-------------|
| SSN | `\b\d{3}[-\s]?\d{2}[-\s]?\d{4}\b` | HIGH |
| Credit card | `\b(?:4[0-9]{12}(?:[0-9]{3})?|5[1-5][0-9]{14}|3[47][0-9]{13})\b` | HIGH |
| Bank account | `(account[_\s]?number\|acct[_\s]?no?)\s*[:=]\s*\d{6,17}` | HIGH |
| Gov ID | `(passport\|driver[_\s]?licen[sc]e)[_\s]?no?\s*[:=]\s*[A-Z0-9]{6,12}` | HIGH |
| Medical record / NPI | `(mrn\|npi\|hicn\|health[_\s]plan[_\s]id)\s*[:=]\s*[A-Z0-9\-]{5,20}` | HIGH |
| Diagnosis / Rx | `(icd[_\s-]?10\|cpt[_\s]?code\|diagnosis\|prescription)\s*[:=]\s*[A-Z0-9\.\-]{3,10}` | HIGH |
| Biometric / device | `(biometric\|fingerprint\|imei\|mac[_\s]?address)\s*[:=]\s*[A-Z0-9:\-.]{8,}` | HIGH |
| Date of birth | `(dob\|birth[_\s]?date\|date[_\s]?of[_\s]?birth)\s*[:=]\s*\d{1,2}[-/]\d{1,2}[-/]\d{2,4}` | MODERATE |
| Full name | `(patient[_\s]?name\|full[_\s]?name)\s*[:=]\s*["'][A-Za-z\s\-']{2,50}["']` | MODERATE |
| Email / Phone | `[a-zA-Z0-9._%+\-]+@[a-zA-Z0-9.\-]+\.[a-zA-Z]{2,}` · `(\+?1[-.\s]?)?\(?\d{3}\)?[-.\s]?\d{3}[-.\s]?\d{4}` | LOW |

## Statutory Compliance Scan Patterns (run in parallel with PII scan)

| Law | What to Flag | Pattern / Indicator | Rating |
|-----|-------------|---------------------|--------|
| **FTC Act § 5** | Unencrypted consumer data writes | `(localStorage\|sessionStorage\|cookie)\s*\[?\s*["']?(ssn\|credit_card\|password\|dob)` | HIGH |
| **FTC Safeguards Rule** | Plaintext financial data in config or logs | `(log\|print\|console)\s*\(.*?(account\|routing\|card[_\s]?number)` | HIGH |
| **FTC / COPPA** | Age-gate bypass or child data collection without consent | `(age\s*[<>=]+\s*1[0-2]\|is_child\|under_13)\s*[:=]\s*(true\|1\|bypass)` | HIGH |
| **DMCA § 1201** | DRM / copy-protection circumvention | `(drm[_\s]?bypass\|circumvent[_\s]?protection\|crack[_\s]?license\|keygen\|serial[_\s]?crack)` | HIGH |
| **DMCA § 1201** | Access control bypass (scraping past Cloudflare, CAPTCHA solvers) | `(captcha[_\s]?bypass\|cloudflare[_\s]?bypass\|anti[_\s]?bot[_\s]?bypass\|turnstile[_\s]?solve)` | MODERATE |
| **DMCA § 512** | Unlicensed copyrighted content served or stored | `(copyright\s+\d{4}.*?all rights reserved)` in non-comment source — flag for manual review | MODERATE |
| **CFAA § 1030(a)(2)** | Credential stuffing / brute force automation | `(brute[_\s]?force\|credential[_\s]?stuff\|password[_\s]?spray\|login[_\s]?attempt\s*[>]=\s*\d{3,})` | HIGH |
| **CFAA § 1030(a)(5)** | Unauthorized system disruption patterns | `(fork[_\s]?bomb\|dos[_\s]?attack\|flood[_\s]?request\|kill[_\s]?process.*loop)` | HIGH |
| **CFAA § 1030(a)(4)** | Unauthorized access or privilege escalation | `(sudo\s+--shell\|escalate[_\s]?privilege\|bypass[_\s]?auth\|admin[_\s]?override\s*=\s*true)` | HIGH |

Also glob for high-risk files: `**/*.csv`, `**/*.sql`, `**/*.db`, `**/*.sqlite`, `**/*patient*`, `**/*pii*`, `**/*phi*`, `**/*medical*`, `**/*crack*`, `**/*keygen*`

## Noise Filters

Skip: `node_modules/`, `vendor/`, `.git/`, `dist/`, `build/`, `*.min.js`, synthetic values (`555-` phones, `123-45-6789` SSNs, `example.com` emails, `John Doe`). Flag but do not skip test fixtures.

## Report Format

```
# Sensitive Data & Compliance Scan Report
Target: <path> | Date: <today> | Standard: NIST FIPS 199 / SP 800-122
Findings: <N> total  (High: N  Moderate: N  Low: N)

## HIGH / MODERATE / LOW
[H1] <Type> — <file>:<line>
  Matched: <truncated>
  Law: HIPAA / FTC / DMCA / CFAA / PCI-DSS / CCPA / GDPR
  Factors: <base rating + aggravating factors>
  Action: <one sentence>

## Files Flagged
- <path> — <reason>

## Regulatory Exposure Summary
<List only laws triggered. One line each with specific section and obligation.>

## Next Steps
1. Remediate HIGH findings before merging or deploying.
2. Purge committed data: git filter-repo --path <file> --invert-paths
3. Add .csv / .sql / .db / *crack* / *keygen* to .gitignore.
4. Add a pre-commit hook (gitleaks, detect-secrets) to block future commits.
5. For PHI: verify a BAA covers all vendors with repo access.
6. For DMCA/CFAA findings: escalate to legal before pushing to a public remote.
```

After the report ask: "Want me to (1) check git history for these patterns, (2) generate a .gitignore patch, or (3) draft a pre-commit hook config?"
