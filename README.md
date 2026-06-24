# Cyber Security Law — Investigative Skills Suite

A collection of Claude Code slash-command skills for white-collar crime research, corporate OSINT, forensic financial analysis, and whistleblower strategy. All skills are invoked directly in the Claude Code chat panel and automatically save dated output files to the `output/` directory.

---

## Setup

### Requirements
- [Claude Code](https://claude.ai/code) (VS Code extension, desktop app, or CLI)
- Active Claude subscription

### How Skills Work
Skills live in `.claude/commands/` as `.md` files. Claude Code automatically recognizes any file in that folder as a slash command. Type `/skill-name` in the chat to invoke it. No additional installation or configuration is required.

---

## Invoking a Skill

```
/skill-name [optional arguments]
```

If you provide arguments, the skill uses them as the target or topic. If you provide no arguments, the skill will prompt you for input.

---

## Skills Reference

### `/white-collar-crime`
**Expert criminal justice and corporate compliance analysis of white-collar crime.**

Produces a structured deep-dive on any corporate crime topic covering typology, federal/state statutes, deception mechanics, and regulatory jurisdiction.

```
/white-collar-crime Insider Trading
/white-collar-crime Enron Scandal
/white-collar-crime Corporate Bribery FCPA
/white-collar-crime Wire Fraud
/white-collar-crime Money Laundering
```

**Output:** `output/wcc-corporate/YYYY-MM-DD_topic-slug.md`

**Four modules:**
1. Executive Summary & Typology — scheme overview, economic motives, crime taxonomy table
2. Statutory Framework — federal statutes with exact proof elements (Wire Fraud, RICO, FCPA, SOX) + state-level overlaps (Martin Act, Delaware DGCL, CA/TX law)
3. Corruption & Deception Mechanisms — Fraud Triangle, Money Laundering 3-phase model, Bribery Payment Chain, Insider Trading flow map, governance bypass breakdown
4. Investigation & Jurisdiction — agency roles table (FBI/SEC/DOJ/FinCEN/IRS-CI/CFTC), civil vs. criminal track comparison, grand jury and whistleblower program mechanics

---

### `/white-collar-charity-crime`
**Expert analysis of white-collar crime in nonprofits, HOAs, and civic organizations.**

Analyzes fraud in charitable, civic, and residential trust contexts: fake disaster charities, HOA embezzlement, youth sports league fraud, PTA booster skimming, religious organization misappropriation.

```
/white-collar-charity-crime HOA Reserve Fund Embezzlement
/white-collar-charity-crime Fake Disaster Relief Charity
/white-collar-charity-crime Youth Sports League Treasurer Fraud
/white-collar-charity-crime PTA Booster Club Skimming
/white-collar-charity-crime Religious Organization Misappropriation
```

**Output:** `output/wcc-charity/YYYY-MM-DD_topic-slug.md`

**Four modules:**
1. Psychology & Opportunity — trust exploit mechanics, authority bias, 7-type governance failure table
2. Operational Mechanics — skimming vs. reserve larceny (5 scheme types), POS manipulation (6 methods), payroll fraud, skimming comparison table
3. Statutory Framework — Wire/Mail Fraud, 18 U.S.C. § 666, IRS 990 fraud, Corporate Transparency Act/FinCEN, RICO, state AG charity bureaus, Davis-Stirling, Florida § 720 HOA law
4. Detection & Red Flags — 15 financial red flags, 8 behavioral red flags, 5-phase forensic accounting protocol, agency referral pathway table

---

### `/white-collar-hoa-crime`
**NJ-specific prosecution framework for HOA corruption in private lake communities.**

Covers bid-rigging on lake/dam infrastructure, clubhouse cash skimming, ghost employees, reserve fund raids, and ABC liquor license abuse. Cites specific N.J.S.A. statutes with criminal penalty tiers.

```
/white-collar-hoa-crime Lake dredging bid-rigging scheme
/white-collar-hoa-crime Clubhouse tiki bar cash skimming
/white-collar-hoa-crime Reserve fund raid disguised as dam repair
/white-collar-hoa-crime Property manager ghost employees
/white-collar-hoa-crime Wedding venue off-books revenue
/white-collar-hoa-crime
```

**Output:** `output/wcc-hoa/YYYY-MM-DD_hoa-slug.md`

**Four modules:**
1. Lakeshore & Hospitality Schemes — full bid-rigging cycle (7 steps), infrastructure vulnerability table by asset type and cost, POS manipulation (6 methods), payroll fraud (5 variants), NJ DEP permit exploitation
2. NJ Statutory Violations — N.J.S.A. 2C:20-3, 2C:20-4, 2C:21-15 with full elements and grading ($75K threshold = 2nd Degree, 5–10 years), PREDFDA enforcement pathway (DCA → County Prosecutor → AG), NJ Nonprofit fiduciary duties, ABC license types and criminal penalties
3. Federal Intersections — Wire/mail fraud trigger map (AppFolio, ACH, Zelle, USPS), CTA/FinCEN BOI obligations, IRS Form 1120-H/990 fraud, Form 8300 cash reporting
4. Forensic Audit & Red Flags — 18 financial + 8 behavioral red flags, 33-step forensic procedure, full prosecutorial jurisdictional matrix

---

### `/human-osint`
**Elite OSINT profile on an individual subject using open-source and publicly available data.**

Authorized use only: licensed private investigators, law enforcement, credentialed journalists, authorized compliance teams, fraud examiners.

```
/human-osint Target Name: John Smith | Email: jsmith@example.com | Phone: 555-xxx-xxxx | Title: HOA Treasurer | Location: Morris County, NJ
/human-osint
```

**Output:** `output/human-osint/YYYY-MM-DD_subject-slug.md`

**Five modules:**
1. Core Identity Resolution — email-to-identity (Epieos, Holehe), username enumeration (WhatsMyName, Sherlock, Maigret), breach exposure mapping (HIBP, DeHashed), platform discovery across professional/social/secure/subscription platforms
2. Socio-Behavioral Graphing — 5-step social graph construction (Tier 1/2/3 contacts), interaction weight analysis, Maltego/Gephi visualization, 7-day activity heatmap, Strava/fitness route analysis, Google Maps review extraction
3. Registrations, Civil Records & Litigation — NJ Business Gateway, OpenCorporates, PACER federal court search, NJ eCourts, UCC liens, property records, all professional licensing boards (FINRA BrokerCheck, NJ Bar, NJ DCA, NMLS, FAA)
4. Geospatial & Metadata Forensics — ExifTool EXIF extraction, Jeffrey's Viewer, PDF metadata XML recovery, 5-step visual geolocation, SunCalc chronolocation, Yandex/TinEye reverse image
5. HUMINT Bridge — OSINT-to-pretext pipeline, persona congruence table (with legal limits), SUE interrogation technique, SCAN behavioral deception methodology, 5-phase funnel interview structure

---

### `/corporate-osint`
**Multi-layered entity and individual corporate intelligence investigation.**

Combines individual profiling, entity registry tracing, HOA-specific forensics, nonprofit 990 analysis, and advanced geospatial/litigation forensics into a single unified investigation report.

```
/corporate-osint Individual: John Smith, jsmith@lakeviewhoa.org | Institution: Lakeview HOA, NJ
/corporate-osint Institution: Green Valley Community Association, Morris County NJ
/corporate-osint Individual: Jane Doe, CFO | Institution: Sunrise Relief Foundation, 501(c)(3), NJ EIN: 22-xxxxxxx
/corporate-osint
```

**Output:** `output/corporate-osint/YYYY-MM-DD_subject-slug.md`

**Five modules:**
1. Individual SOCMINT — Holehe/Epieos/Maigret/WhatsMyName, HIBP/DeHashed breach exposure, institutional email on personal platform detection, 7-day behavioral heatmap, Strava route analysis
2. Corporate B2B Reconnaissance — OpenCorporates officer search, ICIJ Offshore Leaks, FinCEN CTA/BOI analysis, interlocking directorate mapping, UCC-1 lien tracing, Panjiva/ImportGenius trade manifests
3. HOA-Specific Forensics — NJ DEP permit vs. invoiced scope, Google Earth Pro satellite before/after verification, POS Z-tape reconciliation, liquor inventory variance formula, ghost employee payroll audit (5-step), NJ ABC compliance
4. Charity & Nonprofit 990 Forensics — Part VII compensation benchmarking, Schedule L self-dealing analysis, Schedule G fundraiser retention rate, 5-year trend analysis, crowdfunding vs. 990 revenue gap, reverse image fundraising verification
5. Advanced Forensics — ExifTool + Metagoofil batch metadata, Office XML tracked-change recovery, 5-step visual geolocation, SunCalc chronolocation, PACER bankruptcy SOFA analysis, SUE interrogation, SCAN deception indicators

---

### `/forensic-financials`
**Forensic accounting and fraud examination of raw financial data.**

Ingest raw financial records and run a full CFE-standard quantitative analysis: trend analysis, Benford's Law, cross-report reconciliation, and a prioritized follow-the-money roadmap.

**Accepts:** General ledgers, bank statements, IRS Form 990s, HOA balance sheets, POS cash logs, vendor invoices, accounts payable journals, special assessment records, crowdfunding totals.

```
/forensic-financials
[paste CSV, tabular ledger data, bank statement rows, 990 line items, POS Z-tapes, or AP journal]
```

**Output:** `output/financial-forensics/YYYY-MM-DD_entity-slug.md`

**Four modules:**
1. Horizontal & Vertical Analysis — period-over-period % change with anomaly thresholds by category; structural ratio analysis (food cost %, program efficiency, fundraising overhead) vs. industry benchmarks
2. Benford's Law & Digit Analysis — first and second digit Z-statistic testing (95% / 99% confidence), structuring/threshold evasion detection (evasion ratio >70% = flag), duplicate transaction detection, sequential invoice analysis, rounded-dollar frequency
3. Reconciliation & Cross-Report Discrepancy — GL-to-bank three-way match, cash receipt shortage calculation, POS Z-tape vs. deposit daily variance, vendor phantom invoice scoring, bid compliance verification, dues/crowdfunding revenue gap analysis
4. Forensic Outlook & Roadmap — master flagged transaction register (11 exception codes), aggregate loss estimate (conservative/midpoint/maximum), 10-step follow-the-money roadmap, statutory violation matrix, summary dashboard

---

### `/whistleblower-strategy`
**Multi-jurisdictional whistleblower disclosure strategy bypassing compromised local enforcement.**

Generates a complete filing strategy for reporting fraud to state and federal agencies when county-level prosecutors are compromised, with OPSEC guidance and evidence packaging templates.

```
/whistleblower-strategy HOA lake community, Morris County NJ, reserve fund embezzlement ~$400K, county prosecutor conflict of interest
/whistleblower-strategy Nonprofit charity fraud, Essex County NJ, false 990 filings, ~$200K unreported revenue
/whistleblower-strategy
```

**Output:** Not auto-saved — copy the generated strategy manually or request a file save.

**Five modules:**
1. Escalation Map & Jurisdictional Bypass — legal basis for federal jurisdiction without county referral (18 U.S.C. §§ 1341, 1343, 1344, 666, RICO), day-by-day dual-track simultaneous filing timeline
2. Federal Reporting Pathways — FBI Newark (tips.fbi.gov + in-person intake), SEC Form TCR with award structure (10–30% of sanctions >$1M), IRS Form 211 mailing to Ogden UT with award tiers (15–30% of collected proceeds >$2M), FinCEN CTA/BSA reporting
3. NJ State Agency Contacts — NJ OSC (constitutional independence, N.J.S.A. 52:15C-1), NJ AG OPIA with supersession authority (N.J.S.A. 52:17B-98), NJ DCA PREDFDA complaints, NJ ABC, NJ Division of Taxation
4. Press Asymmetry & Watchdogs — SecureDrop 6-step Tor protocol, ProPublica/NJ Advance Media/The Intercept routing, NJ Shield Law protection (N.J.S.A. 2A:84A-21), POGO/GAP watchdog contacts
5. Evidence Packaging & Source Protection — full OPSEC threat model (dedicated device, Tor/ProtonMail, burner phone), ExifTool metadata scrubbing commands, VeraCrypt encrypted USB, 8-tab indexed evidence packet structure, pre-filled Executive Summary cover letter template, retaliation protection protocol (CEPA, Dodd-Frank § 922, SOX § 806, FCA § 3730(h)), 25-item pre-submission checklist

---

### `/scan-sensitive-data`
**Scans the repository for PII, PHI, and statutory compliance risks.**

Rates findings using NIST FIPS 199 (HIGH / MODERATE / LOW). Use before any commit, PR, or public release.

```
/scan-sensitive-data
/scan-sensitive-data src/
/scan-sensitive-data check this file for leaks
```

Detects: SSNs, credit card numbers, medical record IDs, biometric data, FTC/DMCA/CFAA violations, DRM bypass patterns, credential stuffing code, and more. Located in `.github/skills/Sensitive-Scanner/SKILL.md`.

---

## Output Directory Structure

All skills (except `/whistleblower-strategy` and `/scan-sensitive-data`) automatically write a dated markdown file to the `output/` directory after completing each analysis.

```
output/
├── corporate-osint/        ← /corporate-osint reports
├── human-osint/            ← /human-osint reports
├── financial-forensics/    ← /forensic-financials reports
├── wcc-charity/            ← /white-collar-charity-crime reports
├── wcc-corporate/          ← /white-collar-crime reports
└── wcc-hoa/                ← /white-collar-hoa-crime reports
```

**File naming:** `YYYY-MM-DD_subject-slug.md`

**Each file opens with:**
```markdown
# [Report Title]
**Date:** [Full date]
**Subject:** [Entity / Person / Topic]
**Skill:** /skill-name
**Output Directory:** output/[folder]/
---
[full report follows]
```

---

## Skill Chaining (Recommended Workflow)

Skills are designed to feed into each other. The recommended investigation pipeline:

```
1. /corporate-osint       — Find who, what entities, what relationships
        ↓
2. /human-osint           — Deep profile on key individuals identified
        ↓
3. /forensic-financials   — Analyze financial records obtained
        ↓
4. /white-collar-hoa-crime       — Apply NJ HOA prosecution framework
   /white-collar-charity-crime   — Apply nonprofit prosecution framework
   /white-collar-crime           — Apply general corporate fraud framework
        ↓
5. /whistleblower-strategy       — Generate multi-jurisdictional filing strategy
```

---

## File Structure

```
.claude/
└── commands/
    ├── white-collar-crime.md
    ├── white-collar-charity-crime.md
    ├── white-collar-hoa-crime.md
    ├── human-osint.md
    ├── corporate-osint.md
    ├── forensic-financials.md
    └── whistleblower-strategy.md

.github/
└── skills/
    ├── Sensitive-Scanner/
    │   └── SKILL.md
    └── white-collar-corporate-crime/
        └── SKILL.md

output/
├── corporate-osint/
├── human-osint/
├── financial-forensics/
├── wcc-charity/
├── wcc-corporate/
└── wcc-hoa/
```

---

## Legal Disclaimer

All skills in this suite are intended for educational research, authorized compliance investigation, licensed private investigation, law enforcement support, and journalistic research on matters of public concern. No skill in this suite provides legal advice or creates an attorney-client relationship. Consult licensed legal counsel before taking any enforcement action based on outputs generated by these skills. All investigative techniques described rely exclusively on publicly available records and legally accessible data sources.
