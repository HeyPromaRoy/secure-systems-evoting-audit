# Secure Systems Audit – Rust-Based E-Voting Platform

This repository documents a security audit conducted as **Phase III (Audit & Analysis)** of a Secure Systems Engineering course project at **The City College of New York (CCNY)**. The work focuses on identifying design, implementation, and operational security flaws in a Rust-based electronic voting system through structured threat modeling and adversarial analysis.

📄 **Primary Artifact:** [Audit Security Analysis on E-Voting System – CCNY – TEAM ThermoRust (PDF)](./Audit%20Security%20Analysis%20on%20E-Voting%20System%20-%20CCNY%20-%20TEAM%20Thermorust.pdf)

**Team:** ThermoRust  
**Analysts:** Proma Roy, Md Ariful Islam Fahim, Hsiao-Yin Peng, Tahsinur Rahman  
**Course:** EE 17701 – Secure Systems Engineering  
**Institution:** The City College of New York (CCNY)  

---

## Project Scope

The audit was performed on a pre-existing Rust codebase provided as part of a controlled academic exercise. The system had undergone intentional adversarial modification prior to analysis. The objective was to evaluate the system’s resilience against insider and external threats, assess compliance with secure-by-design principles, and propose effective mitigations.

The assessment covered:

* Authentication and authorization logic
* Cryptographic practices
* Input validation and error handling
* Build and dependency integrity
* Data storage and privacy guarantees
* System availability and fault tolerance

---

## Methodology

This repository intentionally emphasizes **analysis and outcomes** rather than implementation details. No source code excerpts or configuration snippets are included, as the focus of this phase was system evaluation rather than development.

The analysis followed established security engineering practices:

* **Threat Modeling:** STRIDE-based analysis of core system components and trust boundaries
* **Adversary Analysis:** Insider and external attacker capability modeling
* **Static Analysis:** Dependency inspection and source-level review
* **Runtime Testing:** Fault injection and invalid input execution
* **Binary & Build Analysis:** Inspection of compiled artifacts and build pipeline behavior
* **Standards Mapping:** OWASP Top 10 (2021) and CWE classification for each finding

---

## System Overview

The evaluated system consisted of:

* Rust-based CLI application
* SQLite database backend
* Role-based workflows (Admin, District Official, Voter)
* Authentication and audit logging modules
* Build scripts and auxiliary binaries

Architecture and execution flow diagrams are included in the accompanying presentation materials.

---

## Key Findings (Summary)

The audit identified multiple high-impact security issues, including but not limited to:

* Broken access control enabling unauthorized actions
* Weak and improper cryptographic practices
* Hardcoded and improperly managed credentials
* Plaintext storage and logging of sensitive PII
* SQL injection vulnerabilities
* Denial-of-Service conditions via unhandled panics
* Malicious build artifacts compromising supply-chain integrity
* Violations of ballot secrecy and voter anonymity

Each finding was mapped to OWASP Top 10 categories and corresponding CWE identifiers, with concrete mitigation strategies proposed.

---

## Mitigation Strategy

For each identified vulnerability, remediation recommendations were developed, including:

* Role-based access enforcement
* Modern password hashing with unique salts
* Application-level encryption for sensitive data
* Secure input handling and error recovery
* Dependency upgrades and CI-based security checks
* Build pipeline hardening and artifact validation
* Privacy-preserving ballot design

The mitigations emphasize defense-in-depth and least-privilege principles.

---

## CIA Triad Assessment

**Confidentiality:** Failed
Sensitive voter data and ballots were exposed through design and implementation flaws.

**Integrity:** Failed
Insufficient access controls and malicious build logic enabled undetectable manipulation.

**Availability:** Failed
Uncaught exceptions and malformed inputs allowed trivial denial-of-service attacks.

---

## Artifacts Included

* Security audit presentation (PDF/PPT)
* Threat model and system flow diagrams
* Vulnerability classification and mitigation documentation

---

## Responsible Disclosure Statement

The analyzed source code and binaries are intentionally **not included** in this repository.
The codebase was provided for academic audit purposes and contained intentionally injected vulnerabilities and malicious components. To adhere to responsible disclosure practices, academic policy, and security ethics, only analysis, findings, and remediation strategies are documented here.

---

## Academic Context

This project was completed as part of a graduate-level Secure Systems Engineering course and reflects applied security analysis practices used in real-world system audits.
