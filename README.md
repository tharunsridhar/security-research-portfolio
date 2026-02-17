# Tharun Sridhar — Security Case Studies

I am a Computer Science student interested in software systems and information security.
This repository contains personal case studies where I analyzed real-world vulnerabilities
and breaches to understand how systems fail and how they can be designed more safely.

These are not penetration tests or exploit reproductions.  
They are technical analyses based on public disclosures, documentation, and security research.

Focus areas:
• Web application security  
• API authorization failures  
• Cloud identity and access control  
• System design weaknesses


---

## React2Shell — React Server Components Remote Code Execution

![React2Shell Attack Flow](assets/rce-nextjs.png)
*Diagram: Crafted Flight payload reaches the server action endpoint, triggers insecure deserialization, prototype pollution, and finally server-side command execution.*

### What happened
- A server action endpoint accepted crafted serialized data
- The framework trusted client-controlled UI state

### How the attacker succeeded
- Flight protocol deserialization flaw
- Prototype pollution of object chain
- Execution via JavaScript Function() constructor
- Node.js child_process execution

### Impact
- Full server compromise
- Environment variable and database access
- Remote command execution

### Detection signals
- Unusual POST requests to server action endpoints
- Unexpected child process execution
- Outbound traffic from application server

### Prevention
- Strict deserialization validation
- Server action exposure restrictions
- Framework patching
- Runtime process monitoring

**Full case study:**  
[Remote_Code_Execution_CVE-2025-55182.pdf](https://github.com/tharunsridhar/security-research-portfolio/blob/main/Remote_Code_Execution_CVE-2025-55182.pdf)


---

## Star Health Insurance Breach — Broken Authorization (IDOR)

![IDOR Authorization Failure](assets/idor.png)
*Diagram: Logged-in user requests sequential user IDs; backend checks authentication but not record ownership, exposing private data.*

### What happened
- Attackers obtained valid credentials
- Backend APIs allowed access to unrelated user records

### How the attacker succeeded
- Insecure Direct Object Reference (IDOR)
- Missing object-level authorization checks
- Sequential ID enumeration

### Impact
- Large-scale exposure of sensitive personal and medical data
- Identity and financial risk to users

### Detection signals
- Sequential API ID requests
- High volume data access per account
- Access to unrelated user records

### Prevention
- Record ownership verification
- Authorization checks per request
- Monitoring abnormal access patterns

**Full case study:**  
[star_health_data_breach.pdf](https://github.com/tharunsridhar/security-research-portfolio/blob/main/star_health_data_breach.pdf)


---

## Zero Trust → Adaptive Trust in Cloud Security

![Adaptive Trust Model](assets/adaptive-trust.png)
*Diagram: After login the system monitors behavior; anomalies trigger MFA challenge and access is blocked.*

### What I studied
- Identity-based security in distributed cloud systems
- Continuous verification models
- Behavioral anomaly detection

### Key observations
- Identity is now the primary security boundary
- Valid credentials do not equal trusted activity
- Continuous monitoring detects compromised sessions

### Security concept
Traditional Zero Trust:
- Verify identity at login

Adaptive Trust:
- Continuously evaluate user behavior
- Dynamically adjust access privileges

**Full case study:**  
[Zero_Trust_to_Adaptive_Trust_in_Multi-Cloud_Environments.pdf](https://github.com/tharunsridhar/security-research-portfolio/blob/main/Zero_Trust_to_Adaptive_Trust_in_Multi-Cloud_Environments.pdf)


---

## Overall Observations

From analyzing multiple incidents:

• Major breaches often originate from authorization failures rather than advanced exploits  
• Framework features can unintentionally create attack surface  
• Identity compromise is now more common than system intrusion  
• Detection failures extend attacker dwell time  
• Secure architecture matters as much as secure code


---

