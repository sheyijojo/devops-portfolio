# John Gaji — Senior DevSecOps Engineer & Cloud Security Engineer

> Interest: In ML Engineering

> Houston, TX | [LinkedIn](https://linkedin.com/in/john-gaji/) | john.s.gaji@gmail.com

## 📊 Impact at a Glance

| Metric | Result |
|--------|--------|
| AWS accounts managed | 10+ -account Organization |
| Security Hub findings reduced | 33% (159 → 106) |
| CI build time reduction | ~90% across 200+ repos |
| PR review time reduction | ~70% via AI automation |
| Engineer-hours saved/day | ~400 hrs (org-wide) |
| Cloud cost savings | $200+/month |
| Production downtime during changes | Zero |

---

## 🔐 Security & Compliance Projects

### 1. Rapid7 InsightIDR Honeypot Audit, Redesign & Expansion
**May 2026 | AWS Security Account | CLI-only**

Inherited a year-old undocumented honeypot with unknown health status. Mapped entire AWS security account from scratch and identified a critical gap that made the honeypot completely ineffective.

**What I did:**
- Reverse-engineered undocumented CloudFormation deployment running since April 2025 with no runbook
- Mapped full account: 3 VPCs, 11 subnets, 4 NAT gateways, Transit Gateway, 2 IPSec VPN tunnels, 10+ security groups
- Identified critical NACL gap silently dropping all inbound traffic from internal networks — lateral movement would never trigger an alert
- Implemented fix: 7 targeted NACL rules covering all RFC1918 and on-premises VPN CIDRs
- Deployed second honeypot to previously uncovered VPC via CloudFormation — diagnosed multi-layer connectivity failure (missing peering route, SG egress restriction, pcap4j interface binding)
- Confirmed live MITRE ATT&CK-tagged detections: Initial Access, Valid Accounts, lateral movement
- Investigated GuardDuty `Recon:EC2/Portscan` finding, traced to benign Cisco vMX routing
- Tuned CloudWatch anomaly detection alarm 2→3 std deviations to reduce false positive noise
- Produced full architecture reference doc + Confluence-ready operational runbook

`AWS VPC` `CloudFormation` `IAM` `GuardDuty` `CloudWatch` `Rapid7 InsightIDR` `MITRE ATT&CK` `AWS CLI`

---

### 2. AWS Security Hardening — 10-Account Organization
**2026 | Meneses Law PLLC**

Led comprehensive security initiative across entire AWS Organization — 33% reduction in non-compliant findings with zero production downtime.

**Key deliverables:**
- **IAM:** Org-wide password policies, IAM Access Analyzer (4 regions), break-glass admin with hardware MFA
- **Encryption:** SSL-only policies on 80 S3 buckets, KMS on CloudTrail + 18 SNS topics, EBS encryption by default, re-encrypted 22,000+ S3 objects resolving production frontend outage
- **Network:** Closed default VPC security groups org-wide, NACL SSH/RDP deny rules, VPC flow logs (3 regions), blocked EBS snapshot public access
- **TLS:** Updated ALB SSL policy to post-quantum resistant `ELBSecurityPolicy-TLS13-1-2-Res-PQ-2025-09`
- **Logging:** Centralized S3 access logging (78 buckets), 365-day retention on security-critical log groups, deleted 248 orphaned log groups, Route53 query logging on 5 hosted zones
- **Cost:** Decommissioned CloudStorageSec ($200+/month saved), deleted 47 CodeBuild projects, 39 DynamoDB tables, 29,000+ orphaned S3 objects

`Security Hub` `AWS Config` `IAM` `KMS` `S3` `CloudTrail` `VPC` `ALB` `Route53` `CloudWatch`

---

### 3. AWS Audit Manager — CIS Benchmark Compliance Pipeline
**May 2026 | Meneses Law PLLC**

Architected end-to-end compliance automation before service maintenance mode deadline.

**What I built:**
- Delegated administrator model with AWS Organizations trusted access for automatic account enrollment
- CIS AWS Foundations Benchmark v1.4.0 (Level 1 & 2) scoped org-wide
- Evidence collection integrated across AWS Config, CloudTrail, and Security Hub
- Evidence Finder backed by CloudTrail Lake
- SNS notification pipeline to 5 stakeholders
- Validated full pipeline via AWS CLI

`AWS Audit Manager` `Control Tower` `Organizations` `Config` `CloudTrail Lake` `Security Hub` `SNS`

---

## ⚙️ Infrastructure & Patching Projects

### 4. Cross-Account SSM Automation Patching Architecture
**May 4, 2026 | Meneses Law PLLC**

Engineered org-wide cross-account patch management from scratch — zero existing framework, zero documentation.

**Architecture decisions:**
- Created custom patch baselines for Ubuntu 22.04/24.04 and Amazon Linux 2023
- Built maintenance window targeting all hub-managed Linux instances across member accounts
- Developed SSM Automation document with STS cross-account role assumption (ExternalId)
- Iteratively resolved full IAM permission chain: `sts:AssumeRole`, `iam:PassRole`, `ssm:SendCommand`, `ssm:ListCommands`
- Onboarded Security Workloads account (8 EC2 instances including Rapid7 tooling, Cisco vMX, InsightIDR honeypots)
- **Deliberate exclusion:** Made architecture decision to exclude honeypots and network appliances from SSM management
- Verified DHMC auto-enrollment for future instances

`SSM` `STS` `IAM` `EC2` `CloudFormation` `Ubuntu` `Amazon Linux`

---

### 5. EC2 Disk Exhaustion — Incident Response
**April 30, 2026 | Production | Meneses Law PLLC**

SSM patch job silently failing with exit code 1, no stdout. Rather than assuming script bug, traced through entire SSM invocation chain.

**Diagnosis chain:**
- Queried `aws ssm list-command-invocations --details` to retrieve S3-backed stderr/stdout log paths
- Root cause: `/dev/root` at 100% capacity (6.8G) — silently blocking all script execution
- Layered disk forensics: `du -sh` across `/var`, `/usr`, `/snap`, `/opt`
- Isolated culprits: systemd-journald (242MB), rotated syslogs, compressed cloud-init logs
- Audited running kernel with `uname -r` to safely target stale images
- Preserved production Deepgram ML inference container throughout all operations
- Diagnosed secondary `403 Forbidden` — missing `s3:GetObject` on instance profile, flagged for remediation

`SSM` `EC2` `Linux` `IAM` `S3` `systemd` `apt`

---

## 🚀 CI/CD & Developer Productivity Projects

### 6. Docker CI Build Optimization — 200 Repositories
**2026 | Meneses Law PLLC**

90% CI build time reduction across entire 200+ repo organization.

**What I fixed:**
- Implemented GitHub Actions layer caching (`type=gha,mode=max`) on FastAPI/AWS ECS project
- Fixed Dockerfile layer ordering to cache compilation steps correctly
- Consolidated 30+ stale Dependabot PRs into grouped updates
- Fixed SonarQube workflow bug scanning wrong project on every PR

**Impact:** ~400 engineer-hours saved per day org-wide

`GitHub Actions` `Docker` `SonarQube` `Dependabot` `FastAPI` `AWS ECS`

---

### 7. Claude/Bedrock AI Code Review Pipeline
**2026 | Meneses Law PLLC**

Integrated Claude (Anthropic) via Amazon Bedrock with GitHub Copilot agents to automate PR reviews at scale.

**What I built:**
- Connected Claude via Bedrock API into CI/CD pipeline as automated code reviewer
- Deployed agents on GitHub Copilot for PR-level analysis
- Automated detection of security vulnerabilities, logic errors, and style violations pre-merge
- Rolled out across 200+ repositories

**Impact:** ~70% reduction in PR review cycle time

`Amazon Bedrock` `Claude (Anthropic)` `GitHub Copilot` `GitHub Actions` `CI/CD`

---

## 🤖 AI & Innovation Projects

### 8. AI-Powered Resume & Career Management System
**2026**

Built a Claude-powered career intelligence system that eliminates manual resume writing.

**What it does:**
- Captures daily engineering achievements in structured brag book format
- Auto-generates quantified resume bullets with metrics
- Produces STAR-formatted interview talking points
- Maintains role-targeted resume versions (DevSecOps, Cloud Security, Platform Engineering)
- Tracks running project inventory with impact metrics

`Claude (Anthropic)` `Prompt Engineering` `Career Systems`

---

## ☁️ Cloud Infrastructure Projects

### 9. GPU Compute Cluster Infrastructure on AWS
**2021–2023 | AirDove Logistics**

Engineered and operated multi-node GPU compute clusters for distributed ML training and inference.

**What I built:**
- Multi-node GPU clusters on EC2 P-series using Kubernetes
- GPU device plugin configuration, node affinity, taints/tolerations, resource quotas
- Terraform IaC provisioning with placement groups and EFA networking
- nvidia-smi + DCGM fleet health monitoring and bottleneck diagnostics

**Impact:** ~30% GPU utilisation improvement, ~40% intra-cluster latency reduction

`Kubernetes` `AWS EC2 (P-series)` `Terraform` `EFA` `DCGM` `nvidia-smi` `GPU`

---

## 🛠️ Tech Stack

```
Cloud:        AWS (Organizations, Control Tower, 20+ services) | Azure | GCP
Security:     Security Hub | GuardDuty | Audit Manager | Rapid7 InsightIDR
              SonarQube | CodeQL | MITRE ATT&CK | CIS Benchmarks
IaC:          Terraform | CloudFormation | Ansible
CI/CD:        GitHub Actions | Jenkins | CircleCI | Azure Pipelines
Containers:   Docker | Kubernetes (CKA) | ECS | ECR
AI/ML:        Amazon Bedrock | Claude | GitHub Copilot | Kiro Agentic DevOps
Observability:Datadog | Prometheus | Grafana | CloudWatch | VPC Flow Logs
Scripting:    Python | Bash | PowerShell | YAML
Networking:   VPC | Transit Gateway | VPN | NACLs | Route Tables | EFA
```

---

## 📜 Certifications

- AWS Certified Generative AI Developer – Professional  
- AWS Certified Security – Specialty
- AWS Certified Solutions Architect – Associate
- AWS Certified Developer – Associate
- AWS Certified CloudOps Engineer – Associate
- AZ-104: Microsoft Azure Administrator
- Google Associate Cloud Engineer
- Google Cloud Digital Leader

---

*Last updated: May 2026*
