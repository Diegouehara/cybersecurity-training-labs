# 🛡️ Cybersecurity Training Labs

<p align="center">
  <img src="https://img.shields.io/badge/Focus-Cybersecurity-red?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Approach-Practical-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Status-Continuous%20Learning-success?style=for-the-badge" />
</p>

<p align="center">
  <strong>Portfólio de estudos práticos em Cybersecurity, com foco em análise de vulnerabilidades, segurança de redes, penetration testing e documentação técnica.</strong>
</p>

<p align="center">
  🔎 Reconnaissance &nbsp; • &nbsp; 🌐 Network Security &nbsp; • &nbsp; ⚔️ Penetration Testing &nbsp; • &nbsp; 🛡️ Vulnerability Analysis
</p>

---

## 👨‍💻 Sobre Mim

Sou estudante de Cybersecurity, direcionando minha formação para a área de segurança da informação, com interesse em segurança de redes, análise de vulnerabilidades e penetration testing.

Atualmente, desenvolvo conhecimentos em redes de computadores, Linux e ferramentas de segurança, buscando compreender não apenas como executar procedimentos técnicos, mas também os fundamentos e o funcionamento das tecnologias envolvidas.

Este repositório faz parte do meu desenvolvimento profissional e reúne laboratórios práticos, investigações técnicas, evidências e documentação dos conhecimentos adquiridos durante esse processo.

**Áreas de interesse:**
- Network Security
- Vulnerability Assessment
- Penetration Testing
- Linux Security
- Web Application Security

**Estudos em andamento:**
- Fundamentos de redes e protocolos de comunicação.
- Linux e administração de sistemas.
- CompTIA Network+ (N10-009).
- Fundamentos de automação com Python.

## 📁 Sobre o Repositório

O **Cybersecurity Training Labs** é um projeto pessoal de aprendizado prático, criado para documentar estudos e investigações de segurança em ambientes controlados.

O repositório reúne exercícios envolvendo sistemas intencionalmente vulneráveis, serviços de rede, mecanismos de autenticação e ferramentas utilizadas em atividades de segurança ofensiva.

Cada investigação busca seguir uma abordagem estruturada:

- Compreensão do ambiente alvo (*Target Environment*).
- Identificação e enumeração de serviços.
- Pesquisa e análise de possíveis vulnerabilidades.
- Validação técnica das descobertas.
- Execução de testes controlados.
- Análise de evidências e impactos.
- Documentação dos resultados e recomendações de mitigação.

Além de servir como material de estudo e consulta, este projeto funciona como meu **portfólio técnico**, registrando minha evolução e experiência prática na área de Cybersecurity.

## 🎯 Objetivos de Aprendizado

O objetivo é desenvolver progressivamente conhecimentos e habilidades nas seguintes áreas:

| Área | Objetivo |
|---|---|
| 🔎 Reconnaissance | Descoberta de hosts, coleta de informações e mapeamento de redes. |
| 🌐 Network Security | Compreensão de protocolos, portas, serviços e tráfego de rede. |
| 🧭 Service Enumeration | Identificação de serviços, detecção de versões e análise de configurações. |
| 🔐 Authentication Security | Análise de mecanismos de autenticação e auditoria controlada de credenciais. |
| 🕸️ Web Application Security | Estudo de aplicações web e identificação de vulnerabilidades. |
| 💥 Vulnerability Assessment | Pesquisa, validação e avaliação de vulnerabilidades. |
| ⚔️ Penetration Testing | Execução de testes de segurança e exploração controlada. |
| 🛡️ Security Remediation | Análise de riscos e recomendações de mitigação. |

## 🧪 Laboratórios Documentados

Esta seção reúne as investigações práticas concluídas e documentadas no repositório.

### 1. Metasploitable 2 — FTP Authentication Security

<sub>Authentication Security · FTP · Credential Auditing · TCP/21</sub>

**Objetivo:** Avaliar a segurança do serviço FTP, investigando mecanismos de autenticação, exposição de credenciais e possibilidades de acesso ao sistema de arquivos.

**Atividades realizadas:**
- 🔎 Reconhecimento e enumeração do serviço FTP com Nmap.
- 🔐 Análise do comportamento de autenticação e das respostas do servidor.
- ⚔️ Execução de ataques de dicionário utilizando Hydra e Medusa.
- ✅ Validação manual das credenciais identificadas.
- 📡 Captura e análise do tráfego FTP com Wireshark.
- 🔍 Identificação de credenciais transmitidas em texto claro.
- 📂 Enumeração de diretórios acessíveis após a autenticação.
- 📑 Documentação das evidências, riscos e recomendações de segurança.

**Resultado verificado:** Identificação e validação de credenciais de acesso ao serviço FTP, além da constatação de transmissão de dados de autenticação sem criptografia e acesso a diretórios do sistema de arquivos.

**Ferramentas:** `Kali Linux` · `Nmap` · `Hydra` · `Medusa` · `Wireshark`

**Documentação técnica:**

[Visualizar Authentication Security Lab](metasploitable-2/ftp/authentication-security/README.md)

---

### 2. Metasploitable 2 — Backdoor do vsFTPd 2.3.4

<sub>Vulnerability Assessment · CVE-2011-2523 · TCP/21 · TCP/6200</sub>

**Objetivo:** Investigar e validar a backdoor associada à distribuição comprometida do vsFTPd 2.3.4, analisando seu mecanismo de ativação e as possibilidades de execução remota de comandos.

**Atividades realizadas:**
- 🔎 Identificação e enumeração do serviço FTP utilizando Nmap.
- 🧭 Análise do banner e do comportamento do serviço.
- 📚 Pesquisa do contexto técnico da CVE-2011-2523.
- 🔬 Análise do script de detecção NSE do Nmap.
- ⚔️ Validação da vulnerabilidade utilizando Nmap NSE.
- 🛠️ Exploração controlada utilizando o Metasploit Framework.
- 💻 Investigação do mecanismo de ativação manual da backdoor por meio de FTP e Netcat.
- 🔐 Confirmação de acesso remoto com privilégios de `root`.
- 📑 Documentação das evidências e recomendações de mitigação.

**Resultado verificado:** A vulnerabilidade foi validada no ambiente isolado por dois métodos: exploração automatizada com Metasploit Framework e conexão manual ao serviço de shell disponibilizado pela backdoor. Foi confirmada execução de comandos com privilégios de `root`.

**Ferramentas:** `Kali Linux` · `Nmap` · `Metasploit Framework` · `Netcat` · `Metasploitable 2`

**Documentação técnica:**

[Visualizar vsFTPd 2.3.4 Backdoor Lab](metasploitable-2/ftp/vsftpd-234-backdoor/README.md)

---

## 🧰 Ferramentas e Tecnologias

Ferramentas utilizadas nas investigações e tecnologias que fazem parte do meu processo de aprendizado.

### Ferramentas utilizadas nos laboratórios

| Ferramenta | Aplicação |
|---|---|
| 🔎 Nmap | Descoberta de hosts, varredura de portas, enumeração de serviços e detecção de vulnerabilidades. |
| ⚔️ Metasploit Framework | Validação e exploração controlada de vulnerabilidades. |
| 🔐 Hydra | Auditoria de mecanismos de autenticação utilizando ataques de dicionário. |
| 🔐 Medusa | Testes controlados de autenticação em serviços de rede. |
| 📡 Wireshark | Captura e análise de tráfego e protocolos de rede. |
| 💻 Netcat | Estabelecimento de conexões TCP e interação com serviços de rede. |
| 🐧 Linux | Administração de sistemas e utilização de ambientes de segurança. |
| 🖥️ Virtualização | Criação de ambientes isolados para execução dos laboratórios. |

### Tecnologias em desenvolvimento

| Tecnologia | Aplicação pretendida |
|---|---|
| 🐍 Python | Automação, scripting e desenvolvimento de ferramentas auxiliares. |
| 🌐 Burp Suite | Inspeção de tráfego HTTP e testes de segurança em aplicações web. |

A presença de uma tecnologia nesta seção não significa necessariamente que tenha sido utilizada em todos os laboratórios ou que represente domínio profissional sobre a ferramenta.

## ⚙️ Metodologia de Testes

As investigações seguem uma metodologia estruturada, inspirada em práticas de *Penetration Testing* e *Vulnerability Assessment*.

| Etapa | Atividade |
|---|---|
| 01. Reconnaissance | Coleta inicial de informações sobre o ambiente alvo. |
| 02. Scanning | Identificação de hosts, portas abertas e serviços disponíveis. |
| 03. Enumeration | Investigação dos serviços e das informações expostas. |
| 04. Vulnerability Analysis | Pesquisa e validação de possíveis falhas de segurança. |
| 05. Controlled Exploitation | Reprodução de vulnerabilidades em ambientes autorizados. |
| 06. Impact Assessment | Avaliação das consequências técnicas das falhas identificadas. |
| 07. Reporting | Documentação das evidências, descobertas e recomendações. |

A metodologia é adaptada de acordo com o escopo, as características e os objetivos de cada laboratório.

## 📑 Documentação Técnica e Evidências

Cada investigação busca fornecer documentação clara, organizada e fundamentada tecnicamente.

Dependendo da natureza do laboratório, os relatórios podem incluir:

- **Overview:** objetivo e escopo da investigação.
- **Environment:** sistemas alvo, configuração de rede e ferramentas utilizadas.
- **Discovery:** procedimentos de reconhecimento e enumeração.
- **Technical Analysis:** explicação técnica do serviço ou vulnerabilidade investigada.
- **Validation:** procedimentos e resultados que confirmam as descobertas.
- **Evidence:** capturas de tela, comandos, outputs e observações relevantes.
- **Security Impact:** consequências e riscos identificados.
- **Mitigation:** recomendações para reduzir ou eliminar os riscos.
- **References:** documentação oficial e fontes técnicas.

As evidências são armazenadas no diretório `evidence/` de cada investigação, enquanto as fontes técnicas ficam organizadas em `references/`.

## 📈 Evolução do Aprendizado

Este projeto representa um processo contínuo de aprendizado e desenvolvimento profissional.

O foco não está apenas na execução de ferramentas, mas também no desenvolvimento da capacidade de:

- Compreender protocolos de rede e o comportamento de sistemas operacionais.
- Investigar serviços e identificar possíveis superfícies de ataque (*Attack Surface*).
- Entender o funcionamento e as limitações das ferramentas de segurança.
- Validar descobertas e interpretar resultados tecnicamente.
- Analisar evidências e avaliar impactos na segurança.
- Documentar investigações de maneira clara e reproduzível.
- Compreender medidas defensivas e estratégias de mitigação.

Novos laboratórios serão adicionados conforme o avanço dos estudos e a realização de novas investigações práticas.

## 📚 Referências Técnicas

Recursos utilizados como apoio aos estudos e pesquisas:

- [OWASP Foundation](https://owasp.org/)
- [OWASP Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [Documentação oficial do Nmap](https://nmap.org/book/man.html)
- [MITRE ATT&CK](https://attack.mitre.org/)
- [MITRE CWE](https://cwe.mitre.org/)
- [CVE Program](https://www.cve.org/)
- [FIRST CVSS](https://www.first.org/cvss/)

As referências específicas utilizadas em cada investigação são documentadas nos respectivos diretórios.

## ⚠️ Aviso Legal e Ético

Este repositório destina-se exclusivamente a fins educacionais e ao desenvolvimento profissional.

Todas as atividades práticas são realizadas em ambientes de laboratório isolados, em sistemas intencionalmente vulneráveis ou em infraestruturas para as quais existe autorização explícita.

As técnicas e ferramentas documentadas não devem ser utilizadas contra sistemas, redes ou serviços de terceiros sem a devida autorização.

## 🔗 Contato e Perfis

- **GitHub:** [Diegouehara](https://github.com/Diegouehara)
- **LinkedIn:** [Perfil profissional](https://www.linkedin.com/in/diego-uehara-010830272/)

---

<p align="center">
  <strong>🔎 Investigar. ⚔️ Compreender. 🛡️ Proteger.</strong>
</p>

<p align="center">
  <sub>Portfólio pessoal de estudos e pesquisas em Cybersecurity</sub>
</p>
