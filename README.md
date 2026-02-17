# Tharun Sridhar — Security Case Studies

I am a Computer Science student interested in software systems and information security.
This repository contains personal case studies where I analyzed real-world vulnerabilities
and breaches to understand how systems fail and how they can be designed more safely.

These are not penetration tests or exploit reproductions.  
They are technical analyses based on public disclosures, documentation, and security research articles.

Focus areas:
• Web application security
• API authorization failures
• Cloud identity and access control
• System design weaknesses


---

## React2Shell — React Server Components Remote Code Execution

### What happened
- A server action endpoint accepted crafted serialized data
- The framework trusted client-controlled input

### How the attacker succeeded
- Deserialization logic flaw
- Prototype pollution
- Server-side command execution

### Impact
- Full server compromise
- Access to application data
- Remote command execution

### Detection signals
- Unusual POST requests to server action endpoints
- Unexpected child process execution
- Outbound connections from the application server

### Prevention
- Validate serialized inputs
- Restrict exposed server actions
- Patch framework versions
- Monitor runtime processes

**Full case study:**  
[react2shell-rce-case-study.pdf](https://github.com/tharunsridhar/security-research-portfolio/blob/main/Remote_Code_Execution_CVE-2025-55182.pdf)


---

## Star Health Insurance Breach — API Authorization Failure

### What happened
- Attackers obtained valid credentials
- API endpoints allowed access to unrelated customer records

### How the attacker succeeded
- IDOR (Insecure Direct Object Reference)
- Missing object-level authorization checks
- No effective rate limiting

### Impact
- Large-scale personal and medical data exposure
- Identity and financial risk to customers

### Detection signals
- Sequential API ID requests
- High data access volume per account
- Access to multiple unrelated user records

### Prevention
- Object-level authorization checks
- Rate limiting and monitoring
- Credential lifecycle management

**Full case study:**  
[star-health-breach-case-study.pdf](https://github.com/tharunsridhar/security-research-portfolio/blob/main/star_health_data_breach.pdf)


---

## Zero Trust → Adaptive Trust in Multi-Cloud Security

### What I studied
- Identity-based access control in cloud systems
- Continuous verification models
- Behavioral risk evaluation

### Key observations
- Network perimeter security is no longer sufficient
- Identity becomes the primary security boundary
- Continuous validation reduces lateral movement risk

**Full case study:**  
[adaptive-trust-cloud-case-study.pdf](https://github.com/tharunsridhar/security-research-portfolio/blob/main/Zero_Trust_to_Adaptive_Trust_in_Multi-Cloud_Environments.pdf)


---

## Overall Observations

From analyzing multiple incidents:

• Many major breaches originate from authorization failures rather than hacking tools  
• Trusted system features often create unintended attack surface  
• Detection failures allow attackers to remain longer than the initial compromise  
• Secure system design is as important as secure code
