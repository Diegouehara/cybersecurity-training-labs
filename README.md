# 🛡️ Cybersecurity Training Labs

<p align="center">
  <img src="https://img.shields.io/badge/Foco-Cybersecurity-red?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Abordagem-Aprendizado%20Prático-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Status-Aprendizado%20Contínuo-success?style=for-the-badge" />
</p>

<p align="center">
  <strong>Laboratórios práticos de Cybersecurity com foco em investigação de vulnerabilidades, segurança de redes, análise de aplicações e penetration testing.</strong>
</p>

<p align="center">
  🔎 Reconnaissance &nbsp; • &nbsp; 🌐 Network Security &nbsp; • &nbsp; 🔐 Authentication Security &nbsp; • &nbsp; ⚔️ Penetration Testing &nbsp; • &nbsp; 🛡️ Vulnerability Analysis
</p>

---

## 📁 Sobre o Projeto

O **Cybersecurity Training Labs** é um repositório dedicado à documentação de estudos, experimentos e investigações práticas na área de Cybersecurity.

Os laboratórios são realizados em ambientes controlados, utilizando sistemas e aplicações intencionalmente vulneráveis para investigar serviços de rede, analisar mecanismos de autenticação, compreender vulnerabilidades e estudar técnicas de exploração.

O objetivo não é apenas executar ferramentas, mas compreender os procedimentos realizados, interpretar seus resultados e documentar as descobertas de maneira técnica e reproduzível.

Cada investigação busca reunir:

- 🔎 Reconhecimento e identificação de superfícies de ataque.
- 🔬 Análise técnica de serviços, aplicações e vulnerabilidades.
- ⚔️ Testes controlados utilizando ferramentas de segurança.
- 📡 Inspeção de tráfego e análise de requisições.
- 📸 Evidências práticas dos procedimentos realizados.
- 📊 Interpretação dos resultados e avaliação de impacto.
- 🛡️ Recomendações de mitigação e segurança.

Este repositório também funciona como um **portfólio técnico**, registrando a evolução dos conhecimentos e as experiências práticas desenvolvidas ao longo dos estudos.

## 🎯 Áreas de Estudo

O projeto contempla diferentes áreas da segurança da informação, com foco no desenvolvimento progressivo de conhecimentos técnicos.

| Área | Objetivo |
|---|---|
| 🔎 Reconnaissance | Descoberta de hosts, coleta de informações e mapeamento de redes. |
| 🌐 Network Security | Estudo de protocolos, portas, serviços e tráfego de rede. |
| 🧭 Service Enumeration | Identificação de serviços, detecção de versões e análise de configurações. |
| 🔐 Authentication Security | Investigação de mecanismos de autenticação e auditoria controlada de credenciais. |
| 🕸️ Web Application Security | Análise de aplicações web e identificação de vulnerabilidades. |
| 💥 Vulnerability Assessment | Pesquisa, validação e análise do impacto de vulnerabilidades. |
| ⚔️ Penetration Testing | Execução de testes de segurança e exploração controlada. |
| 📡 Traffic Analysis | Captura, inspeção e interpretação de comunicações de rede. |
| 🛡️ Defensive Security | Análise de riscos, identificação de exposições e estratégias de mitigação. |

## 🧪 Ambientes de Laboratório

Os estudos são organizados por ambiente, permitindo separar a configuração dos sistemas alvo e as investigações realizadas em cada um.

### 🖥️ Metasploitable 2

<sub>Linux Security · Network Services · Vulnerability Assessment · Penetration Testing</sub>

O Metasploitable 2 é uma máquina virtual Linux intencionalmente vulnerável, utilizada para investigar serviços de rede, analisar configurações inseguras e praticar técnicas de segurança ofensiva em ambiente controlado.

**Investigações realizadas:**

#### 1. 🔐 FTP Authentication Security

<sub>Authentication Security · Credential Auditing · FTP · TCP/21</sub>

**Objetivo:** avaliar os mecanismos de autenticação FTP, identificar fragilidades relacionadas a credenciais e analisar a exposição de informações durante a comunicação.

**Atividades realizadas:**

- 🔎 Reconhecimento e enumeração do serviço FTP utilizando Nmap.
- 🔐 Análise da autenticação anônima e de usuários locais.
- 🔬 Investigação do comportamento do servidor após falhas consecutivas de login.
- ⚔️ Auditoria de credenciais utilizando Hydra e Medusa.
- ✅ Validação manual das credenciais identificadas.
- 📡 Captura e análise do tráfego FTP utilizando Wireshark.
- 🔍 Identificação de credenciais e comandos transmitidos em texto claro.
- 📂 Análise da navegação e do acesso aos diretórios do sistema de arquivos.

**Resultado verificado:** identificação e validação de credenciais padrão de uma conta local, confirmação da exposição de informações de autenticação sem criptografia e acesso à estrutura de diretórios por meio do serviço FTP.

**Ferramentas:** `Nmap` · `Hydra` · `Medusa` · `Wireshark` · `Cliente FTP` · `Kali Linux`

**Documentação técnica:**

[📄 Visualizar FTP Authentication Security](metasploitable-2/ftp/authentication-security/README.md)

---

#### 2. 🛡️ vsFTPd 2.3.4 Backdoor

<sub>Vulnerability Investigation · CVE-2011-2523 · TCP/21 · TCP/6200</sub>

**Objetivo:** investigar, validar e explorar a backdoor associada a uma distribuição comprometida do vsFTPd 2.3.4.

**Atividades realizadas:**

- 🔎 Identificação e enumeração do serviço FTP utilizando Nmap.
- 📚 Investigação do contexto técnico da CVE-2011-2523.
- 🔬 Análise do código-fonte do script NSE de detecção do Nmap.
- ⚔️ Validação da vulnerabilidade utilizando Nmap NSE.
- 🛠️ Exploração automatizada utilizando Metasploit Framework.
- 🔧 Reprodução manual da exploração utilizando FTP e Netcat.
- 🔐 Confirmação de execução remota de comandos com privilégios de `root`.
- 📑 Documentação das evidências, impacto e recomendações de mitigação.

**Resultado verificado:** exploração realizada por duas abordagens: utilização do Metasploit Framework e acionamento manual da backdoor com conexão ao Bind Shell disponibilizado na TCP/6200. Em ambas as abordagens, foi confirmado acesso remoto com privilégios de `root`.

**Ferramentas:** `Nmap` · `Metasploit Framework` · `Netcat` · `Cliente FTP` · `Kali Linux`

**Documentação técnica:**

[📄 Visualizar vsFTPd 2.3.4 Backdoor](metasploitable-2/ftp/vsftpd-234-backdoor/README.md)

---

### 🕸️ DVWA — Damn Vulnerable Web Application

<sub>Web Application Security · Authentication Security · Vulnerability Assessment</sub>

O DVWA é uma aplicação web intencionalmente vulnerável, utilizada para estudar falhas comuns de segurança em aplicações web e compreender técnicas de identificação, validação e mitigação.

A aplicação está hospedada localmente por meio de Docker e é utilizada para investigações práticas de segurança web.

**Investigações realizadas:**

#### 1. 🔐 Brute Force Authentication

<sub>Web Authentication · Dictionary Attack · HTTP · Medusa</sub>

**Objetivo:** investigar a resistência de um formulário web a tentativas automatizadas de autenticação.

**Atividades realizadas:**

- 🔎 Análise do formulário de autenticação e de seus parâmetros.
- 🌐 Inspeção de requisições HTTP utilizando Firefox DevTools.
- 🍪 Investigação do gerenciamento de sessões por meio de cookies.
- 🔬 Análise do código-fonte PHP responsável pela autenticação.
- ⚔️ Auditoria automatizada de credenciais utilizando Medusa.
- 📊 Análise de respostas HTTP e identificação de condições de sucesso e falha.
- ✅ Validação manual das credenciais identificadas.
- 🛡️ Estudo de mecanismos de proteção contra brute force.

**Resultado verificado:** identificação de credenciais válidas no nível de segurança Low e confirmação manual da autenticação por meio da resposta da aplicação.

**Ferramentas:** `DVWA` · `Docker` · `Medusa` · `Firefox DevTools` · `Kali Linux`

**Documentação técnica:**

[📄 Visualizar DVWA Lab](dvwa/README.md)

<sub>Próxima etapa: comparação do comportamento do formulário nos níveis de segurança Medium e Low.</sub>

---

## 🧰 Ferramentas e Tecnologias

Ferramentas utilizadas nas investigações e tecnologias que fazem parte do processo de aprendizado.

### 🔧 Ferramentas utilizadas

| Ferramenta | Aplicação |
|---|---|
| 🔎 Nmap | Descoberta de hosts, varredura de portas, enumeração de serviços e detecção de vulnerabilidades. |
| ⚔️ Metasploit Framework | Validação e exploração controlada de vulnerabilidades. |
| 🔐 Hydra | Auditoria de mecanismos de autenticação utilizando ataques de dicionário. |
| 🔐 Medusa | Testes automatizados de autenticação em serviços de rede e formulários web. |
| 📡 Wireshark | Captura e análise de tráfego e protocolos de rede. |
| 💻 Netcat | Estabelecimento de conexões TCP e interação com serviços de rede. |
| 🐳 Docker | Criação e gerenciamento de ambientes de aplicações em containers. |
| 🌐 Firefox DevTools | Inspeção de requisições HTTP, cabeçalhos, cookies e respostas. |
| 🐧 Linux | Utilização e administração de sistemas e ambientes de segurança. |
| 🖥️ Virtualização | Criação e gerenciamento de ambientes isolados de laboratório. |

### 📚 Tecnologias em estudo

| Tecnologia | Aplicação |
|---|---|
| 🐍 Python | Automação, scripting e desenvolvimento de ferramentas auxiliares. |
| 🌐 Burp Suite | Inspeção de tráfego HTTP e testes de segurança em aplicações web. |
| 🗄️ SQL | Estudo de consultas, bancos de dados e vulnerabilidades relacionadas. |

A presença de uma ferramenta ou tecnologia nesta seção não significa que ela tenha sido utilizada em todos os laboratórios ou que represente domínio completo sobre ela.

## ⚙️ Metodologia de Testes

As investigações seguem uma metodologia estruturada, inspirada em práticas de *Penetration Testing* e *Vulnerability Assessment*.

| Etapa | Atividade |
|---|---|
| 01. Reconnaissance | Coleta inicial de informações sobre o ambiente alvo. |
| 02. Scanning | Identificação de hosts, portas abertas e serviços disponíveis. |
| 03. Enumeration | Investigação dos serviços identificados e das informações expostas. |
| 04. Vulnerability Analysis | Pesquisa e validação de possíveis falhas de segurança. |
| 05. Controlled Exploitation | Reprodução de vulnerabilidades em ambientes autorizados. |
| 06. Impact Assessment | Avaliação das consequências técnicas das falhas identificadas. |
| 07. Reporting | Documentação das evidências, descobertas e recomendações de mitigação. |

A metodologia é adaptada ao escopo e aos objetivos de cada investigação. Nem todas as etapas são necessariamente aplicáveis a todos os laboratórios.

## 📑 Documentação Técnica e Evidências

Cada investigação busca fornecer documentação clara, organizada e fundamentada tecnicamente.

Dependendo da natureza do laboratório, os relatórios podem incluir:

- **Overview:** objetivo e escopo da investigação.
- **Environment:** sistemas alvo, configuração de rede e ferramentas utilizadas.
- **Discovery:** procedimentos de reconhecimento e enumeração.
- **Technical Analysis:** explicação técnica do serviço ou vulnerabilidade investigada.
- **Validation:** procedimentos e resultados utilizados para confirmar as descobertas.
- **Evidence:** capturas de tela, comandos, outputs e observações relevantes.
- **Security Impact:** consequências e riscos identificados.
- **Mitigation:** recomendações para reduzir ou eliminar os riscos.
- **References:** documentação oficial e fontes técnicas.

As evidências são armazenadas no diretório `evidence/` de cada investigação, enquanto as fontes técnicas são organizadas em `references/`.

## 📈 Desenvolvimento dos Estudos

O repositório é atualizado continuamente conforme novos conhecimentos são adquiridos e novas investigações são realizadas.

Os estudos atuais incluem:

- Fundamentos de redes de computadores e protocolos de comunicação.
- Linux e administração de sistemas.
- Segurança de redes e serviços.
- Segurança de aplicações web.
- Análise de vulnerabilidades e técnicas de exploração.
- Fundamentos de segurança ofensiva e defensiva.
- Automação e scripting com Python.

Novos ambientes, ferramentas e laboratórios serão incorporados conforme o avanço dos estudos e a realização de novas investigações práticas.

## 📚 Referências Técnicas

Recursos utilizados como apoio aos estudos e pesquisas:

- [OWASP Foundation](https://owasp.org/)
- [OWASP Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)
- [Documentação oficial do Nmap](https://nmap.org/book/man.html)
- [MITRE ATT&CK](https://attack.mitre.org/)
- [MITRE CWE](https://cwe.mitre.org/)
- [CVE Program](https://www.cve.org/)
- [FIRST CVSS](https://www.first.org/cvss/)

As referências específicas utilizadas em cada investigação são documentadas nos respectivos diretórios.

## ⚠️ Aviso Legal e Ético

Este repositório destina-se exclusivamente a fins educacionais e ao desenvolvimento de conhecimentos em segurança da informação.

Todas as atividades práticas são realizadas em ambientes de laboratório isolados, em sistemas intencionalmente vulneráveis ou em infraestruturas para as quais existe autorização explícita.

As técnicas e ferramentas documentadas não devem ser utilizadas contra sistemas, redes ou serviços de terceiros sem a devida autorização.

## 🔗 Links

- [GitHub — Repositório](https://github.com/Diegouehara/cybersecurity-training-labs)
- [LinkedIn — Perfil profissional](https://www.linkedin.com/in/diego-uehara-010830272/)

---

<p align="center">
  <strong>🔎 Investigar. 🔬 Compreender. ⚔️ Validar. 🛡️ Proteger.</strong>
</p>

<p align="center">
  <sub>Cybersecurity Training Labs · Portfólio de estudos e investigações práticas</sub>
</p>
