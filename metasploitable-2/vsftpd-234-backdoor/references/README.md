# 📚 Referências Técnicas — CVE-2011-2523

Este documento reúne as fontes técnicas utilizadas durante a investigação da backdoor associada à distribuição comprometida do vsFTPd 2.3.4.

As referências estão organizadas de acordo com sua finalidade, abrangendo a identificação da vulnerabilidade, o funcionamento do protocolo FTP, os mecanismos de detecção do Nmap e a implementação dos métodos de exploração utilizados no laboratório.

## 1. Vulnerabilidade e contexto histórico

### CVE-2011-2523 — National Vulnerability Database (NVD)

- **Fonte:** National Institute of Standards and Technology (NIST)
- **Link:** https://nvd.nist.gov/vuln/detail/CVE-2011-2523
- **Finalidade:** Consultar a descrição técnica, a classificação de severidade e as informações oficiais sobre a vulnerabilidade.

### Exploit-DB — Exploit 49757

- **Fonte:** Exploit Database
- **Link:** https://www.exploit-db.com/exploits/49757
- **Finalidade:** Consultar uma implementação de prova de conceito (*Proof of Concept — PoC*) relacionada à backdoor do vsFTPd 2.3.4.

### Análise histórica — ScaryBeasts Security

- **Autor:** Chris Evans
- **Link:** https://scarybeastsecurity.blogspot.com/2011/07/alert-vsftpd-download-backdoored.html
- **Finalidade:** Consultar o relato original sobre a identificação da distribuição comprometida do vsFTPd 2.3.4, publicado em julho de 2011.

## 2. Protocolo FTP

### RFC 959 — File Transfer Protocol

- **Fonte:** RFC Editor
- **Link:** https://www.rfc-editor.org/rfc/rfc959.html
- **Finalidade:** Consultar a especificação do protocolo FTP, incluindo a estrutura das conexões, os comandos de controle e o processo de autenticação por meio de `USER` e `PASS`.

## 3. Nmap — Detecção de vulnerabilidades

### ftp-vsftpd-backdoor NSE

- **Documentação:** https://nmap.org/nsedoc/scripts/ftp-vsftpd-backdoor.html
- **Código-fonte:** https://github.com/nmap/nmap/blob/master/scripts/ftp-vsftpd-backdoor.nse
- **Finalidade:** Compreender o funcionamento do script NSE utilizado para investigar a presença da backdoor, verificar o serviço na TCP/6200 e testar a execução do comando `id`.

## 4. Metasploit Framework

### vsftpd_234_backdoor

- **Código-fonte:** https://github.com/rapid7/metasploit-framework/blob/master/modules/exploits/unix/ftp/vsftpd_234_backdoor.rb
- **Finalidade:** Analisar a implementação do módulo de exploração, incluindo o acionamento da backdoor pelo serviço FTP, a conexão com o shell disponibilizado na TCP/6200 e os métodos de obtenção de uma sessão remota.

## 5. Netcat — Conexões TCP

### nc — NetBSD Manual Pages

- **Documentação:** https://man.netbsd.org/nc.1
- **Finalidade:** Consultar o funcionamento do utilitário `nc` (*Netcat*) para estabelecer conexões TCP e interagir com serviços de rede.

**Observação:** as opções e o comportamento podem variar conforme a implementação de Netcat instalada no sistema utilizado.

## 6. Escopo das referências

As fontes reunidas neste documento apoiam a investigação da CVE-2011-2523 e dos mecanismos utilizados para validar e explorar a backdoor associada ao vsFTPd 2.3.4.

Os testes práticos foram realizados em ambiente virtualizado e isolado, utilizando Kali Linux como máquina de análise e Metasploitable 2 como sistema alvo.

**Escopo:** vsFTPd 2.3.4 Backdoor — TCP/21 e TCP/6200.

