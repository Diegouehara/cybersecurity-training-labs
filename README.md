# 🛡️ Cybersecurity Training Labs

<p align="center">
  <img src="https://img.shields.io/badge/Focus-Cybersecurity-red?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Approach-Practical-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Status-Continuous%20Learning-success?style=for-the-badge" />
</p>

<p align="center">
  <strong>Laboratórios práticos de Cybersecurity voltados à investigação de vulnerabilidades, segurança de redes, penetration testing e análise técnica de sistemas.</strong>
</p>

<p align="center">
  🔎 Reconnaissance &nbsp; • &nbsp; 🌐 Network Security &nbsp; • &nbsp; ⚔️ Penetration Testing &nbsp; • &nbsp; 🛡️ Vulnerability Analysis
</p>

---

## 📁 Sobre o Repositório

O **Cybersecurity Training Labs** é um repositório dedicado à documentação de estudos, experimentos e investigações práticas na área de Cybersecurity.

O projeto utiliza ambientes de laboratório controlados, incluindo sistemas intencionalmente vulneráveis, para explorar serviços de rede, investigar falhas de segurança, compreender técnicas de exploração e analisar mecanismos de proteção.

O objetivo não é apenas executar ferramentas, mas compreender os procedimentos realizados, interpretar seus resultados e documentar as descobertas de maneira técnica e reproduzível.

Cada laboratório representa uma investigação independente, reunindo procedimentos, comandos, evidências, análises e referências técnicas.

## 🎯 Objetivos de Aprendizado

O repositório acompanha o desenvolvimento de conhecimentos em diferentes áreas da segurança da informação.

| Área | Objetivo |
|---|---|
| 🔎 Reconnaissance | Descoberta de hosts, coleta de informações e mapeamento de redes. |
| 🌐 Network Security | Estudo de protocolos, portas, serviços e tráfego de rede. |
| 🧭 Service Enumeration | Identificação de serviços, detecção de versões e análise de configurações. |
| 🔐 Authentication Security | Investigação de mecanismos de autenticação e auditoria controlada de credenciais. |
| 🕸️ Web Application Security | Estudo de aplicações web e identificação de vulnerabilidades. |
| 💥 Vulnerability Assessment | Pesquisa, validação e análise do impacto de vulnerabilidades. |
| ⚔️ Penetration Testing | Execução de testes de segurança e exploração controlada. |
| 🛡️ Defensive Security | Análise de riscos, identificação de exposições e estratégias de mitigação. |

O escopo contempla tanto práticas de segurança ofensiva quanto defensiva, buscando compreender as vulnerabilidades e também os mecanismos utilizados para identificá-las e corrigi-las.

## 🧪 Laboratórios Documentados

Nesta seção estão reunidas as investigações práticas concluídas e documentadas no repositório.

### 1. Metasploitable 2 — FTP Authentication Security

<sub>Authentication Security · FTP · Credential Auditing · TCP/21</sub>

**Objetivo:** Investigar a segurança do serviço FTP, analisando os mecanismos de autenticação, a exposição de credenciais e as possibilidades de acesso ao sistema de arquivos.

**Atividades realizadas:**

- 🔎 Reconhecimento e enumeração do serviço FTP com Nmap.
- 🔐 Análise do comportamento de autenticação e das respostas do servidor.
- ⚔️ Execução de ataques de dicionário utilizando Hydra e Medusa.
- ✅ Validação manual das credenciais identificadas.
- 📡 Captura e análise do tráfego FTP com Wireshark.
- 🔍 Identificação de credenciais transmitidas em texto claro.
- 📂 Enumeração de diretórios acessíveis após a autenticação.
- 📑 Documentação das evidências e dos riscos identificados.

**Resultados:** Foram identificadas e validadas credenciais de acesso ao serviço FTP. A análise do tráfego demonstrou a transmissão de informações de autenticação sem criptografia, e os testes também confirmaram o acesso a diretórios do sistema de arquivos.

**Ferramentas:** `Nmap` · `Hydra` · `Medusa` · `Wireshark` · `Kali Linux`

**Documentação técnica:**

[📄 Acessar Authentication Security Lab](metasploitable-2/ftp/authentication-security/README.md)

---

### 2. Metasploitable 2 — Backdoor do vsFTPd 2.3.4

<sub>Vulnerability Assessment · CVE-2011-2523 · TCP/21 · TCP/6200</sub>

**Objetivo:** Investigar e validar a backdoor associada à distribuição comprometida do vsFTPd 2.3.4, analisando seu mecanismo de ativação e as possibilidades de execução remota de comandos.

**Atividades realizadas:**

- 🔎 Identificação e enumeração do serviço FTP utilizando Nmap.
- 🧭 Análise do banner e do comportamento do serviço.
- 📚 Investigação do contexto técnico da CVE-2011-2523.
- 🔬 Análise do script de detecção NSE do Nmap.
- ⚔️ Validação da vulnerabilidade utilizando Nmap NSE.
- 🛠️ Exploração controlada utilizando o Metasploit Framework.
- 💻 Investigação da exploração manual por meio de FTP e Netcat.
- 🔐 Confirmação de execução remota de comandos com privilégios de `root`.
- 📑 Documentação das evidências e recomendações de mitigação.

**Resultados:** A vulnerabilidade foi validada por dois métodos: exploração automatizada com Metasploit Framework e interação manual com o serviço de shell disponibilizado pela backdoor. Foi confirmado acesso remoto com privilégios de `root` no sistema alvo.

**Ferramentas:** `Nmap` · `Metasploit Framework` · `Netcat` · `Kali Linux` · `Metasploitable 2`

**Documentação técnica:**

[📄 Acessar vsFTPd 2.3.4 Backdoor Lab](metasploitable-2/ftp/vsftpd-234-backdoor/README.md)

---

## 🧰 Ferramentas e Tecnologias

Ferramentas e tecnologias utilizadas nos laboratórios e no desenvolvimento dos estudos.

| Ferramenta / Tecnologia | Aplicação |
|---|---|
| 🔎 Nmap | Descoberta de hosts, varredura de portas, enumeração de serviços e detecção de vulnerabilidades. |
| ⚔️ Metasploit Framework | Validação e exploração controlada de vulnerabilidades. |
| 🔐 Hydra | Auditoria de mecanismos de autenticação utilizando ataques de dicionário. |
| 🔐 Medusa | Testes controlados de autenticação em serviços de rede. |
| 📡 Wireshark | Captura e análise de tráfego e protocolos de rede. |
| 💻 Netcat | Estabelecimento de conexões TCP e interação com serviços de rede. |
| 🐧 Linux | Utilização e administração de sistemas e ambientes de segurança. |
| 🐍 Python | Automação, scripting e desenvolvimento de ferramentas auxiliares. |
| 🌐 Burp Suite | Inspeção de tráfego HTTP e testes de segurança em aplicações web. |
| 🖥️ Virtualização | Criação de ambientes isolados para execução dos laboratórios. |

A presença de uma ferramenta nesta seção não significa que ela tenha sido utilizada em todos os laboratórios ou que represente domínio completo sobre a tecnologia.

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
| 07. Reporting | Documentação das evidências, descobertas e recomendações. |

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

As evidências são armazenadas no diretório `evidence/` de cada investigação. As fontes técnicas são organizadas no diretório `references/`.

## 📈 Desenvolvimento dos Estudos

Este repositório é atualizado continuamente conforme novos conhecimentos são adquiridos e novas investigações são realizadas.

O desenvolvimento dos estudos busca fortalecer a capacidade de:

- Compreender protocolos de rede e o comportamento de sistemas operacionais.
- Investigar serviços e identificar superfícies de ataque (*Attack Surface*).
- Compreender o funcionamento e as limitações das ferramentas de segurança.
- Validar descobertas e interpretar resultados tecnicamente.
- Analisar evidências e avaliar impactos na segurança.
- Documentar investigações de maneira clara e reproduzível.
- Identificar vulnerabilidades e compreender suas possíveis correções.

Novos ambientes, ferramentas e laboratórios serão incorporados conforme o avanço das investigações.

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

Este repositório destina-se exclusivamente a fins educacionais e ao desenvolvimento de conhecimentos em segurança da informação.

Todas as atividades práticas são realizadas em ambientes de laboratório isolados, em sistemas intencionalmente vulneráveis ou em infraestruturas para as quais existe autorização explícita.

As técnicas e ferramentas documentadas não devem ser utilizadas contra sistemas, redes ou serviços de terceiros sem a devida autorização.

## 🔗 Links

- [GitHub — Repositório](https://github.com/Diegouehara/cybersecurity-training-labs)
- [LinkedIn — Perfil profissional](https://www.linkedin.com/in/diego-uehara-010830272/)

---

<p align="center">
  <strong>🔎 Investigar. ⚔️ Compreender. 🛡️ Proteger.</strong>
</p>

<p align="center">
  <sub>Cybersecurity Training Labs · Portfólio de estudos e investigações práticas</sub>
</p>
