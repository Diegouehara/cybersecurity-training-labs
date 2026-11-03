# 🎯 Metasploitable 2 — Security Assessment

## Overview

This directory contains practical security investigations conducted against **Metasploitable 2**, an intentionally vulnerable Linux virtual machine designed for cybersecurity training and penetration testing practice.

The objective is to investigate exposed services, understand security vulnerabilities, validate findings in a controlled environment, and document their technical impact and mitigation strategies.

All activities are performed within an isolated virtual network.

## 🖥️ Laboratory Environment

| Component | Configuration |
|---|---|
| Target | Metasploitable 2 |
| Operating System | Ubuntu Linux 8.04 |
| Virtualization | Virtual Machine |
| Network | Isolated laboratory network |
| Attacker Machine | Kali Linux |

## 🔬 Vulnerability Investigations

Each investigation is maintained independently, with its own technical report, evidence, and references.

| Investigation | Vulnerability | Status |
|---|---|---|
| [vsFTPd 2.3.4 Backdoor](vsftpd-234-backdoor/README.md) | CVE-2011-2523 · TCP/21 | Completed |

Additional investigations will be documented as they are performed and validated.

## 📑 Documentation Structure

Each laboratory directory may contain:

- **README.md:** technical report, methodology, findings, impact, and mitigation.
- **evidence/:** screenshots and supporting technical evidence.
- **references/:** official documentation and research sources.

## ⚠️ Scope and Authorization

All tests are conducted against the intentionally vulnerable Metasploitable 2 virtual machine in an isolated environment under my control.

The techniques documented here are intended exclusively for educational purposes and authorized security testing.

---

<p align="center">
  <sub>Metasploitable 2 · Cybersecurity Training Environment</sub>
</p>
