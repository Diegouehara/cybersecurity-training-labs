# 📁 FTP — Análise de Segurança

<p align="center">
  <img src="https://img.shields.io/badge/Service-FTP-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Protocol-TCP%2F21-orange?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Focus-Network%20Security-red?style=for-the-badge" />
</p>

<p align="center">
  <strong>Investigação de segurança do serviço FTP no ambiente Metasploitable 2, abrangendo autenticação, exposição de informações e vulnerabilidades do vsFTPd.</strong>
</p>

---

## 📖 1. Visão geral

O **File Transfer Protocol (FTP)** é um protocolo de rede utilizado para transferir arquivos entre um cliente e um servidor.

Tradicionalmente, utiliza a porta TCP/21 para o canal de controle, responsável pela troca de comandos e respostas entre as partes. A transferência de dados ocorre por meio de conexões próprias, estabelecidas conforme o modo de operação ativo ou passivo.

O protocolo FTP tradicional não oferece criptografia nativa para proteger a comunicação. Consequentemente, informações como comandos de autenticação e credenciais podem ser transmitidas em texto claro.

Neste ambiente, a investigação está direcionada ao serviço FTP disponibilizado pelo servidor **vsftpd**, instalado na máquina Metasploitable 2.

## 🖥️ 2. Serviço identificado no ambiente

Durante o reconhecimento da máquina alvo, foi identificado o seguinte serviço:

| Informação | Resultado |
|---|---|
| Serviço | FTP |
| Implementação | vsftpd |
| Versão identificada | 2.3.4 |
| Porta de controle | TCP/21 |
| Máquina alvo | Metasploitable 2 |
| Endereço IP | `192.168.100.10` |

**Resultado observado com Nmap:**

```text
21/tcp open ftp vsftpd 2.3.4
```

O banner identificado foi utilizado como ponto de partida para investigar a implementação do serviço e suas possíveis fragilidades.

## 🔬 3. Aspectos de segurança investigados

A análise do serviço FTP contempla diferentes aspectos que podem comprometer a segurança de um servidor.

### 🔐 Autenticação e controle de acesso

Investigação dos mecanismos de autenticação, incluindo:

- Autenticação de usuários locais.
- Acesso anônimo, quando permitido pela configuração.
- Utilização de credenciais padrão ou fracas.
- Comportamento do servidor após tentativas consecutivas de autenticação.
- Restrições de acesso aos diretórios e arquivos.

### 📡 Exposição de informações e tráfego

Análise da comunicação entre cliente e servidor FTP, considerando:

- Transmissão de comandos e credenciais.
- Ausência de criptografia no FTP tradicional.
- Identificação de informações expostas durante a comunicação.
- Captura e interpretação de pacotes de rede.

### 💥 Vulnerabilidades do vsFTPd 2.3.4

Investigação da backdoor associada à **CVE-2011-2523**, presente em uma distribuição comprometida do vsFTPd 2.3.4 disponibilizada em 2011.

O mecanismo malicioso pode ser acionado por meio de uma sequência especial no processo de autenticação FTP, disponibilizando um shell remoto na TCP/6200.

É importante destacar que a vulnerabilidade está associada à distribuição comprometida, não necessariamente a todas as instalações legítimas do vsFTPd 2.3.4.

## 🧪 4. Investigações relacionadas

As investigações realizadas contra o serviço FTP estão organizadas em relatórios independentes.

### 🔐 FTP Authentication Security

**Escopo:** mecanismos de autenticação, auditoria de credenciais, análise de tráfego e acesso ao sistema de arquivos.

**Ferramentas:** `Nmap` · `Hydra` · `Medusa` · `Wireshark`

[📄 Consultar documentação da investigação](authentication-security/README.md)

### 🛡️ vsFTPd 2.3.4 Backdoor

**Escopo:** investigação e exploração da CVE-2011-2523, incluindo validação com Nmap NSE, exploração automatizada com Metasploit Framework e exploração manual com FTP e Netcat.

**Portas investigadas:** TCP/21 e TCP/6200.

**Ferramentas:** `Nmap` · `Metasploit Framework` · `Netcat`

[📄 Consultar documentação da vulnerabilidade](vsftpd-234-backdoor/README.md)

## 🧰 5. Ferramentas utilizadas

| Ferramenta | Aplicação |
|---|---|
| Nmap | Reconhecimento, enumeração e validação de vulnerabilidades. |
| Hydra | Auditoria de mecanismos de autenticação por meio de ataques de dicionário. |
| Medusa | Testes automatizados de autenticação em serviços de rede. |
| Wireshark | Captura e análise do tráfego FTP. |
| Metasploit Framework | Exploração controlada da CVE-2011-2523. |
| Netcat | Estabelecimento de conexão TCP e interação com o Bind Shell disponibilizado pela backdoor. |
| Cliente FTP | Interação manual com o serviço e análise do processo de autenticação. |

## 📑 6. Organização da documentação

Cada investigação possui uma estrutura independente para facilitar a consulta e a reprodução dos procedimentos.

```text
ftp/
├── README.md
├── authentication-security/
│   ├── README.md
│   ├── evidence/
│   └── references/
└── vsftpd-234-backdoor/
    ├── README.md
    ├── evidence/
    └── references/
```

- **README.md:** relatório técnico da investigação.
- **evidence/:** capturas de tela e evidências técnicas.
- **references/:** documentação oficial e fontes utilizadas durante a análise.

## ⚠️ 7. Escopo e autorização

Todas as atividades foram realizadas em um ambiente virtualizado e isolado, utilizando o Metasploitable 2 como sistema alvo e Kali Linux como máquina de análise.

As técnicas e ferramentas documentadas destinam-se exclusivamente a fins educacionais e a testes de segurança em ambientes próprios ou explicitamente autorizados.

---

<p align="center">
  <strong>🔎 Reconhecer. 📡 Analisar. 🔬 Investigar. 🛡️ Proteger.</strong>
</p>

<p align="center">
  <sub>FTP · Security Assessment · Metasploitable 2</sub>
</p>
