# 🛡️ Cybersecurity Training Labs

<p align="center">
  <img src="https://img.shields.io/badge/Focus-Cybersecurity-red?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Approach-Hands--On%20Learning-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Status-Active%20Learning-success?style=for-the-badge" />
</p>

<p align="center">
  <strong>Practical cybersecurity labs focused on vulnerability analysis, penetration testing, security assessment, and technical documentation.</strong>
</p>

<p align="center">
  🔎 Reconnaissance &nbsp; • &nbsp; 🌐 Network Security &nbsp; • &nbsp; ⚔️ Penetration Testing &nbsp; • &nbsp; 🛡️ Vulnerability Analysis
</p>

---

## 👨‍💻 About This Project

**Cybersecurity Training Labs** is a personal hands-on cybersecurity project created to develop practical skills through controlled security experiments, vulnerability investigations, and technical analysis.

The repository documents practical exercises involving intentionally vulnerable systems, security tools, network services, and exploitation techniques.

Each lab follows a structured approach:

- Understanding the target environment and its services.
- Identifying potential security weaknesses.
- Investigating and validating vulnerabilities.
- Performing controlled security tests.
- Analyzing technical evidence and security impact.
- Documenting findings and mitigation recommendations.

This repository also serves as my **technical portfolio**, documenting my learning progress, practical experience, and development toward a career in cybersecurity.

## 🎯 Learning Objectives

The main goal is to progressively develop practical competencies in the following areas:

| Area | Skills |
|---|---|
| 🔎 Reconnaissance | Host discovery, information gathering, and network mapping. |
| 🌐 Network Security | Network protocols, ports, services, and traffic analysis. |
| 🧭 Service Enumeration | Service identification, version detection, and configuration analysis. |
| 🔐 Authentication Security | Authentication mechanisms and controlled credential auditing. |
| 🕸️ Web Application Security | Web technologies, application testing, and vulnerability identification. |
| 💥 Vulnerability Assessment | Vulnerability research, validation, and impact analysis. |
| ⚔️ Penetration Testing | Controlled exploitation and security testing methodologies. |
| 🛡️ Security Remediation | Risk analysis and mitigation recommendations. |

## 🧪 Completed Labs

### Metasploitable 2 — vsFTPd 2.3.4 Backdoor

<sub>Vulnerability Investigation · CVE-2011-2523 · TCP/21</sub>

<kbd>Completed</kbd>

**Objective:** Investigate and validate the backdoor vulnerability associated with a compromised distribution of vsFTPd 2.3.4.

**Activities performed:**

- 🔎 Identified and enumerated the FTP service using Nmap.
- 🧭 Analyzed the service banner and FTP behavior.
- 📚 Investigated the technical background of CVE-2011-2523.
- 🔬 Examined the Nmap NSE detection script.
- ⚔️ Validated the vulnerability using Nmap NSE.
- 🛠️ Performed controlled exploitation using the Metasploit Framework.
- 🔐 Confirmed remote command execution with `root` privileges.
- 📑 Documented technical evidence, security impact, and mitigation recommendations.

**Verified result:** Successful exploitation in the isolated laboratory environment, resulting in a remote session with `root` privileges on the target system.

**Tools:** `Kali Linux` · `Nmap` · `Metasploit Framework` · `Metasploitable 2`

**Technical documentation and evidence:**

[View the complete lab report](metasploitable-2/vsftpd-234-backdoor/README.md)

---

## 🧰 Tools & Technologies

Tools used or studied throughout the learning process:

| Tool | Application |
|---|---|
| 🔎 Nmap | Host discovery, port scanning, service enumeration, and vulnerability detection. |
| ⚔️ Metasploit Framework | Controlled exploitation and security validation. |
| 🔐 Medusa | Authentication auditing in authorized laboratory environments. |
| 📡 Wireshark | Network traffic capture and protocol analysis. |
| 🌐 Burp Suite | HTTP traffic inspection and web application security testing. |
| 🐧 Linux | System administration and security testing environments. |
| 🐍 Python | Automation, scripting, and development of security utilities. |
| 🖥️ Virtualization | Isolated laboratory environments using virtual machines. |

Tools are included according to their relevance to current and future laboratory exercises. Their presence in this list does not necessarily mean they have been used in every completed lab.

## ⚙️ Security Testing Methodology

Laboratory investigations follow a structured methodology inspired by common penetration testing and vulnerability assessment practices.

| Phase | Activity |
|---|---|
| 01. Reconnaissance | Gather initial information about the target environment. |
| 02. Scanning | Identify hosts, open ports, and available services. |
| 03. Enumeration | Investigate identified services and exposed information. |
| 04. Vulnerability Analysis | Research and validate potential security weaknesses. |
| 05. Controlled Exploitation | Reproduce vulnerabilities in authorized environments. |
| 06. Impact Assessment | Evaluate the technical consequences of successful exploitation. |
| 07. Reporting | Document evidence, findings, and remediation recommendations. |

The methodology is adapted to the scope and objectives of each individual lab.

## 📑 Technical Documentation & Evidence

Each completed investigation aims to provide clear, reproducible, and technically grounded documentation.

Depending on the nature of the lab, reports may include:

- **Overview:** purpose and scope of the investigation.
- **Environment:** target systems, network configuration, and tools.
- **Discovery:** identification and enumeration procedures.
- **Technical Analysis:** explanation of the vulnerability or behavior investigated.
- **Validation:** methods and results used to confirm findings.
- **Evidence:** terminal output, screenshots, and relevant observations.
- **Security Impact:** consequences and potential risks.
- **Mitigation:** recommendations to reduce or eliminate the identified risk.
- **References:** official documentation and technical sources.

Evidence is organized alongside the corresponding laboratory documentation.

## 📈 Learning Progress

This repository represents an ongoing learning process toward a career in cybersecurity.

The focus is on developing the ability to:

- Independently investigate systems and network services.
- Understand network protocols and operating system behavior.
- Identify and analyze attack surfaces.
- Use security tools with an understanding of their operation and limitations.
- Validate findings instead of relying solely on automated tool output.
- Interpret technical evidence and assess security impact.
- Produce professional technical reports.
- Understand defensive measures and remediation strategies.

New laboratories and technical investigations will be added as knowledge and practical experience progress.

## 📚 Technical References

The following resources support ongoing study and technical research:

- [OWASP Foundation](https://owasp.org/)
- [OWASP Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [Nmap Official Documentation](https://nmap.org/book/man.html)
- [MITRE ATT&CK](https://attack.mitre.org/)
- [MITRE CWE](https://cwe.mitre.org/)
- [CVE Program](https://www.cve.org/)
- [FIRST CVSS](https://www.first.org/cvss/)

Specific references used in individual investigations are documented in their respective laboratory directories.

## ⚠️ Legal & Ethical Disclaimer

This repository is intended exclusively for educational purposes and professional development.

All practical activities are performed in isolated laboratory environments, on intentionally vulnerable systems, or on infrastructure for which explicit authorization has been obtained.

The techniques and tools documented here must not be used against third-party systems, networks, or services without proper authorization.

---

<p align="center">
  <strong>🔎 Investigate. ⚔️ Understand. 🛡️ Secure.</strong>
</p>

<p align="center">
  <sub>Personal Cybersecurity Training & Research Portfolio</sub>
</p>
