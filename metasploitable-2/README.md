# 🎯 Metasploitable 2 — Avaliação de Segurança

## 📋 Visão Geral

Este diretório reúne investigações práticas de segurança realizadas contra o **Metasploitable 2**, uma máquina virtual Linux intencionalmente vulnerável, desenvolvida para treinamento em cybersecurity e prática de *Penetration Testing*.

O objetivo é investigar serviços expostos, compreender vulnerabilidades de segurança, validar descobertas em um ambiente controlado e documentar seus impactos técnicos e estratégias de mitigação.

Todas as atividades são realizadas em uma rede virtual isolada.

## 🖥️ Ambiente de Laboratório

| Componente | Configuração |
|---|---|
| Sistema alvo (*Target*) | Metasploitable 2 |
| Sistema operacional | Ubuntu Linux 8.04 |
| Virtualização | Máquina virtual (*Virtual Machine*) |
| Rede | Rede isolada de laboratório |
| Máquina de testes | Kali Linux |

## 🔬 Investigações de Vulnerabilidades

Cada investigação é documentada de forma independente, com seu próprio relatório técnico, evidências e referências.

| Investigação | Vulnerabilidade | Status |
|---|---|---|
| [Backdoor do vsFTPd 2.3.4](vsftpd-234-backdoor/README.md) | CVE-2011-2523 · TCP/21 | Concluído |

Novas investigações serão documentadas conforme forem realizadas e validadas.

## 📑 Estrutura da Documentação

Cada diretório de laboratório pode conter:

- **README.md:** relatório técnico, metodologia, descobertas, impacto e medidas de mitigação.
- **evidence/:** capturas de tela e evidências técnicas de apoio.
- **references/:** documentação oficial e fontes utilizadas na pesquisa.

## ⚠️ Escopo e Autorização

Todos os testes são realizados contra a máquina virtual Metasploitable 2, intencionalmente vulnerável, em um ambiente isolado sob meu controle.

As técnicas documentadas destinam-se exclusivamente a fins educacionais e a atividades de testes de segurança devidamente autorizadas.

---

<p align="center">
  <sub>Metasploitable 2 · Ambiente de Treinamento em Cybersecurity</sub>
</p>
