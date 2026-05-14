# John Gaji — Senior DevSecOps Engineer & Cloud Security Engineer

> Houston, TX | [LinkedIn](https://linkedin.com/in/john-gaji/) | john.s.gaji@gmail.com | [Portfolio](https://github.com/sheyijojo/devops-portfolio)

## 📊 Impact at a Glance

| Metric | Result |
|--------|--------|
| AWS accounts managed | 10-account Organization |
| Azure DevOps & GitHub Enterprise Adminstration| 
| Security Hub findings reduced | 33% (159 → 106) |
| CI build time reduction | ~90% across 200+ repos |
| PR review time reduction | ~70% via AI automation |
| Engineer-hours saved/day | ~400 hrs org-wide |
| Cloud cost savings | $200+/month |
| Patch MTTR reduction | 85% (14 days → <2 days) |
| SSM associations deployed | 49 org-wide |
| S3 objects re-encrypted | 22,000+ |
| LocalStack cost reduction | 75% ($13,080 → $3,204/yr) |
| Cert tracking effort reduction | ~90% via automation |
| Production downtime | Zero |

---

## 💼 Current Role

**Senior DevSecOps Engineer** | Meneses Law PLLC | Jan 2024 – Present | Houston, TX

Full-stack cloud security, DevOps automation, platform engineering, and enterprise tools administration — spanning AWS, Azure, CI/CD pipelines, identity federation, monitoring, and developer platform governance.

---

## 🖥️ Platform & Tools Administration

> Part of the Senior DevSecOps Engineer role — enterprise developer and security platform administration covering identity federation, monitoring, local cloud testing, CI/CD governance, and network infrastructure.

### A1. GitHub SSO / SAML Configuration & Identity Federation
**2024–2026 | Meneses Law PLLC**

Configured and maintained GitHub Organization SSO using SAML 2.0 federation with Azure Active Directory, enforcing centralized identity governance across all engineering repositories.

- Configured SAML SSO between GitHub Organization and Azure AD — enforced SSO requirement for all members
- Managed SCIM provisioning for automatic user lifecycle (provision/deprovision) from Azure AD to GitHub
- Administered GitHub Organization membership, team structure, repository access, and role assignments
- Diagnosed and resolved SAML assertion failures, certificate expiration issues, and SSO enforcement gaps
- Rotated SAML signing certificates with zero authentication downtime across engineering teams
- Enforced OAuth app policies and GitHub App permissions to restrict third-party access to org resources

**Impact:** Centralized identity governance for all engineering access, eliminated manual user provisioning, zero SSO downtime during certificate rotations

`GitHub Enterprise` `SAML 2.0` `Azure Active Directory` `SCIM` `OAuth` `SSO` `GitHub Actions`

---

### A2. Azure Active Directory & Enterprise Application Management
**2024–2026 | Meneses Law PLLC**

Administered Azure AD enterprise applications, service principals, and identity workflows supporting secure application integrations across cloud and SaaS platforms.

- Managed enterprise application registrations, service principal credentials, and API permission scopes
- Configured Conditional Access policies restricting application access based on user, device, and location context
- Administered App Roles, group assignments, and claims mapping for SAML and OIDC application integrations
- Rotated client secrets and certificates for service principals with zero disruption to dependent workloads
- Reviewed and remediated risky sign-in alerts and identity protection findings in Azure AD Identity Protection
- Managed cross-tenant application access for vendor integrations (MongoDB Atlas, SolarWinds, Rapid7)

**Impact:** Secure enterprise application governance across all SaaS and cloud platforms, eliminated standing credentials via rotation automation

`Azure Active Directory` `Enterprise Applications` `Conditional Access` `SAML` `OIDC` `Service Principals` `Azure AD Identity Protection`

---

### A3. SolarWinds Observability — Platform Administration & Monitoring
**2024–2026 | Meneses Law PLLC**

Administered SolarWinds Observability platform for infrastructure health monitoring, alerting, and AWS resource visibility across cloud and on-premises environments.

- Configured SolarWinds AWS integration for EC2, ECS, RDS, ALB, and Lambda metric ingestion
- Built custom dashboards for infrastructure health, deployment status, and security event visibility
- Configured alert policies and notification channels (email, Slack) for infrastructure anomalies and threshold breaches
- Tuned anomaly detection thresholds to reduce false positive noise (CloudWatch vMX metric: 2σ → 3σ)
- Identified and escalated critical vendor bug — terminated ASG instances appearing as active entities in real-time dashboards, forced engineering escalation with documented evidence package
- Managed agent deployments and SolarWinds collector configurations across managed EC2 instances

**Impact:** Improved infrastructure observability org-wide, eliminated ~10+ phantom alerts/day from vendor bug, tuned alerting to reduce false positive noise

`SolarWinds Observability` `AWS EC2` `ECS` `CloudWatch` `Alert Management` `Infrastructure Monitoring`

---

### A4. LocalStack — Platform Adoption & License Management
**2024–2026 | Meneses Law PLLC**

Led LocalStack platform evaluation, licensing negotiation, and adoption strategy for AWS infrastructure testing and Terraform workflow validation.

- Evaluated LocalStack Ultimate licensing proposal vs. actual team requirements (3 engineers vs. 10-seat proposal)
- Negotiated with vendor — reduced annual cost from $13,080 to $3,204/year (75% reduction) by eliminating unnecessary SSO/security add-ons
- Configured LocalStack environment for Terraform module testing, AWS service emulation, and CI/CD pipeline validation
- Established LocalStack workflows for S3, Lambda, SQS, DynamoDB, and IAM local testing before AWS deployment
- Documented LocalStack setup, configuration patterns, and team onboarding guidelines
- Integrated LocalStack into GitHub Actions CI workflows for pre-deployment infrastructure validation

**Impact:** 75% licensing cost reduction ($9,876/year saved), enabled Terraform and CI/CD testing at sustainable cost, established repeatable local AWS testing workflows

`LocalStack` `Terraform` `AWS Emulation` `GitHub Actions` `CI/CD` `Cost Optimization`

---

### A5. Azure DevOps — Administration & Pipeline Governance
**2024–2026 | Meneses Law PLLC**

Administered Azure DevOps organization settings, pipeline governance, and developer access controls across engineering projects.

- Managed Azure DevOps organization-level settings: project policies, pipeline permissions, and agent pool configurations
- Configured branch policies across Azure Repos: required reviewers, build validation, comment resolution, and merge strategies
- Administered service connections for AWS, Azure, and GitHub integrations — rotated credentials and validated OIDC federation
- Managed self-hosted agent pool deployments on EC2 — configured agent registration, capability tags, and maintenance schedules
- Enforced pipeline security: restricted pipeline access to specific repositories, validated YAML template inheritance
- Reviewed and remediated Azure DevOps audit logs for unauthorized access attempts and policy violations
- Configured variable groups and Azure Key Vault integration for secure secret management in pipelines

**Impact:** Standardized pipeline governance across Azure DevOps projects, eliminated standing service connection credentials via OIDC, improved audit visibility

`Azure DevOps` `Azure Pipelines` `Azure Repos` `Service Connections` `OIDC` `Key Vault` `Agent Pools`

---

### A6. SonarQube — Platform Administration & DevSecOps Integration
**2024–2026 | Meneses Law PLLC**

Administered SonarQube platform end-to-end — from installation and database migration to quality gate enforcement and enterprise licensing management.

- Administered SonarQube projects, quality gates, quality profiles, and user/group permissions
- Configured GitHub Actions integration for PR decoration and branch analysis across 28+ TypeScript repositories
- Diagnosed and fixed SonarQube misconfiguration scanning wrong project on every PR across 200+ repositories
- Pinned SonarQube GitHub Action to commit SHA resolving supply chain risk (SonarQube S7637)
- Migrated SonarQube database from local PostgreSQL to AWS RDS — pg_dump/restore with zero data loss
- Diagnosed SonarQube 2026 crash-loop traced to Elasticsearch disk watermark cascade shutdown
- Managed LOC licensing capacity — identified 499,995/500K threshold risk, coordinated enterprise upgrade to 1M LOC preventing CI/CD disruption

**Impact:** Uninterrupted code quality scanning across all repos, zero data loss on DB migration, CI/CD disruption prevented at 499,995 LOC threshold

`SonarQube` `GitHub Actions` `PostgreSQL` `AWS RDS` `Elasticsearch` `SAST` `DevSecOps`

---

### A7. Cisco vMX — Network Infrastructure Administration
**2024–2026 | Meneses Law PLLC**

Administered Cisco vMX virtual network appliances deployed in AWS for enterprise VPN and network routing across cloud environments.

- Managed Cisco vMX configuration, routing tables, and VPN tunnel health across AWS VPC environments
- Monitored vMX network performance and investigated GuardDuty findings related to vMX routing behavior
- Identified and documented benign GuardDuty `Recon:EC2/Portscan` finding caused by Cisco vMX routing internal traffic to honeypot IPs — prevented unnecessary incident escalation
- Tuned CloudWatch anomaly detection on vMX `NetworkOut` metric (2σ → 3σ) to reduce false positive alerting noise
- Excluded Cisco vMX from SSM patch management — deliberate architecture decision to preserve network appliance stability
- Coordinated vMX connectivity with Transit Gateway, VPC peering, and on-premises IPSec VPN tunnel management

**Impact:** Stable enterprise VPN connectivity, false positive GuardDuty findings documented and triaged, vMX excluded from automated patching to prevent network disruption

`Cisco vMX` `AWS VPC` `Transit Gateway` `GuardDuty` `CloudWatch` `IPSec VPN`

---

## 🔐 Security & Compliance Projects

### 1. AWS Security Hub Centralization — 10-Account Organization
**May 2026 | Meneses Law PLLC**

Designed and implemented centralized Security Hub architecture across AWS Organization — 10 accounts, 3 compliance frameworks, 100% member enrollment.

- Deregistered incorrect delegated admin, re-registered Security-workloads account (`250740063095`)
- Enrolled all 9 member accounts — 100% enrollment, zero failures
- Enabled FSBP v1.0, CIS AWS Foundations Benchmark v1.4, and NIST 800-53 Rev 5
- Enforced us-east-1 only posture, configured auto-enable for future accounts

**Impact:** 10 accounts under centralized monitoring (up from 0), 3 frameworks enforced, future-proofed

`Security Hub` `AWS Organizations` `Control Tower` `CIS` `NIST 800-53` `FSBP`

---

### 2. AWS Security Hardening — 10-Account Organization
**April 2026 | Meneses Law PLLC**

53+ findings remediated across IAM, S3, EC2, networking, logging — zero production downtime.

- SSL-only policies on 80 S3 buckets, KMS on CloudTrail + 18 SNS topics, re-encrypted 22,000+ S3 objects
- Post-quantum TLS 1.3 ALB policy, IMDSv2 on all EC2 launch templates, EBS encryption by default (4 regions)
- Deleted 248 orphaned log groups, 47 CodeBuild projects, 39 DynamoDB tables, 29,000+ orphaned S3 objects

**Impact:** 159 → 106 findings (33% reduction), $200+/month saved, zero downtime

`Security Hub` `Config` `IAM` `KMS` `S3` `EC2` `VPC` `ALB` `CloudTrail`

---

### 3. AWS Audit Manager — CIS Benchmark Compliance Pipeline
**May 2026 | Meneses Law PLLC**

Org-wide CIS v1.4.0 (L1 & L2) compliance automation before service maintenance deadline.

- Delegated administrator model, Config + CloudTrail Lake + Security Hub evidence collection
- SNS alerting to 5 stakeholders, validated end-to-end via AWS CLI

**Impact:** Automated compliance evidence org-wide, hard deadline met

`Audit Manager` `Control Tower` `Organizations` `CloudTrail Lake` `Security Hub` `SNS`

---

### 4. Rapid7 InsightIDR Honeypot Audit, Redesign & Expansion
**May 2026 | Meneses Law PLLC | CLI-only**

Inherited year-old undocumented honeypot — found critical NACL gap making it blind to internal threats.

- Mapped 3 VPCs, 11 subnets, 4 NAT gateways, Transit Gateway, 2 IPSec VPN tunnels
- Implemented 7 NACL rules covering RFC1918 + VPN CIDRs, deployed second honeypot
- Confirmed live MITRE ATT&CK detections: Initial Access, Valid Accounts, lateral movement
- Produced first-ever architecture doc + Confluence runbook

**Impact:** 2x coverage, critical gap closed, live detections confirmed

`VPC` `CloudFormation` `GuardDuty` `Rapid7 InsightIDR` `MITRE ATT&CK` `AWS CLI`

---

### 5. Rapid7 S3 Log Ingestion Remediation (Lambda)
**May 7, 2026 | Meneses Law PLLC**

Serverless fix for Rapid7 SIEM ingestion failures caused by Mosyle log lines exceeding 1.4MB.

- S3-triggered Lambda split oversized lines, re-uploaded to processed prefix, recursive trigger safeguards

**Impact:** Ingestion failures eliminated, SOC visibility restored, fully automated

`Lambda` `S3` `Python` `Rapid7` `Serverless`

---

### 6. AWS SCP Architecture — Bedrock Access Unblock
**May 7, 2026 | Meneses Law PLLC**

Unblocked AI Lambda from Bedrock via SCP engineering — preserved Control Tower governance intact.

- Traced blocking SCP (`GRREGIONDENY`) via CLI, created `AllowBedrockAllUSRegions` SCP
- Attached to Development OU without modifying any Control Tower guardrails

**Impact:** AI Lambda unblocked, governance preserved, first-ever SCP hierarchy documented

`Organizations` `Control Tower` `SCPs` `Lambda` `Bedrock` `IAM`

---

### 7. SEC-T01 AWS Config Compliance Remediation Sprint
**2026 | Meneses Law PLLC**

Phased remediation of high-risk Config findings across Dev, Sandbox, Operations, Security, and Production.

- Prioritized public exposure, encryption gaps, overpermissive SGs, IAM hygiene
- Validated via Config Aggregator + CloudWatch before Production rollout

**Impact:** Critical findings reduced, phased workflow established, zero production impact

`AWS Config` `Security Hub` `IAM` `CloudWatch` `Organizations`

---

### 8. Secrets Rotation & Certificate Expiration Automation
**May 2025 | Meneses Law PLLC**

Automated SAML/TLS certificate monitoring across AWS accounts — shifted from reactive to proactive.

- Lambda + Config + Secrets Manager inventory, CloudWatch 30/15/7-day alarms
- SAML certificate validation integrated into CI/CD pipelines

**Impact:** ~90% manual tracking reduction, zero authentication outage risk

`Lambda` `Secrets Manager` `Config` `CloudWatch` `SAML` `GitHub Actions`

---

### 9. Security Hub CSPM + Control Tower Governance Audit
**May 2026 | Meneses Law PLLC**

Diagnosed multi-account CSPM and Control Tower governance drift — built remediation path.

- Audited Config baselines, diagnosed delegated admin removal failures
- Mapped GuardDuty, Inspector, IAM Access Analyzer, Firewall Manager integrations

**Impact:** Root causes identified, future baseline conflicts prevented

`Control Tower` `Security Hub` `Config` `GuardDuty` `Inspector`

---

## ⚙️ Infrastructure, Patching & Systems Management

### 10. Centralized SSM Infrastructure — Multi-Account Organization
**May 2026 | Meneses Law PLLC**

49 State Manager associations deployed org-wide — unified patch, inventory, and compliance visibility.

- DHMC org-wide, SSM Agent updates (14-day), inventory (12-hour), patch compliance (daily)
- Resolved failed associations in 2 member accounts, onboarded Security Workloads account

**Impact:** 100% visibility across 6 accounts, ~80% overhead reduction

`SSM` `Organizations` `Control Tower` `State Manager` `Quick Setup`

---

### 11. Cross-Account SSM Automation Patching
**May 4, 2026 | Meneses Law PLLC**

Built org-wide patching from scratch — custom baselines, STS cross-account role assumption.

- Ubuntu 22.04/24.04 + AL2023 baselines, full IAM chain resolved
- Excluded honeypots and Cisco vMX — deliberate architecture decision

**Impact:** Full patch compliance, org-wide automation, deliberate exclusions documented

`SSM Automation` `STS` `IAM` `EC2` `CloudFormation`

---

### 12. AWS Inspector + SSM Vulnerability Remediation Pipeline
**2026 | Meneses Law PLLC**

Automated CVE remediation — eliminated 14+ day manual patching windows.

- OS-specific baselines, State Manager + maintenance windows, closed-loop Inspector integration

**Impact:** 85% MTTR reduction (14 days → <2 days), 8+ hrs/week saved

`Inspector` `SSM Patch Manager` `State Manager` `EC2` `Python (boto3)`

---

### 13. AWS Control Tower Landing Zone Unblock
**Oct 2025 | Meneses Law PLLC**

Resolved all Control Tower pre-check failures blocking multi-account governance adoption.

- Purged Config recorders/delivery channels across all regions, removed conflicting delegated admins
- Recreated AWSControlTowerExecution role with correct trust relationships

**Impact:** Landing zone unblocked, governance-ready multi-account structure restored

`Control Tower` `Organizations` `Config` `IAM` `StackSets` `AWS CLI`

---

### 14. Multi-Account Terraform Architecture
**Feb 2024 | Meneses Law PLLC**

Enterprise-ready IaC pattern — modular stacks, isolated state, OIDC federation.

- Environment/account/region-based organization, S3 + DynamoDB state isolation per stack
- GitHub OIDC role assumption — zero static credentials in CI

**Impact:** Reduced blast radius, improved deployment safety, scalable for future account expansion

`Terraform` `GitHub Actions` `OIDC` `S3` `DynamoDB` `KMS` `Organizations`

---

### 15. EC2 Disk Exhaustion — Production Incident Response
**April 30, 2026 | Meneses Law PLLC**

SSM patch job silently failing — traced to 100% disk exhaustion, not a script bug.

- S3-backed SSM log forensics, layered disk forensics (journald 242MB, syslogs, cloud-init)
- Vacuumed, purged, fixed broken apt state — zero downtime, secondary IAM gap identified

**Impact:** Production restored, zero downtime, IAM gap proactively flagged

`SSM` `EC2` `Linux` `IAM` `systemd` `apt`

---

### 16. EC2 Kernel Accumulation Remediation
**May 2026 | Meneses Law PLLC**

Removed 23 stale kernels, deployed permanent APT auto-removal config.

**Impact:** CVE surface reduced, future accumulation permanently prevented

`EC2` `Ubuntu 22.04` `Bash` `APT` `dpkg`

---

### 17. SonarQube PostgreSQL → AWS RDS Migration
**Apr 4, 2026 | Meneses Law PLLC**

Migrated SonarQube from local PostgreSQL to managed RDS — zero data loss.

- pg_dump/restore, RDS provisioned with VPC/SG isolation, JDBC reconfigured

**Impact:** Single-node dependency eliminated, managed backups enabled

`RDS` `PostgreSQL` `EC2` `VPC` `SonarQube`

---

### 18. Lambda Chromium Layer Architecture
**May 11, 2026 | Meneses Law PLLC**

Versioned Lambda layer strategy for headless browser automation across dev/prod accounts.

- chromium-v143 layer published, S3-backed, ARNs managed via SSM Parameter Store

**Impact:** Lambda package size limits eliminated, repeatable upgrade pattern established

`Lambda Layers` `S3` `SSM Parameter Store` `Puppeteer` `TypeScript`

---

## 🌐 Networking & Private Connectivity

### 19. MongoDB Atlas PrivateLink — Zero Public Internet Architecture
**April 22, 2026 | Meneses Law PLLC**

7 VPC endpoints across 3 VPCs — zero public internet for all MongoDB and AWS service traffic.

- SQS, S3, Bedrock, EventBridge, Secrets Manager, Textract, Atlas PrivateLink
- Full pipeline restored: SQS→Lambda→S3→Textract→Bedrock→EventBridge→MongoDB

**Impact:** Zero public exposure, TLS mismatch resolved, repeatable multi-VPC pattern

`VPC` `PrivateLink` `Lambda` `ECS` `MongoDB Atlas` `Secrets Manager`

---

### 20. ECS/ECR Private Subnet Networking Fix
**May 7, 2026 | Meneses Law PLLC**

Diagnosed and fixed incomplete VPC endpoint chain causing ECS image pull failures.

- Validated ecr.api + ecr.dkr + S3 gateway dependency chain, documented pattern

**Impact:** Deployment rollbacks eliminated, private networking pattern established

`ECS` `ECR` `VPC Endpoints` `Route Tables` `Security Groups`

---

### 21. GoTo Connect Webhook Ingestion Pipeline
**March 27, 2026 | Meneses Law PLLC**

Debugged multi-layer API Gateway CORS failure blocking GoTo webhook registration.

- OPTIONS method rebuilt (HTTP→Mock), POST body fix, ALB locked to GoTo CIDRs (~39K IPs)

**Impact:** Webhook validated, ALB restricted, reusable ingestion pattern established

`API Gateway` `ALB` `ECS Fargate` `Lambda` `GoTo Connect`

---

### 22. IAM Roles Anywhere — External Container S3 Access
**2026 | Meneses Law PLLC**

Zero-trust S3 auth for external containerized workloads — eliminated long-lived credentials.

**Impact:** Zero static credentials, reusable pattern for future external integrations

`IAM Roles Anywhere` `STS` `S3` `Docker`

---

### 23. Azure Cross-Region VNet Peering
**May 13, 2026 | Meneses Law PLLC**

Resolved Azure cross-region VM connectivity blocker — VM NIC cross-region attachment unsupported.

- Designed Global VNet Peering solution, enabled cross-region traffic over Azure backbone

**Impact:** VM redeployment eliminated, cross-region connectivity established

`Azure VNet` `Global VNet Peering` `Azure VM` `Azure Networking`

---

## 🚀 CI/CD & Developer Productivity

### 24. AI TypeScript PR Review Pipeline — 28 Repositories
**May 7, 2026 | Meneses Law PLLC**

Claude Sonnet 4.6 via Bedrock reviews every PR in 60 seconds across 28 TypeScript repos.

- GitHub Actions + OIDC + tsc/ESLint + boto3, zero static AWS credentials
- All actions SHA-pinned (SonarQube S7637), branches rebased on origin/main
- Recovered from base-branch defect via git commit-tree plumbing under lock constraints

**Impact:** 28x PR review coverage, 60-sec structured reviews, zero static creds

`Bedrock` `Claude` `GitHub Actions` `OIDC` `TypeScript` `ESLint` `Python`

---

### 25. GitHub Branch Protection Automation
**May 7, 2026 | Meneses Law PLLC**

Programmatic branch protection enforcement via GitHub REST API — org-wide, zero manual config.

- Required PR approvals, SonarQube/CI checks, linear history, admin enforcement, auto-delete merged branches

**Impact:** Manual config eliminated, force pushes prevented, reusable GitOps pattern

`GitHub Actions` `GitHub REST API` `SonarQube` `CI/CD`

---

### 26. Docker CI Build Optimization — 200 Repositories
**2026 | Meneses Law PLLC**

- GitHub Actions layer caching (type=gha,mode=max), Dockerfile fix, SonarQube misconfiguration repaired

**Impact:** ~90% build time reduction, ~400 engineer-hours/day saved

`GitHub Actions` `Docker` `SonarQube` `Dependabot` `ECS`

---

### 27. Claude/Bedrock AI Code Review Pipeline
**2026 | Meneses Law PLLC**

- Claude via Bedrock + GitHub Copilot agents across 200+ repos, security/logic/style issues pre-merge

**Impact:** ~70% PR review cycle reduction

`Bedrock` `Claude` `GitHub Copilot` `GitHub Actions`

---

### 28. EC2 Self-Hosted Runner + Cognito + MongoDB CI/CD
**June 2025 | Meneses Law PLLC**

- Self-hosted runner in private VPC, automated Cognito group + MongoDB permission sync on every SPA deploy

**Impact:** ~80% provisioning effort reduction, zero configuration drift

`GitHub Actions` `EC2` `VPC` `Cognito` `MongoDB` `Python`

---

### 29. Rapid7 InsightConnect S3 Webhook Fix
**2026 | Meneses Law PLLC**

- Resolved AuthorizationHeaderMalformed errors from improper SigV4 Content-Length handling

**Impact:** SOC automation pipeline unblocked, reusable webhook ingestion pattern

`Rapid7 InsightConnect` `S3` `AWS SigV4` `IAM`

---

## 🛑 Incident Response & Forensics

### 30. AWS WAF 403 Production Incident
**March 18, 2026 | Meneses Law PLLC**

- Traced 403 to WAF SizeRestrictions_BODY, tuned BLOCK→COUNT preserving monitoring

**Impact:** Production API restored in <1 hour

`AWS WAF` `ALB` `ECS Fargate` `Cognito`

---

### 31. ECS-to-SQS Webhook Pipeline Fix
**March 26, 2026 | Meneses Law PLLC**

- Traced silent message loss to IS_LOCAL env var misconfiguration causing wrong IAM role assumption

**Impact:** ECS→SQS→Lambda pipeline restored, silent message loss eliminated

`ECS` `SQS` `Lambda` `IAM` `AWS SDK v3 (TypeScript)`

---

### 32. ECS Fargate IAM Chain Fix
**March 2026 | Meneses Law PLLC**

- Fixed GitHub OIDC → ECS task role → cross-account S3/Secrets Manager chain
- Resolved iam:PassRole, STS trust policies, resource scoping (bucket vs bucket/*)

**Impact:** CI/CD deployments restored, hardcoded credentials eliminated

`ECS` `IAM` `STS` `Secrets Manager` `GitHub OIDC`

---

### 33. ECS Cross-Role S3 Bridge Fix
**Feb 2025 | Meneses Law PLLC**

- Diagnosed AccessDenied on S3CrossAccountBridgeRolePROD, fixed trust policy + resource scoping

**Impact:** Production S3 access restored, zero downtime

`ECS` `IAM` `STS` `S3`

---

### 34. AWS Payment Cryptography Alert Investigation
**May 13, 2026 | Meneses Law PLLC**

- Multi-region CloudTrail forensics (ap-northeast-1/3), validated all activity as AWS-managed service roles

**Impact:** Account compromise ruled out, unnecessary escalation prevented

`CloudTrail` `IAM` `Security Hub` `Trusted Advisor`

---

### 35. SSM Patch Scan vs Install Investigation
**March 9, 2026 | Meneses Law PLLC**

- Confirmed AWS-RunPatchBaseline in Scan mode via CloudTrail — no unauthorized installations

**Impact:** Escalation prevented, patch behavior documented

`SSM` `CloudTrail` `EC2` `Linux`

---

### 36. SolarWinds Observability Vendor Bug
**May 7, 2026 | Meneses Law PLLC**

- Proved terminated ASG instances being actively polled — forced vendor engineering escalation

**Impact:** Phantom alerts eliminated, vendor opened internal investigation

`SolarWinds` `AWS ASG` `CloudTrail` `EC2`

---

### 37. SonarQube Crash-Loop Diagnosis
**2023 | Meneses Law PLLC**

- Correlated SonarQube + Elasticsearch + systemd logs — root cause: ES disk watermark cascade shutdown

**Impact:** Misdiagnosis prevented, targeted EBS remediation path identified

`SonarQube` `Elasticsearch` `EC2` `EBS` `systemd`

---

## 🤖 AI & Innovation

### 38. Deepgram AI Engine — Self-Hosted Deployment (mTLS)
**Dec 2025 | Meneses Law PLLC**

- Resolved NVIDIA driver kernel incompatibility (575→580), established mTLS cert chain
- ALB routing, multi-account DNS, 10-stream GPU capacity confirmed

**Impact:** Production AI engine live, zero CPU fallback

`EC2` `ALB` `Route53` `Docker` `NVIDIA` `mTLS` `ACM`

---

### 39. GPU Container Runtime Fix (L4/Ubuntu 24.04)
**Nov 2025 | Meneses Law PLLC**

- Restored nvidia-container-runtime on Ubuntu 24.04, eliminated CUDA initialization failures

**Impact:** CPU fallback eliminated, GPU-ready Docker runtime documented

`EC2` `NVIDIA L4` `Docker` `CUDA` `Ubuntu 24.04`

---

### 40. GPU Compute Cluster Infrastructure on AWS
**2021–2023 | AirDove Logistics**

- Multi-node GPU clusters on EC2 P-series, Kubernetes, Terraform IaC with EFA networking
- nvidia-smi + DCGM fleet monitoring

**Impact:** ~30% GPU utilisation improvement, ~40% latency reduction

`Kubernetes` `EC2 P-series` `Terraform` `EFA` `DCGM`

---

### 41. Lambda@Edge CloudFront Referer Validation
**Aug 2025 | Meneses Law PLLC**

- Enforce allow-list for portal.meneses.law at CDN edge, fail-closed redirects globally

**Impact:** 100% portal entry enforcement at CloudFront edge

`Lambda@Edge` `CloudFront` `TypeScript`

---

### 42. AI-Powered Resume & Career Management System
**2026 | Personal Project**

- Claude-powered brag book → quantified resume bullets, STAR talking points, role-targeted versions

**Impact:** Always current, zero manual writing effort

`Claude (Anthropic)` `Prompt Engineering`

---

## 💰 Cost Optimization

### 43. LocalStack Licensing Negotiation
**March 3, 2026 | Meneses Law PLLC**

- Identified 10-seat overprovisioning for 3-engineer team, eliminated unnecessary SSO add-ons
- Negotiated $13,080/yr → $3,204/yr

**Impact:** 75% cost reduction ($9,876/year saved)

`LocalStack` `Vendor Management` `Cost Optimization`

---

### 44. SonarQube LOC Capacity Planning
**May 2026 | Meneses Law PLLC**

- Identified 499,995/500K LOC risk, coordinated enterprise upgrade to 1M LOC

**Impact:** CI/CD disruption prevented, capacity planning process established

`SonarQube` `DevSecOps Governance` `SAST`

---

## 🛠️ Tech Stack

```
Cloud:          AWS (Organizations, Control Tower, 25+ services) | Azure | GCP
Security:       Security Hub | GuardDuty | Audit Manager | Inspector | Rapid7 InsightIDR
                SonarQube | CodeQL | MITRE ATT&CK | CIS | NIST 800-53 | WAF | PrivateLink
IaC:            Terraform | CloudFormation | Ansible | SSM Automation
CI/CD:          GitHub Actions | Azure Pipelines | Jenkins | CircleCI
Containers:     Docker | Kubernetes (CKA) | ECS | ECR | Fargate
AI/ML:          Amazon Bedrock | Claude (Anthropic) | GitHub Copilot | Kiro | Deepgram
Observability:  Datadog | Prometheus | Grafana | CloudWatch | SolarWinds | VPC Flow Logs
Identity:       Azure AD | SAML 2.0 | OIDC | SCIM | IAM Roles Anywhere | STS
Networking:     VPC | Transit Gateway | PrivateLink | VPN | NACLs | ALB | WAF | EFA
Scripting:      Python | Bash | PowerShell | TypeScript | YAML
Databases:      MongoDB Atlas | PostgreSQL | MySQL | DynamoDB | Oracle
Tools:          LocalStack | SonarQube | SolarWinds | Cisco vMX | Azure DevOps
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
| Certified Kubernetes Administrator (CKA) | — |
| AZ-104: Microsoft Azure Administrator | — |
| Google Associate Cloud Engineer | — |
| Google Cloud Digital Leader | — |

---

## 📅 Project Timeline

| Date | Project | Metric |
|------|---------|--------|
| May 13, 2026 | AWS Governance & Platform Standards | Terraform modules, ECS CI/CD |
| May 13, 2026 | AWS Payment Cryptography Investigation | Compromise ruled out |
| May 13, 2026 | Azure Cross-Region VNet Peering | VM redeployment eliminated |
| May 11, 2026 | Lambda Chromium Layer | Multi-account, SSM-managed |
| May 7, 2026 | AI TypeScript PR Review (28 repos) | 60-sec reviews, zero static creds |
| May 7, 2026 | GitHub Branch Protection Automation | Org-wide, zero manual config |
| May 2026 | SonarQube LOC Capacity Planning | 499,995→1M LOC |
| May 2026 | Security Hub Centralization | 10 accounts, 3 frameworks |
| May 2026 | AWS Audit Manager CIS Pipeline | Org-wide, deadline met |
| May 4, 2026 | Cross-Account SSM Patching | Org-wide compliance |
| May 1, 2026 | Rapid7 Honeypot Audit & Expansion | 2x coverage, MITRE detections |
| Apr 30, 2026 | EC2 Disk Exhaustion Response | Prod restored, zero downtime |
| Apr 22, 2026 | MongoDB Atlas PrivateLink | Zero public internet, 7 endpoints |
| Apr 4, 2026 | SonarQube PostgreSQL → RDS | Zero data loss |
| April 2026 | AWS Security Hardening | 33% findings, $200+/mo saved |
| Mar 27, 2026 | GoTo Connect Webhook Pipeline | Webhook validated |
| Mar 18, 2026 | AWS WAF 403 Incident | Production restored <1hr |
| Mar 2026 | ECS Fargate IAM Chain Fix | OIDC→ECS→cross-account |
| Mar 3, 2026 | LocalStack Licensing Negotiation | 75% cost reduction |
| Dec 2025 | Deepgram AI Engine (mTLS) | GPU live, 10-stream capacity |
| Nov 2025 | GPU Container Runtime Fix | CPU fallback eliminated |
| Oct 2025 | Control Tower Landing Zone Unblock | Governance restored |
| Aug 2025 | Lambda@Edge CloudFront Validation | 100% portal enforcement |
| Jun 2025 | EC2 Runner + Cognito + MongoDB CI/CD | 80% provisioning reduction |
| May 2025 | Secrets Rotation & Cert Automation | 90% manual effort reduction |
| Feb 2025 | ECS Cross-Role S3 Bridge Fix | Zero downtime |
| Feb 2024 | Multi-Account Terraform Architecture | Modular, OIDC, state isolated |
| 2026 | Docker CI Optimization | 90% build reduction |
| 2026 | Claude/Bedrock AI Code Review | 70% PR review reduction |
| 2026 | IAM Roles Anywhere | Zero long-lived credentials |
| 2021–2023 | GPU Cluster Infrastructure | 30% utilisation up |

---

*Last updated: May 2026 | 44 projects documented | 2 concurrent role tracks*
