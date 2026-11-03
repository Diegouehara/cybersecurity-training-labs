# 📚 Referências Técnicas — CVE-2011-2523

Este documento reúne as fontes técnicas utilizadas durante a investigação da backdoor associada à distribuição comprometida do vsFTPd 2.3.4.

As referências foram organizadas por finalidade, abrangendo o contexto histórico da vulnerabilidade, o funcionamento do protocolo FTP, os mecanismos de detecção do Nmap e as ferramentas utilizadas nos métodos de exploração.

## 1. Vulnerabilidade e contexto histórico

### CVE-2011-2523 — National Vulnerability Database (NVD)

- **Fonte:** National Institute of Standards and Technology (NIST).
- **Link:** https://nvd.nist.gov/vuln/detail/CVE-2011-2523
- **Finalidade:** Consultar a descrição técnica, a classificação de severidade e as informações oficiais sobre a vulnerabilidade.

A referência identifica a distribuição comprometida do vsFTPd 2.3.4 disponibilizada entre 30 de junho e 3 de julho de 2011, que continha uma backdoor capaz de disponibilizar um shell na TCP/6200.

### Exploit-DB — Exploit 49757

- **Fonte:** Exploit Database.
- **Link:** https://www.exploit-db.com/exploits/49757
- **Finalidade:** Consultar o registro histórico e a prova de conceito relacionada à backdoor do vsFTPd 2.3.4.

### Análise histórica — ScaryBeasts Security

- **Fonte:** ScaryBeasts Security.
- **Link:** https://scarybeastsecurity.blogspot.com/2011/07/alert-vsftpd-download-backdoored.html
- **Finalidade:** Consultar a análise original sobre a identificação da distribuição comprometida do vsFTPd 2.3.4, publicada em julho de 2011.

## 2. Protocolo FTP

### RFC 959 — File Transfer Protocol

- **Fonte:** RFC Editor.
- **Link:** https://www.rfc-editor.org/rfc/rfc959.html
- **Finalidade:** Consultar a especificação do protocolo FTP, incluindo a estrutura das conexões, os comandos de controle e o processo de autenticação por meio de `USER` e `PASS`.

Essa referência auxilia na compreensão da comunicação entre o cliente FTP e o servidor, incluindo a sequência de comandos utilizada durante a investigação da backdoor.

## 3. Nmap — Detecção de vulnerabilidades

### ftp-vsftpd-backdoor NSE

- **Documentação:** https://nmap.org/nsedoc/scripts/ftp-vsftpd-backdoor.html
- **Código-fonte:** https://github.com/nmap/nmap/blob/master/scripts/ftp-vsftpd-backdoor.nse
- **Finalidade:** Compreender o funcionamento do script NSE utilizado para investigar a presença da backdoor, acionar o mecanismo de teste e executar o comando `id` por padrão.

A documentação também apresenta exemplos de utilização e resultados esperados durante a validação da vulnerabilidade.

## 4. Metasploit Framework

### vsftpd_234_backdoor

- **Código-fonte:** https://github.com/rapid7/metasploit-framework/blob/master/modules/exploits/unix/ftp/vsftpd_234_backdoor.rb
- **Finalidade:** Analisar a implementação do módulo utilizado na exploração automatizada, incluindo o acionamento da backdoor pelo serviço FTP e a interação com o shell disponibilizado na TCP/6200.

A implementação permite compreender como o Metasploit automatiza etapas que também podem ser realizadas manualmente.

## 5. Netcat — Conexões TCP

### nc — Netcat Manual

- **Documentação:** https://man.openbsd.org/nc
- **Finalidade:** Consultar o funcionamento do utilitário `nc` para estabelecer conexões TCP e interagir com serviços de rede.

Essa referência auxilia na compreensão da conexão direta estabelecida com o Bind Shell disponibilizado pela backdoor na TCP/6200.

**Observação:** opções e comportamentos específicos podem variar conforme a implementação do Netcat instalada no sistema.

## 6. Escopo e utilização das referências

As fontes reunidas neste documento apoiam a investigação da CVE-2011-2523 e dos mecanismos utilizados para validar e explorar a backdoor associada ao vsFTPd 2.3.4.

Os testes práticos foram realizados em ambiente virtualizado e isolado, utilizando Kali Linux como máquina de análise e Metasploitable 2 como sistema alvo.

**Escopo da investigação:**

- Serviço FTP — TCP/21.
- Bind Shell disponibilizado pela backdoor — TCP/6200.
- Validação com Nmap NSE.
- Exploração automatizada com Metasploit Framework.
- Exploração manual com FTP e Netcat.

---

- **Laboratório:** vsFTPd 2.3.4 Backdoor.
- **Vulnerabilidade:** CVE-2011-2523.
- **Escopo:** TCP/21 e TCP/6200.
- **Ambiente:** laboratório virtual isolado.
