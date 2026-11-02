# Awesome-Identity-Threat-Detection-Response-ITDR

## Top Identity Threat Detection & Response (ITDR) Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**  

*Focused on Identity Attack Path Analysis, Behavioral Anomaly Detection & Self-Hosted ITDR Tooling*  

**Last updated: November 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Identity Threat Detection & Response (ITDR)**. These tools enable organizations to detect and respond to identity-based attacks—credential theft, privilege escalation, lateral movement, and MFA manipulation—before adversaries can establish persistence or reach critical systems.



**Examples** include CrowdStrike Falcon Identity Protection, Silverfort, Microsoft Entra ID Protection, SentinelOne Singularity Identity, Authomize, Vectra AI, BeyondTrust, Semperis, Tenable Identity Exposure, and Spera Security (the category leaders).



**Open-source emphasis**: ITDR is a domain where the **commercial market is mature and consolidating**, but open-source tooling is **genuinely emerging at the detection and attack-path layers**. **Authomize's Open-ITDR** is the most structured open-source effort—a framework with an OpenITDR Query API, community connectors, and automated remediation playbooks, though its GitHub activity has slowed (last push over a year ago) . **BloodHound Community Edition** is the standout for identity attack path analysis—a graph-based tool that reveals hidden privilege relationships and unintended access paths across AD and Azure environments . **AI-Driven-IAM-Anomaly-Detection** provides a research-grade implementation of behavioral anomaly detection for IAM logs, using per-identity Markov chains and tail-percentile risk scoring . The critical caveat: **no open-source project matches the real-time inline blocking** of Silverfort (runtime authentication firewall)  or the **unified endpoint + identity telemetry** of CrowdStrike Falcon —open-source tools focus on visibility and attack path discovery rather than live prevention.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [SaaS/Hosted Platforms](#saas-products)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **[CrowdStrike Falcon Identity Protection](https://www.crowdstrike.com/)**  

  Unified ITDR combining endpoint and identity telemetry; AI-powered behavioral detection, lateral movement prevention, and risk-based MFA enforcement. Protects AD, Entra ID, and Okta, with coverage across 150+ SaaS applications . Forrester TEI study reports 310% ROI . **Best for organizations wanting unified endpoint + identity protection** with a single agent and console.



- **[Silverfort](https://www.silverfort.com/)**  

  Identity security platform with **patented Runtime Access Protection (RAP)** —integrates natively with IAM infrastructure to enforce controls at runtime, blocking malicious authentications as they happen. Features: **Identity-first incident response**, **service account protection**, **ransomware and lateral movement prevention**, **passwordless PAM**, and **AI agent identity security** . **Best for organizations wanting inline, real-time identity threat prevention** without replacing existing IAM.



- **[Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/entra/id-protection/overview-identity-protection)**  

  Native ITDR within Microsoft Entra; continuously detects risky sign-ins (anonymous IP, password spray, leaked credentials) and feeds risk signals to Conditional Access or SIEM. Provides **risk detections, risky sign-ins, and risky users** reports, with automated remediation via risk-based policies or manual review . **Best for Microsoft 365/Entra-centric organizations** wanting native identity risk detection without additional tooling.



- **[SentinelOne Singularity Identity](https://www.sentinelone.com/)**  

  ITDR integrated into SentinelOne's Singularity platform; combines identity threat detection with autonomous EDR response for unified protection.



- **[Semperis (via Cohesity)](https://www.cohesity.com/)**  

  Identity resilience platform with ITDR for **AD and Entra ID**; continuously inspects identity posture against 200+ indicators of exposure, detects malicious changes (even when logging is off), and **automatically rolls back changes** before attackers exploit them. Provides clean recovery and identity forensics . **Best for organizations prioritizing AD/Entra resilience and recovery**.



- **[Vectra AI](https://www.vectra.ai/)**  

  AI-driven hybrid cloud threat detection and response covering identity, network, and cloud; **Attack Signal Intelligence** correlates attacker TTPs for prioritization.



- **[BeyondTrust](https://www.beyondtrust.com/)**  

  Identity security platform fusing **PAM, ITDR, CIEM, and remote support**; acquired Entitle (2026) for JIT access and modern IGA.



- **[Tenable Identity Exposure](https://www.tenable.com/)**  

  AD security monitoring and attack path analysis; **CAUTION**: CVE-2026-106126 (command injection in AD Events Listener allowing SYSTEM-level RCE from a low-privileged account) was reported in October 2026 . Verify patch status before deployment.



- **[Spera Security](https://www.spera.io/)**  

  Identity security posture management platform; **acquired by Okta** (December 2023, $100M–$130M valuation) for identity-driven breach prevention .



## Open-Source GitHub Projects



### Attack Path Analysis (BloodHound CE)



- **[BloodHound Community Edition](https://github.com/SpecterOps/BloodHound)**  

  The **leading open-source identity attack path analysis tool** (Apache 2.0, SpecterOps). Uses **graph theory** to reveal hidden and unintended relationships across identity and access management systems; supports AD and Azure environments via SharpHound and AzureHound collectors, with OpenGraph extending analysis to diverse identity platforms . **Best for red/blue teams** wanting to discover and mitigate privilege escalation paths—but it is visibility and analysis, not real-time prevention.



### ITDR Frameworks & Playbooks (Open-ITDR)



- **[Authomize Open-ITDR](https://github.com/authomize/Open-ITDR)**  

  An **open framework for the ITDR community** with an OpenITDR Query API for pulling identity context, community connectors for data ingestion from SaaS/IaaS/on-premises sources, and **automated remediation playbooks** (e.g., protecting compromised Okta users, remediating over-privilege in AWS) . **Caveat**: GitHub activity has slowed—last push over a year ago . **Best for organizations building custom ITDR pipelines**—but it is a framework, not a maintained platform.



### Behavioral Anomaly Detection (Research)



- **[AI-Driven-IAM-Anomaly-Detection](https://github.com/keyfive5/AI-Driven-IAM-Anomaly-Detection)**  

  A research-grade **IAM anomaly detection system** (Python) using **per-identity Markov chains** for behavioral surprisal, **tail-percentile risk scoring** (not probability—risk 57 ≈ oddest 1% of events), and **rules as floor not cap** (rules catch known-bad like `cloudtrail:StopLogging` regardless of statistical novelty) . Demonstrates measurable improvements: switching from averaging to weighted tail-max moved average precision from 0.50 to 0.85. **Best for security engineers** wanting a reference implementation of behavioral ITDR—but it is a research project, not production-ready.



### AD Security Assessment Pipelines (Cocytus)



- **[Cocytus (CSIRT-MU)](https://gitlab.ics.muni.cz/CSIRT-MU-PUBLIC/threat-management/activedirectory/cocytus)**  

  A Python-based **orchestration pipeline for AD security assessment**; coordinates **SharpHound, PingCastle, and GPOZaurr** to gather AD data, normalize/enrich it, and upload to BloodHound CE . **Windows-only** (collectors are Windows binaries); Linux mode is testing-only. **Best for AD administrators** wanting automated data collection for attack path analysis—but it feeds BloodHound rather than replacing it.



### Additional Strong Open-Source Options



- **idryx** — Open-source **Identity Security Graph** (Apache-2.0) unifying humans, service accounts, keys, and AI agents; detects excessive privilege and anomalous behavior, with alert delivery to Slack, webhooks, or OTLP . **Best for teams wanting a graph-based identity security layer**—but it is newer and less community-validated.

- **Bloodtrail** — Python CLI for AD attack path analysis with BloodHound import, query library, and attack chain detection (Exchange WriteDACL → DCSync, etc.) . **Best for penetration testers**—but it is offensive tooling, not defensive ITDR.



**Frameworks for building custom systems**: For **attack path discovery**, BloodHound CE is the mature standard . For **ITDR playbooks and connectors**, Open-ITDR provides a framework (accepting slowed maintenance) . For **behavioral anomaly detection research**, AI-Driven-IAM-Anomaly-Detection demonstrates the pattern . For **AD data collection automation**, Cocytus . **No open-source project matches the real-time inline blocking** of Silverfort  or the **unified endpoint + identity telemetry** of CrowdStrike —choose based on whether you need visibility (BloodHound), behavioral research (AI-Driven-IAM), or a framework (Open-ITDR).



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- ITDR platforms handling identity telemetry must comply with organizational security policies and privacy regulations; **self-hosted solutions place full responsibility for tuning, integration maintenance, and data accuracy on the operator**.

- **Open-source ITDR is emerging but fundamentally limited compared to commercial platforms**—BloodHound provides attack path analysis , and Open-ITDR provides a framework , but **no open-source project matches the real-time inline blocking** of Silverfort  or the **unified endpoint + identity correlation** of CrowdStrike . **Tenable Identity Exposure has a known critical CVE** (October 2026) . Choose based on whether you need visibility (BloodHound), behavioral research (AI-Driven-IAM), or a framework (Open-ITDR).

- Verify license terms for commercial use; BloodHound uses Apache 2.0 , Open-ITDR is open-source , and AI-Driven-IAM-Anomaly-Detection is open-source .



---



**Made for identity security architects, SOC analysts, and organizations choosing their ITDR strategy.**  

Let's make identity threat detection more open at the visibility and analysis layer, but with clear eyes about the real-time inline prevention gaps that commercial platforms still fill.
