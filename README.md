# John Gaji — Senior DevSecOps Engineer & Cloud Security Architect

> Houston, TX | [LinkedIn](https://linkedin.com/in/john-gaji/) | john.s.gaji@gmail.com | [Portfolio](https://github.com/sheyijojo/devops-portfolio)

## 📊 Impact at a Glance

| Metric | Result |
|--------|--------|
| AWS accounts managed | 10-account Organization |
| Security Hub findings reduced | 33% (159 → 106) |
| CI build time reduction | ~90% across 200+ repos |
| PR review time reduction | ~70% via AI automation |
| Engineer-hours saved/day | ~400 hrs org-wide |
| Cloud cost savings | $200+/month |
| Patch MTTR reduction | 85% (14 days → <2 days) |
| SSM associations deployed | 49 org-wide |
| S3 objects re-encrypted | 22,000+ |
| Production downtime | Zero |

---

## 🔐 Security & Compliance

### 1. AWS Security Hub Centralization — 10-Account Organization
**May 2026 | Meneses Law PLLC**

Designed and implemented centralized Security Hub architecture across AWS Organization. Designated Security-workloads account as delegated administrator, enrolled all member accounts, and enforced 3 compliance frameworks simultaneously.

- Deregistered incorrect delegated admin, re-registered `250740063095` (Security-workloads) as proper delegated administrator
- Enrolled all 9 member accounts — 100% enrollment, zero failures
- Enabled FSBP v1.0, CIS AWS Foundations Benchmark v1.4, and NIST 800-53 Rev 5 — all `READY`
- Enforced us-east-1 only posture, removed incorrect cross-region aggregator
- Configured auto-enable for all future accounts joining the organization
- Eliminated security blind spots across Production, Development, CICD, Identity, CloudTrail, and Operations accounts

**Impact:** 10 accounts under centralized monitoring (up from 0), 3 compliance frameworks enforced, future-proofed for new account onboarding

`Security Hub` `AWS Organizations` `Control Tower` `CIS Benchmarks` `NIST 800-53` `FSBP` `AWS CLI`

---

### 2. AWS Security Hardening — 10-Account Organization
**April 2026 | Meneses Law PLLC**

Led comprehensive security hardening engagement across entire AWS Organization for a law firm handling sensitive client immigration data. 53+ findings remediated with zero production downtime.

- **IAM:** Org-wide password policies, IAM Access Analyzer (4 regions), break-glass admin with hardware MFA
- **S3:** SSL-only policies on 80 buckets, centralized access logging (78 buckets), versioning with Glacier lifecycle, KMS encryption
- **EC2/EBS:** IMDSv2 on all launch templates, EBS encryption by default (4 regions), blocked public snapshot access, DLM backup policies
- **Network:** Closed default VPC security groups org-wide, NACL SSH/RDP deny rules, VPC flow logs (3 regions)
- **TLS:** Updated ALB to post-quantum resistant TLS 1.3 (`ELBSecurityPolicy-TLS13-1-2-Res-PQ-2025-09`)
- **Cost:** Decommissioned CloudStorageSec ($200+/month), deleted 47 CodeBuild projects, 39 DynamoDB tables, 29,000+ orphaned S3 objects

**Impact:** 159 → 106 findings (33% reduction), $200+/month saved, zero downtime, 22,000+ S3 objects re-encrypted

`Security Hub` `Config` `IAM` `KMS` `S3` `EC2` `VPC` `ALB` `CloudTrail` `CloudWatch` `SSM`

---

### 3. AWS Audit Manager — CIS Benchmark Compliance Pipeline
**May 2026 | Meneses Law PLLC**

Architected end-to-end compliance automation before AWS Audit Manager's April 30, 2026 new-customer cutoff deadline.

- Designated Control Tower Audit account as delegated administrator
- Deployed CIS AWS Foundations Benchmark v1.4.0 (Level 1 & 2) org-wide
- Integrated evidence collection: Config, CloudTrail, Security Hub, Evidence Finder (CloudTrail Lake)
- Updated KMS key policy to grant delegated administrator account access
- Configured SNS alerting pipeline to 5 stakeholders — validated end-to-end via AWS CLI

**Impact:** Automated continuous compliance evidence collection org-wide, met hard vendor deadline, eliminated manual audit prep

`Audit Manager` `Control Tower` `Organizations` `Config` `CloudTrail Lake` `Security Hub` `KMS` `SNS`

---

### 4. Rapid7 InsightIDR Honeypot Audit, Redesign & Expansion
**May 2026 | Meneses Law PLLC | CLI-only**

Inherited a year-old undocumented honeypot with unknown health status. Found a critical NACL gap making it completely blind to internal threats.

- Mapped full account via CLI: 3 VPCs, 11 subnets, 4 NAT gateways, Transit Gateway, 2 IPSec VPN tunnels
- Identified critical NACL gap silently dropping all internal traffic — lateral movement would never trigger an alert
- Implemented fix: 7 targeted NACL rules covering all RFC1918 and on-premises VPN CIDRs
- Deployed second honeypot to uncovered VPC, resolved multi-layer connectivity failure
- Confirmed live MITRE ATT&CK-tagged detections: Initial Access, Valid Accounts, lateral movement
- Produced full architecture reference doc + Confluence runbook — first-ever documentation

**Impact:** 2x honeypot coverage, critical detection gap closed, live MITRE ATT&CK detections confirmed

`AWS VPC` `CloudFormation` `IAM` `GuardDuty` `CloudWatch` `Rapid7 InsightIDR` `MITRE ATT&CK` `AWS CLI`

---

### 5. Rapid7 S3 Log Ingestion Remediation (Lambda)
**May 7, 2026 | Meneses Law PLLC**

Designed and deployed serverless remediation pipeline for failing Rapid7 SIEM log ingestion caused by oversized Mosyle log lines exceeding 1.4MB limit.

- Designed S3-triggered Lambda workflow for preprocessing oversized log files
- Developed Python logic to validate, split, and re-upload sanitized files to processed prefix
- Implemented recursive S3 event trigger safeguards

**Impact:** Ingestion failures eliminated, continuous SOC visibility restored, manual intervention fully automated

`AWS Lambda` `Amazon S3` `Python` `IAM` `CloudWatch` `Rapid7` `Serverless`

---

### 6. AWS SCP Architecture — Bedrock Access Unblock
**May 7, 2026 | Meneses Law PLLC**

Diagnosed and resolved Amazon Bedrock access failure on production Lambda caused by Control Tower-managed SCP.

- Traced exact blocking SCP (`GRREGIONDENY`) via AWS CLI — identified as Control Tower-managed, not safely editable
- Diagnosed secondary issue: Lambda missing `AWSLambdaVPCAccessExecutionRole`
- Created new SCP (`AllowBedrockAllUSRegions`) explicitly allowing `bedrock:*` and `bedrock-runtime:*` across all US regions
- Attached to Development OU without touching any Control Tower guardrails
- Documented full SCP hierarchy for the first time at org level

**Impact:** AI Lambda unblocked, Control Tower governance preserved, Development OU future-proofed for Bedrock

`AWS Organizations` `Control Tower` `SCPs` `Lambda` `Bedrock` `IAM` `AWS CLI`

---

### 7. Security Hub CSPM + Control Tower Governance Audit
**May 2026 | Meneses Law PLLC**

Investigated multi-account Security Hub CSPM and Control Tower governance inconsistencies across the organization.

- Audited Control Tower, Config, Security Hub CSPM, and CloudTrail baselines across governed and non-governed regions
- Diagnosed delegated administrator removal failures tied to Security Hub Central Configuration dependencies
- Mapped org-wide integrations: GuardDuty, Inspector, IAM Access Analyzer, Firewall Manager, AWS Health
- Developed remediation approach for centralized governance model

**Impact:** Root causes identified, remediation path established, future Control Tower baseline conflicts prevented

`Control Tower` `Security Hub` `AWS Config` `Organizations` `GuardDuty` `Inspector` `StackSets`

---

## ⚙️ Infrastructure, Patching & Systems Management

### 8. Centralized SSM Infrastructure — Multi-Account Organization
**May 2026 | Meneses Law PLLC**

Designed centralized AWS Systems Manager infrastructure across multi-account Organization — unified patch management, inventory, and compliance from single delegated admin account.

- Enabled Organizations trusted access for all SSM services
- Registered Ops account (`492661376591`) as SSM delegated administrator
- Deployed DHMC org-wide for automatic IAM permissions on all EC2 instances
- Configured State Manager: SSM Agent updates (14-day), inventory (12-hour), patch compliance (daily)
- Deployed 49 successful State Manager associations org-wide
- Resolved failed associations in 2 member accounts (missing IAM profiles, VPC endpoints)

**Impact:** 100% visibility across 6 accounts, 49 associations deployed, ~80% operational overhead reduction

`SSM Fleet Manager` `Patch Manager` `State Manager` `Quick Setup` `Organizations` `Control Tower` `StackSets`

---

### 9. Cross-Account SSM Automation Patching
**May 4, 2026 | Meneses Law PLLC**

Engineered org-wide cross-account patch management from scratch — zero existing framework, zero documentation.

- Custom patch baselines for Ubuntu 22.04/24.04 and Amazon Linux 2023
- SSM Automation document with STS cross-account role assumption (ExternalId)
- Resolved full IAM permission chain: `sts:AssumeRole`, `iam:PassRole`, `ssm:SendCommand`, `ssm:ListCommands`
- Deliberate architecture decision: excluded honeypots and network appliances from SSM management

**Impact:** Full patch compliance across all instances, org-wide automation, deliberate security exclusions documented

`SSM Automation` `STS` `IAM` `EC2` `CloudFormation` `Ubuntu` `Amazon Linux`

---

### 10. AWS Inspector + SSM Vulnerability Remediation Pipeline
**2026 | Meneses Law PLLC**

Automated vulnerability remediation for multi-OS EC2 fleet — eliminated 14+ day manual patching windows.

- OS-specific patch baselines for Ubuntu 22.04 and Amazon Linux 2 with auto-approval rules
- State Manager associations with `AWS-RunPatchBaseline`, maintenance windows, reboot-safe automation
- Closed-loop vulnerability tracking integrating Inspector findings with patch compliance reporting

**Impact:** 85% MTTR reduction (14 days → <2 days), 100% patch compliance in first month, 8+ hrs/week saved

`AWS Inspector` `SSM Patch Manager` `State Manager` `EC2` `CloudWatch` `Python (boto3)`

---

### 11. EC2 Disk Exhaustion — Production Incident Response
**April 30, 2026 | Meneses Law PLLC**

SSM patch job silently failing (exit code 1, no stdout). Traced through entire invocation chain — root cause was disk exhaustion, not a script bug.

- S3-backed SSM log forensics identified `/dev/root` at 100% blocking all execution
- Layered disk forensics: journald (242MB), rotated syslogs, compressed cloud-init logs
- Vacuumed journals, purged artifacts, resolved broken apt state — zero downtime
- Identified secondary IAM gap (`s3:GetObject` missing on instance profile)
- Preserved production Deepgram ML inference container throughout

**Impact:** Production restored with zero downtime, secondary security gap proactively identified

`SSM` `EC2` `Linux` `IAM` `S3` `systemd` `apt`

---

### 12. EC2 Kernel Accumulation — Remediation & Prevention
**May 2026 | Meneses Law PLLC**

Remediated 23 stale kernel packages on production EC2 creating disk pressure and CVE exposure.

- Audited `/lib/modules`, `/boot`, dpkg package states
- Refactored bash remediation script: fixed inverted logic, corrected typos, replaced if/elif with `case` statement
- Purged 23 stale `rc` entries, deployed APT config for permanent auto-removal on future upgrades

**Impact:** 23 stale kernels removed, future accumulation permanently prevented, CVE surface reduced

`EC2` `Ubuntu 22.04` `Bash` `APT` `dpkg`

---

## 🌐 Networking & Private Connectivity

### 13. MongoDB Atlas PrivateLink — Zero Public Internet Architecture
**April 22, 2026 | Meneses Law PLLC**

Architected private, zero-public-internet connectivity between MongoDB Atlas M30 and multiple AWS workloads across 3 VPCs.

- Provisioned new VPC with 2 private subnets across 2 AZs with Atlas private DNS compatibility
- Created 7 VPC endpoints: MongoDB Atlas, SQS, S3, Bedrock, EventBridge, Secrets Manager, Textract
- Migrated Lambda from public internet to fully private network path
- Fixed SG misconfiguration on Atlas PrivateLink endpoint (ports 1024-1026)
- Established Secrets Manager naming convention for multi-VPC MongoDB connectivity
- Configured cross-account S3 access to management account

**Impact:** Zero public internet exposure, full pipeline restored (SQS→Lambda→S3→Textract→Bedrock→EventBridge→MongoDB), TLS mismatch resolved

`VPC` `PrivateLink` `Lambda` `ECS` `MongoDB Atlas` `Secrets Manager` `SQS` `Bedrock` `Textract`

---

### 14. ECS/ECR Private Subnet Networking Fix
**May 7, 2026 | Meneses Law PLLC**

Diagnosed ECS image pull failures in private subnets caused by incomplete VPC endpoint dependency chain.

- Validated full endpoint chain: `ecr.api`, `ecr.dkr`, and S3 gateway endpoints
- Identified missing S3 backend dependency for ECR image layers
- Documented validated private networking pattern for ECS/ECR without public internet

**Impact:** ECS deployment rollbacks eliminated, repeatable private networking pattern established

`ECS` `ECR` `VPC Interface Endpoints` `S3 Gateway Endpoint` `Route Tables` `Security Groups`

---

### 15. GoTo Connect Webhook Ingestion Pipeline
**March 27, 2026 | Meneses Law PLLC**

Designed secure webhook ingestion pipeline for real-time GoTo Connect telephony events. Debugged multi-layer API Gateway CORS and Mock integration failure.

- Rebuilt OPTIONS method: HTTP → Mock integration with correct `{"statusCode": 200}` mapping
- Traced root cause to non-empty POST body by comparing against working Rapid7 endpoint
- Locked ALB security groups to GoTo Connect's 8 published CIDR blocks (~39,000 IPs)
- Architected ALB → ECS Fargate routing using IP-based target groups

**Impact:** Webhook passes GoTo validation, ALB restricted to GoTo-only CIDRs, reusable pattern established

`API Gateway` `ALB` `ECS Fargate` `Lambda` `Security Groups` `GoTo Connect`

---

### 16. IAM Roles Anywhere — External Container S3 Access
**2026 | Meneses Law PLLC**

Designed zero-trust S3 access architecture for containerized workloads running outside AWS.

- Evaluated IAM access keys vs OIDC vs IAM Roles Anywhere — selected Roles Anywhere for external workloads
- Designed least-privilege IAM policies scoped to required S3 actions only
- Implemented temporary credential generation pattern eliminating long-lived static credentials

**Impact:** Zero long-lived credentials, repeatable auth pattern reusable across multiple external applications

`IAM Roles Anywhere` `STS` `S3` `IAM` `Docker`

---

## 🚀 CI/CD & Developer Productivity

### 17. Docker CI Build Optimization — 200 Repositories
**2026 | Meneses Law PLLC**

- GitHub Actions layer caching (`type=gha,mode=max`), Dockerfile layer ordering fix
- Consolidated 30+ stale Dependabot PRs, fixed SonarQube scanning wrong project on every PR

**Impact:** ~90% build time reduction, ~400 engineer-hours/day saved org-wide

`GitHub Actions` `Docker` `SonarQube` `Dependabot` `FastAPI` `AWS ECS`

---

### 18. Claude/Bedrock AI Code Review Pipeline
**2026 | Meneses Law PLLC**

Integrated Claude (Anthropic) via Amazon Bedrock with GitHub Copilot agents for automated PR reviews across 200+ repos.

**Impact:** ~70% PR review cycle time reduction

`Amazon Bedrock` `Claude (Anthropic)` `GitHub Copilot` `GitHub Actions`

---

### 19. ECS-to-SQS Webhook Pipeline Fix
**March 26, 2026 | Meneses Law PLLC**

Debugged silent ECS-to-SQS message loss — application receiving webhooks but never forwarding to Lambda.

- Traced credential resolution through `awsAssumedRole.ts` — identified `IS_LOCAL` env var misconfiguration
- Added targeted debug logging to confirm credential path in production

**Impact:** Silent message loss eliminated, ECS → SQS → Lambda pipeline fully restored

`ECS` `SQS` `Lambda` `IAM` `STS` `CloudWatch` `AWS SDK v3 (TypeScript)`

---

## 🛑 Incident Response

### 20. AWS WAF 403 Production Incident
**March 18, 2026 | Meneses Law PLLC**

Production 403 on `/courses` API — traced to WAF `SizeRestrictions_BODY` rule in under 1 hour.

- Identified block at infrastructure layer (`awselb/2.0`), not application layer
- Tuned WAF rule from `BLOCK` to `COUNT` preserving monitoring while restoring traffic

**Impact:** Production API restored, WAF tuning documented for future large-payload APIs

`AWS WAF` `ALB` `ECS Fargate` `Cognito`

---

### 21. SolarWinds Observability Bug — Terminated ASG Instances
**May 7, 2026 | Meneses Law PLLC**

Identified critical vendor bug causing terminated ASG instances to appear as active unhealthy entities in real-time dashboards.

- Designed controlled test with full instance lifecycle documentation
- Proved active polling of deleted resources via "Last Seen" timestamp analysis
- Compiled technical evidence package forcing vendor engineering escalation (previously claimed "expected behavior")

**Impact:** Vendor opened internal investigation, ~10+ phantom alerts eliminated daily, escalation methodology documented

`AWS Auto Scaling` `EC2` `CloudTrail` `SolarWinds Observability`

---

## 🤖 AI & Innovation

### 22. AI-Powered Resume & Career Management System
**2026 | Personal Project**

Claude-powered career intelligence system — daily brag book entries auto-converted to quantified resume bullets, STAR talking points, and role-targeted resume versions.

**Impact:** Resume always current, zero manual writing, interview-ready at all times

`Claude (Anthropic)` `Prompt Engineering` `Career Systems`

---

## ☁️ Cloud Infrastructure

### 23. GPU Compute Cluster Infrastructure on AWS
**2021–2023 | AirDove Logistics**

Multi-node GPU clusters on EC2 P-series with Kubernetes, Terraform IaC with EFA networking, nvidia-smi + DCGM monitoring.

**Impact:** ~30% GPU utilisation improvement, ~40% intra-cluster latency reduction

`Kubernetes` `AWS EC2 P-series` `Terraform` `EFA` `DCGM` `nvidia-smi`

---

## 🛠️ Tech Stack

```
Cloud:          AWS (Organizations, Control Tower, 25+ services) | Azure | GCP
Security:       Security Hub | GuardDuty | Audit Manager | Inspector | Rapid7 InsightIDR
                SonarQube | CodeQL | MITRE ATT&CK | CIS Benchmarks | NIST 800-53
                WAF | PrivateLink | IAM Roles Anywhere | SCP Architecture
IaC:            Terraform | CloudFormation | Ansible | SSM Automation
CI/CD:          GitHub Actions | Jenkins | CircleCI | Azure Pipelines
Containers:     Docker | Kubernetes (CKA) | ECS | ECR | Fargate
AI/ML:          Amazon Bedrock | Claude (Anthropic) | GitHub Copilot | Kiro Agentic DevOps
Observability:  Datadog | Prometheus | Grafana | CloudWatch | SolarWinds | VPC Flow Logs
Networking:     VPC | Transit Gateway | PrivateLink | VPN | NACLs | ALB | WAF | EFA
Scripting:      Python | Bash | PowerShell | TypeScript | YAML
Databases:      MongoDB Atlas | MySQL | PostgreSQL | DynamoDB | Oracle
```

---

## 📜 Certifications

| Certification | Level |
|--------------|-------|
| AWS Certified Solutions Architect | Professional |
| AWS Certified Generative AI Developer | Professional |
| AWS Certified Security | Specialty |
| AWS Certified Solutions Architect | Associate |
| AWS Certified Developer | Associate |
| AWS Certified CloudOps Engineer | Associate |
| AZ-104: Microsoft Azure Administrator | — |
| Google Associate Cloud Engineer | — |
| Google Cloud Digital Leader | — |

---

## 📅 Project Timeline

| Date | Project | Key Metric |
|------|---------|------------|
| May 2026 | Security Hub Centralization | 10 accounts, 3 frameworks, 100% enrollment |
| May 2026 | AWS Audit Manager CIS Pipeline | Org-wide CIS v1.4.0, deadline met |
| May 7, 2026 | Rapid7 S3 Log Ingestion Lambda | SOC visibility restored, fully automated |
| May 7, 2026 | Bedrock SCP Architecture | AI Lambda unblocked, governance preserved |
| May 7, 2026 | ECS/ECR Private Subnet Fix | Deployment rollbacks eliminated |
| May 7, 2026 | SolarWinds Bug Investigation | Vendor escalation forced, phantom alerts eliminated |
| May 4, 2026 | Cross-Account SSM Patching | Full compliance, org-wide automation |
| May 2026 | Centralized SSM Infrastructure | 49 associations, 6 accounts, 80% overhead reduction |
| May 2026 | Inspector + SSM Vuln Pipeline | 85% MTTR reduction, 8hrs/week saved |
| May 2026 | Kernel Accumulation Remediation | 23 kernels removed, prevention deployed |
| May 1, 2026 | Rapid7 Honeypot Audit & Expansion | 2x coverage, NACL gap fixed, MITRE detections |
| Apr 30, 2026 | EC2 Disk Exhaustion Response | Root cause found, prod restored |
| Apr 22, 2026 | MongoDB Atlas PrivateLink | Zero public internet, 7 endpoints |
| April 2026 | AWS Security Hardening | 33% findings reduction, $200+/mo saved |
| Mar 27, 2026 | GoTo Connect Webhook Pipeline | Webhook validated, ALB locked |
| Mar 26, 2026 | ECS-to-SQS Pipeline Fix | Silent message loss eliminated |
| Mar 18, 2026 | AWS WAF 403 Incident | Production API restored |
| 2026 | Docker CI Optimization | 90% build reduction, ~400 hrs/day saved |
| 2026 | Claude/Bedrock AI Code Review | 70% PR review reduction, 200+ repos |
| 2026 | IAM Roles Anywhere | Zero long-lived credentials |
| 2021–2023 | GPU Cluster Infrastructure | 30% utilisation up, 40% latency down |

---

*Last updated: May 2026 | 23 projects documented*
