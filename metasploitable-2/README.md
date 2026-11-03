## 🧪 Laboratórios Concluídos

### Metasploitable 2 — Ambiente de Treinamento

Investigações práticas realizadas contra uma máquina Linux intencionalmente vulnerável, com foco em serviços FTP, autenticação e exploração de vulnerabilidades.

#### 🔐 FTP Authentication Security

<sub>Authentication Assessment · Hydra · Medusa · Wireshark · TCP/21</sub>

**Objetivo:** avaliar os mecanismos de autenticação FTP, identificar fragilidades relacionadas a credenciais e analisar a exposição de informações durante a comunicação.

**Atividades realizadas:**

- 🔎 Reconhecimento e enumeração do serviço FTP utilizando Nmap.
- 🔐 Análise de autenticação anônima e usuários locais.
- 🔬 Investigação do comportamento do servidor após falhas consecutivas de login.
- ⚔️ Auditoria de credenciais utilizando Hydra e Medusa.
- ✅ Validação manual das credenciais identificadas.
- 📡 Captura e análise de tráfego FTP utilizando Wireshark.
- 🔍 Identificação de credenciais transmitidas em texto claro.
- 📂 Análise da navegação e das permissões do sistema de arquivos.

**Resultado verificado:** identificação e validação de credenciais padrão de uma conta local, além da confirmação da exposição de comandos de autenticação FTP em texto claro.

**Ferramentas:** `Nmap` · `Hydra` · `Medusa` · `Wireshark` · `Kali Linux`

[Visualizar documentação completa](metasploitable-2/ftp/authentication-security/README.md)

#### 🛡️ vsFTPd 2.3.4 Backdoor

<sub>Vulnerability Investigation · CVE-2011-2523 · TCP/21 · TCP/6200</sub>

**Objetivo:** investigar, validar e explorar a backdoor associada a uma distribuição comprometida do vsFTPd 2.3.4.

**Atividades realizadas:**

- 🔎 Identificação e enumeração do serviço FTP utilizando Nmap.
- 📚 Investigação do contexto técnico da CVE-2011-2523.
- 🔬 Análise do código do script NSE de detecção.
- ⚔️ Validação da vulnerabilidade utilizando Nmap NSE.
- 🛠️ Exploração automatizada utilizando o Metasploit Framework.
- 🔧 Reprodução manual da exploração utilizando FTP e Netcat.
- 🔐 Confirmação de execução remota de comandos com privilégios de `root`.
- 📑 Documentação das evidências, impacto e recomendações de mitigação.

**Resultado verificado:** duas abordagens de exploração foram utilizadas para obter acesso remoto ao sistema alvo com privilégios de `root`: exploração automatizada com Metasploit e acionamento manual da backdoor com conexão direta ao Bind Shell na TCP/6200.

**Ferramentas:** `Nmap` · `Metasploit Framework` · `Netcat` · `Kali Linux`

[Visualizar documentação completa](metasploitable-2/ftp/vsftpd-234-backdoor/README.md)

---

