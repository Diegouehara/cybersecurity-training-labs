# 📚 Technical References — CVE-2011-2523

Este documento reúne as fontes técnicas utilizadas durante a investigação da backdoor associada ao vsFTPd 2.3.4.

As referências foram selecionadas para fundamentar a identificação da vulnerabilidade, a análise do mecanismo de detecção e a compreensão das ferramentas utilizadas no laboratório.

## 1. Vulnerability Information

### CVE-2011-2523

- **Fonte:** National Vulnerability Database (NVD)
- **Link:** https://nvd.nist.gov/vuln/detail/CVE-2011-2523
- **Finalidade:** Consultar a descrição técnica e as informações oficiais sobre a vulnerabilidade.

### Exploit-DB — Exploit 49757

- **Link:** https://www.exploit-db.com/exploits/49757
- **Finalidade:** Consultar o registro histórico relacionado à backdoor do vsFTPd 2.3.4.

## 2. Nmap — Vulnerability Detection

### ftp-vsftpd-backdoor NSE

- **Documentação:** https://nmap.org/nsedoc/scripts/ftp-vsftpd-backdoor.html
- **Código-fonte:** https://github.com/nmap/nmap/blob/master/scripts/ftp-vsftpd-backdoor.nse
- **Finalidade:** Compreender como o Nmap identifica o comportamento da backdoor, verifica a porta TCP/6200 e testa a execução do comando `id`.

## 3. Metasploit Framework

### vsftpd_234_backdoor

- **Código-fonte:** https://github.com/rapid7/metasploit-framework/blob/master/modules/exploits/unix/ftp/vsftpd_234_backdoor.rb
- **Finalidade:** Analisar a implementação do módulo utilizado para explorar a vulnerabilidade e estabelecer a sessão remota.

## 4. Historical Technical Analysis

### The vsftpd download backdoor

- **Fonte:** ScaryBeasts Security
- **Link:** http://scarybeastsecurity.blogspot.com/2011/07/alert-vsftpd-download-backdoored.html
- **Finalidade:** Consultar a análise histórica da distribuição comprometida do vsFTPd 2.3.4.

## 5. Scope and Usage

As referências foram utilizadas exclusivamente para a investigação da vulnerabilidade CVE-2011-2523 no serviço FTP, porta TCP/21.

Os testes práticos foram realizados em ambiente virtualizado e isolado, utilizando Kali Linux e Metasploitable 2.

**Escopo:** vsFTPd 2.3.4 Backdoor — TCP/21.
