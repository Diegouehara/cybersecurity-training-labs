# 📚 Referências Técnicas — FTP Authentication Security

Este documento reúne as fontes técnicas utilizadas como apoio à investigação da segurança de autenticação do serviço FTP disponível no ambiente Metasploitable 2.

As referências estão organizadas por finalidade, abrangendo o funcionamento do protocolo FTP, os mecanismos de autenticação, a identificação de serviços, a auditoria controlada de credenciais e a análise de tráfego de rede.

## 1. Protocolo FTP e segurança

### RFC 959 — File Transfer Protocol

- **Fonte:** RFC Editor.
- **Link:** https://www.rfc-editor.org/rfc/rfc959.html
- **Finalidade:** Consultar a especificação do protocolo FTP, incluindo comandos de controle, respostas do servidor, autenticação e transferência de arquivos.

### RFC 2577 — FTP Security Considerations

- **Fonte:** Internet Engineering Task Force (IETF).
- **Link:** https://www.rfc-editor.org/rfc/rfc2577.html
- **Finalidade:** Investigar os riscos de segurança relacionados ao FTP, incluindo exposição de senhas, tentativas consecutivas de autenticação, ataques de adivinhação de credenciais e recomendações para proteção do serviço.

Essa referência é especialmente relevante para compreender os riscos identificados durante os testes de autenticação.

## 2. Nmap — Reconhecimento e enumeração

### Nmap Reference Guide — Service and Version Detection

- **Documentação:** https://nmap.org/man/pt_BR/man-version-detection.html
- **Finalidade:** Compreender os mecanismos de detecção de serviços e versões utilizados pelo Nmap, especialmente a opção `-sV`, empregada no reconhecimento do serviço FTP.

### Nmap — Official Documentation

- **Documentação:** https://nmap.org/book/man.html
- **Finalidade:** Consultar a documentação geral da ferramenta, incluindo opções de varredura, identificação de serviços e recursos de enumeração.

## 3. Hydra — Auditoria de credenciais

### THC Hydra

- **Projeto:** https://github.com/vanhauser-thc/thc-hydra
- **Manual:** https://github.com/vanhauser-thc/thc-hydra/blob/master/hydra.1
- **Finalidade:** Consultar a documentação do Hydra, seus parâmetros de execução, utilização de listas de usuários e senhas, opções de concorrência e suporte ao protocolo FTP.

A documentação auxilia na compreensão dos procedimentos utilizados durante a auditoria controlada de credenciais.

## 4. Medusa — Auditoria de autenticação

### Medusa — Foofus Networking Services

- **Documentação:** https://jmk-foofus.github.io/medusa/medusa.html
- **Finalidade:** Consultar o funcionamento da ferramenta Medusa, sua arquitetura modular, opções de execução e módulos disponíveis para testes de autenticação em serviços de rede, incluindo FTP.

Essa referência permite compreender os parâmetros utilizados nos testes e o funcionamento do módulo FTP.

## 5. Wireshark — Análise de tráfego

### Wireshark User's Guide

- **Documentação:** https://www.wireshark.org/docs/wsug_html/
- **Finalidade:** Consultar os recursos de captura, inspeção e análise de pacotes de rede, incluindo a interpretação de protocolos e o acompanhamento de fluxos de comunicação.

### Wireshark — Display Filters

- **Documentação:** https://www.wireshark.org/docs/wsug_html_chunked/ChWorkDisplayFilterSection
- **Finalidade:** Compreender a utilização de filtros de exibição para localizar e analisar pacotes específicos durante a investigação do tráfego FTP.

## 6. vsftpd — Configuração do serviço

### vsftpd.conf — Configuration Reference

- **Fonte:** vsftpd.
- **Documentação:** https://security.appspot.com/vsftpd/vsftpd_conf.html
- **Finalidade:** Consultar as diretivas de configuração do servidor vsftpd, incluindo opções relacionadas à autenticação anônima, usuários locais, permissões de escrita e restrições de acesso.

Essa documentação auxilia na interpretação das configurações observadas durante a investigação do serviço.

## 7. Escopo e utilização das referências

As fontes reunidas neste documento apoiam a investigação dos mecanismos de autenticação e das condições de segurança do serviço FTP no ambiente Metasploitable 2.

Os testes práticos envolveram:

- Reconhecimento e identificação da versão do serviço FTP.
- Investigação da autenticação anônima e de usuários locais.
- Análise das respostas do servidor após falhas consecutivas de autenticação.
- Auditoria controlada de credenciais com Hydra e Medusa.
- Validação manual das credenciais identificadas.
- Captura e análise de tráfego FTP com Wireshark.
- Investigação da exposição de comandos e informações de autenticação em texto claro.
- Análise da navegação e do acesso ao sistema de arquivos após a autenticação.

- **Ambiente:** laboratório virtual isolado.
- **Alvo:** Metasploitable 2.
- **Serviço investigado:** FTP — vsftpd 2.3.4.
- **Porta:** TCP/21.
