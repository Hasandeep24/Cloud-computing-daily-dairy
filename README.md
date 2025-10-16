# Cloud-computing-daily-dairy
# AWS-VPC-CloudFormation-Project-Diary

📚 **Project Overview:**  
Automated, modular AWS VPC setup using CloudFormation.  
**Goal:** Create a secure, scalable, and reusable network infrastructure for deploying apps on AWS.  
**Duration:** 4 Weeks (28 Days)  
**Tech Stack:** AWS CloudFormation · Amazon VPC · EC2 · Subnets · IGW · NAT GW · Route Tables · Security Groups · YAML  
**Focus:** Full infra-as-code automation, public/private subnet design, secure routing, modular architecture, cost-aware deployment.

---

# 🛠️ Technologies Mastered

| Technology      | Concepts Covered                                       | Proficiency     | Days   |
|-----------------|-------------------------------------------------------|-----------------|--------|
| AWS CloudFormation | IaC, Templates (YAML), Stack Automation            | Advanced        | 10     |
| Amazon VPC      | Network Isolation, Custom CIDR, Multi-AZ Segments     | Advanced        | 6      |
| EC2             | Instance Launch, Public/Private Placement             | Intermediate    | 4      |
| Subnets         | AZ Mapping, Public vs Private, Route Table Association| Advanced        | 5      |
| Internet Gateway| IGW Attachment, Secure Outbound Setup                 | Advanced        | 2      |
| NAT Gateway     | Private Subnet Internet, EIP, Scalable Protection     | Intermediate    | 2      |
| Route Tables    | Routing Logic, Public/Private Networking              | Advanced        | 2      |
| Security Groups & NACL | Instance/Subnet-level Traffic Control, Best Practices | Advanced        | 2      |
| CLI & Console   | Stack Validation, Resource Inspection                 | Intermediate    | 2      |
---

# 🚀 Major Features & Functionality

1. **Automated VPC Creation:**  
   Repeatable, one-click deployment of entire VPC infra with public/private subnets, IGW, NAT GW, route tables.

2. **Custom CIDR Block Assignment:**  
   User-defined IP ranges for VPC, subnets (IPv4/IPv6 support).

3. **Public and Private Subnets:**  
   Public for internet-facing apps; private for backend/data services. Multi-AZ for high availability.

4. **Internet Gateway Configuration:**  
   IGW attached for public subnet outbound/inbound.

5. **Secure Private Subnet Internet (NAT Gateway):**  
   Private subnets route external connections via NAT Gateway and Elastic IP, blocking direct inbound.

6. **Robust Routing Logic:**  
   Route tables with explicit mapping for subnets; custom rules for IGW and NAT traffic.

7. **Scalable and Modular Design:**  
   Easily extendable template (add EC2s, RDS, ELB); YAML allows modular refactoring.

8. **Security Groups & NACLs:**  
   Granular traffic controls at instance/subnet levels for max isolation and compliance.

---

# 📆 4-Week Progress Timeline

| Week   | Highlights                               | Key Topics/Modules                       |
|--------|------------------------------------------|------------------------------------------|
| 1      | Cloud, VPC, AZ, Subnet Fundamentals      | Networking Core, CIDR, Security Concepts |
| 2      | Architecture, CloudFormation Template    | Modular Resource Design, YAML Structure  |
| 3      | Deployment, Stack Validation, Troubleshooting | Resource Tests, Routing Checks, CLI Success |
| 4      | Documentation, Reflection, Future Scope  | Verification, Challenges, Key Learnings  |

---

# 📋 Sample Daily Entries

---

## Day 1 - 2: Cloud Fundamentals & AWS Exploration

📌 **Topics Covered:**  
- Cloud models (IaaS, PaaS, SaaS), AWS intro.  
- VPC, subnets, AZ mapping basics.

💻 **What I Did:**  
- Set up initial AWS Free Tier account.
- Explored AWS Console: VPCs, Subnets, EC2, Security, IGW.

🧠 **Reflections:**  
Understanding isolation and security in VPC made later networking setup easier.

---

## Day 3 - 4: Architecture Planning

📌 **Topics Covered:**  
- Multi-AZ VPC design for high availability.
- Security isolation: public/private subnet concepts.

💻 **What I Did:**  
- Sketched logical VPC diagrams (ASCII/network).
- Defined subnet CIDR ranges, mapped to AZs.
- Outlined security group requirements.

🧠 **Reflections:**  
A strong architecture upfront avoids painful redesigns and errors in automation.

---

## Day 5 - 7: CloudFormation Template Scaffold

📌 **Topics Covered:**  
- YAML basics: param, resources, outputs.
- Infra modularization for repeatable deployment.

💻 **What I Did:**  
- Wrote skeleton template: VPC, subnets, IGW.
- Planned resource dependencies (VPC > Subnets > IGW > NAT > Route Tables).

🧠 **Reflections:**  
CloudFormation’s dependency management drastically reduced manual order errors.

---

## Day 8 - 11: Public/Private Subnets, Routing, IGW/NAT

📌 **Topics Covered:**  
- Detailed subnet resource blocks.
- Internet Gateway and public route table setup.
- NAT Gateway: Elastic IP, private route table logic.

💻 **What I Did:**  
- Implemented two public and two private subnets, across two AZs using !GetAZs for dynamic deployment.
- Created IGW, attached to VPC, routed public subnet traffic via IGW.
- Created NAT Gateway in public subnet, associated EIP, routed private subnet traffic via NAT.

🧠 **Reflections:**  
Modular YAML gave huge flexibility to tweak/expand. Routing configuration most error-prone—dynamic AZ selection solved region issues.

---

## Day 12 - 14: Security Hardening & Verification

📌 **Topics Covered:**  
- Security Group, NACL logic for isolation and least-privilege.
- Subnet-to-route table association validation.

💻 **What I Did:**  
- Security Groups for HTTP/SSH from specific IP, tight lockdown for backend.
- NACL entries for subnet-level defense.
- CLI/Console checks: VPC, IGW, NAT, routes, security.

🧠 **Reflections:**  
Testing all paths (inbound+outbound) in public/private subnets taught the real difference between SG and NACL.

---

## Day 15 - 19: Stack Deployment & Troubleshooting

📌 **Topics Covered:**  
- Stack creation using AWS Console & CLI.
- Error analysis (routing, AZ mismatch, YAML syntax fixes).

💻 **What I Did:**  
- Used `aws cloudformation validate-template` for syntax.
- Deployed stack; monitored create events.  
- Debugged: subnet-route mismatches, NAT Gateway placement, EIP association, against CloudFormation docs/logs.

🧠 **Reflections:**  
CLI event logs are gold for troubleshooting. Learned to never hardcode AZs, always use dynamic functions.

---

## Day 20 - 22: Resource Testing

📌 **Topics Covered:**  
- EC2 launch in public/private subnets.
- Connectivity (SSH, ping, outbound downloads).

💻 **What I Did:**  
- Launched EC2 in public subnet: confirm direct internet SSH.
- Launched in private subnet: confirmed outbound internet via NAT GW, no inbound.

🧠 **Reflections:**  
NAT Gateway test is the final proof that security and routing are flawless.

---

## Day 23 - 25: Final Verification & Documentation

📌 **Topics Covered:**  
- Full resource and security verification checklist.
- Begin formal documentation of template and stack output.

💻 **What I Did:**  
- Reviewed each resource against checklist (VPC, subnets, IGW, NAT, routes, SG/NACL).
- Documented YAML sections: purpose, parameters, outputs for future contributors.

🧠 **Reflections:**  
Well-commented templates and checklists will save days for teams using/reviewing my project.

---

## Day 26 - 28: Reflection, Challenges, Future Scope

📌 **Topics Covered:**  
- Results, success discussion.
- Key learnings in infra automation.
- Scalability, monitoring, security, cost optimization, advanced networking for future.

💻 **What I Did:**  
- Summarized outcomes: modular, secure, HA infra; passed all verification.
- Wrote lessons learned: IaC, auto-scaling, troubleshooting, cost-awareness.
- Outlined next steps, scalability (multi-region, ELB, RDS), monitoring (CloudWatch), cost optimization (savings plans).

🧠 **Reflections:**  
IaC has truly changed my understanding of automating and scaling cloud infra for real-world production needs.

---

# ✅ Achievements

- Designed and deployed automated VPC with public/private subnets, IGW/NAT, EC2, and modular routing.
- Mastered IaC principles using CloudFormation, YAML best practices, stack troubleshooting.
- Fully documented, reusable template for future team use and scale-out.

---

# 🚀 What’s Next?

- Modularize template for complex services (ECS/RDS/ELB), add autoscaling.
- Refine security: granular IAM, enable VPC Flow Logs, audit with AWS Config.
- Integrate monitoring, cost optimization, advanced networking (Transit GW, PrivateLink).
- Share project for peer usage, student learning, DevOps onboarding
