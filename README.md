# 🛡️ Laboratórios de Cybersecurity

<p align="center">
  <img src="https://img.shields.io/badge/Foco-Cybersecurity-red?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Abordagem-Prática-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Status-Aprendizado%20Contínuo-success?style=for-the-badge" />
</p>

<p align="center">
  <strong>Laboratórios práticos de cybersecurity com foco em análise de vulnerabilidades, penetration testing, avaliação de segurança e documentação técnica.</strong>
</p>

<p align="center">
  🔎 Reconnaissance &nbsp; • &nbsp; 🌐 Network Security &nbsp; • &nbsp; ⚔️ Penetration Testing &nbsp; • &nbsp; 🛡️ Vulnerability Analysis
</p>

---

## 👨‍💻 Sobre o Projeto

**Cybersecurity Training Labs** é um projeto pessoal de aprendizado prático em cybersecurity, desenvolvido para aprimorar habilidades técnicas por meio de experimentos controlados, investigações de vulnerabilidades e análises de segurança.

Este repositório documenta exercícios práticos envolvendo sistemas intencionalmente vulneráveis, ferramentas de segurança, serviços de rede e técnicas de exploração.

Cada laboratório segue uma metodologia estruturada:

- Compreensão do ambiente alvo (*Target Environment*) e dos serviços disponíveis.
- Identificação de possíveis falhas de segurança.
- Investigação e validação de vulnerabilidades.
- Execução de testes de segurança controlados.
- Análise de evidências técnicas e do impacto na segurança.
- Documentação dos resultados e das recomendações de mitigação.

O repositório também funciona como meu **portfólio técnico**, registrando minha evolução no aprendizado, experiência prática e desenvolvimento profissional na área de cybersecurity.

## 🎯 Objetivos de Aprendizado

O objetivo principal é desenvolver progressivamente competências práticas nas seguintes áreas:

| Área | Competências |
|---|---|
| 🔎 Reconnaissance | Descoberta de hosts, coleta de informações e mapeamento de redes. |
| 🌐 Network Security | Protocolos de rede, portas, serviços e análise de tráfego. |
| 🧭 Service Enumeration | Identificação de serviços, detecção de versões e análise de configurações. |
| 🔐 Authentication Security | Mecanismos de autenticação e auditoria controlada de credenciais. |
| 🕸️ Web Application Security | Tecnologias web, testes de aplicações e identificação de vulnerabilidades. |
| 💥 Vulnerability Assessment | Pesquisa, validação e análise de impacto de vulnerabilidades. |
| ⚔️ Penetration Testing | Exploração controlada e metodologias de testes de segurança. |
| 🛡️ Security Remediation | Análise de riscos e recomendações de mitigação. |

## 🧪 Laboratórios Concluídos

### Metasploitable 2 — Backdoor do vsFTPd 2.3.4

<sub>Investigação de Vulnerabilidade · CVE-2011-2523 · TCP/21</sub>

<kbd>Concluído</kbd>

**Objetivo:** Investigar e validar a vulnerabilidade de backdoor associada a uma distribuição comprometida do vsFTPd 2.3.4.

**Atividades realizadas:**

- 🔎 Identificação e enumeração do serviço FTP utilizando Nmap.
- 🧭 Análise do banner do serviço e do comportamento do protocolo FTP.
- 📚 Investigação do contexto técnico da CVE-2011-2523.
- 🔬 Análise do script de detecção NSE do Nmap.
- ⚔️ Validação da vulnerabilidade utilizando Nmap NSE.
- 🛠️ Exploração controlada utilizando o Metasploit Framework.
- 🔐 Confirmação de execução remota de comandos (*Remote Command Execution*) com privilégios de `root`.
- 📑 Documentação das evidências técnicas, do impacto na segurança e das recomendações de mitigação.

**Resultado verificado:** Exploração bem-sucedida no ambiente de laboratório isolado, resultando na abertura de uma sessão remota com privilégios de `root` no sistema alvo.

**Ferramentas:** `Kali Linux` · `Nmap` · `Metasploit Framework` · `Metasploitable 2`

**Documentação técnica e evidências:**

[Visualizar documentação completa do laboratório](metasploitable-2/vsftpd-234-backdoor/README.md)

---

## 🧰 Ferramentas e Tecnologias

Ferramentas utilizadas ou estudadas ao longo do processo de aprendizado:

| Ferramenta | Aplicação |
|---|---|
| 🔎 Nmap | Descoberta de hosts, varredura de portas, enumeração de serviços e detecção de vulnerabilidades. |
| ⚔️ Metasploit Framework | Exploração controlada e validação de segurança. |
| 🔐 Medusa | Auditoria de mecanismos de autenticação em ambientes de laboratório autorizados. |
| 📡 Wireshark | Captura de tráfego de rede e análise de protocolos. |
| 🌐 Burp Suite | Inspeção de tráfego HTTP e testes de segurança em aplicações web. |
| 🐧 Linux | Administração de sistemas e ambientes de testes de segurança. |
| 🐍 Python | Automação, scripting e desenvolvimento de ferramentas de segurança. |
| 🖥️ Virtualização | Criação de ambientes isolados de laboratório utilizando máquinas virtuais. |

As ferramentas são incluídas de acordo com sua relevância para os exercícios atuais e futuros. A presença de uma ferramenta nesta lista não significa necessariamente que ela tenha sido utilizada em todos os laboratórios concluídos.

## ⚙️ Metodologia de Testes de Segurança

As investigações seguem uma metodologia estruturada, inspirada em práticas comuns de *Penetration Testing* e *Vulnerability Assessment*.

| Etapa | Atividade |
|---|---|
| 01. Reconnaissance | Coleta inicial de informações sobre o ambiente alvo. |
| 02. Scanning | Identificação de hosts, portas abertas e serviços disponíveis. |
| 03. Enumeration | Investigação dos serviços identificados e das informações expostas. |
| 04. Vulnerability Analysis | Pesquisa e validação de possíveis falhas de segurança. |
| 05. Controlled Exploitation | Reprodução de vulnerabilidades em ambientes autorizados. |
| 06. Impact Assessment | Avaliação das consequências técnicas de uma exploração bem-sucedida. |
| 07. Reporting | Documentação das evidências, descobertas e recomendações de correção. |

A metodologia é adaptada ao escopo e aos objetivos de cada laboratório.

## 📑 Documentação Técnica e Evidências

Cada investigação concluída busca fornecer documentação clara, reproduzível e fundamentada tecnicamente.

Dependendo da natureza do laboratório, os relatórios podem incluir:

- **Visão geral (*Overview*):** objetivo e escopo da investigação.
- **Ambiente (*Environment*):** sistemas alvo, configuração de rede e ferramentas utilizadas.
- **Descoberta (*Discovery*):** procedimentos de identificação e enumeração.
- **Análise técnica (*Technical Analysis*):** explicação da vulnerabilidade ou comportamento investigado.
- **Validação (*Validation*):** métodos e resultados utilizados para confirmar as descobertas.
- **Evidências (*Evidence*):** saídas de terminal, capturas de tela e observações relevantes.
- **Impacto na segurança (*Security Impact*):** consequências e riscos potenciais.
- **Mitigação (*Mitigation*):** recomendações para reduzir ou eliminar os riscos identificados.
- **Referências (*References*):** documentação oficial e fontes técnicas.

As evidências são organizadas junto à documentação do respectivo laboratório.

## 📈 Evolução do Aprendizado

Este repositório representa um processo contínuo de aprendizado e desenvolvimento profissional na área de cybersecurity.

O foco está no desenvolvimento da capacidade de:

- Investigar sistemas e serviços de rede de forma independente.
- Compreender protocolos de rede e o comportamento de sistemas operacionais.
- Identificar e analisar superfícies de ataque (*Attack Surface*).
- Utilizar ferramentas de segurança compreendendo seu funcionamento e suas limitações.
- Validar descobertas em vez de depender exclusivamente de resultados automatizados.
- Interpretar evidências técnicas e avaliar impactos na segurança.
- Produzir relatórios técnicos profissionais.
- Compreender medidas defensivas e estratégias de mitigação.

Novos laboratórios e investigações técnicas serão adicionados conforme o avanço do conhecimento e da experiência prática.

## 📚 Referências Técnicas

Os seguintes recursos apoiam os estudos e as pesquisas técnicas:

- [OWASP Foundation](https://owasp.org/)
- [OWASP Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [Documentação oficial do Nmap](https://nmap.org/book/man.html)
- [MITRE ATT&CK](https://attack.mitre.org/)
- [MITRE CWE](https://cwe.mitre.org/)
- [CVE Program](https://www.cve.org/)
- [FIRST CVSS](https://www.first.org/cvss/)

As referências específicas utilizadas em cada investigação são documentadas nos respectivos diretórios dos laboratórios.

## ⚠️ Aviso Legal e Ético

Este repositório destina-se exclusivamente a fins educacionais e ao desenvolvimento profissional.

Todas as atividades práticas são realizadas em ambientes de laboratório isolados, em sistemas intencionalmente vulneráveis ou em infraestruturas para as quais existe autorização explícita.

As técnicas e ferramentas documentadas não devem ser utilizadas contra sistemas, redes ou serviços de terceiros sem a devida autorização.

---

<p align="center">
  <strong>🔎 Investigar. ⚔️ Compreender. 🛡️ Proteger.</strong>
</p>

<p align="center">
  <sub>Portfólio pessoal de estudos e pesquisas em Cybersecurity</sub>
</p>
