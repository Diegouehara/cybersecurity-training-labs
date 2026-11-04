# 🕸️ DVWA — Damn Vulnerable Web Application

> Ambiente de treinamento dedicado ao estudo de segurança em aplicações web, análise de vulnerabilidades e validação controlada de mecanismos de proteção.

## 📌 Visão geral

O **Damn Vulnerable Web Application (DVWA)** é uma aplicação web intencionalmente vulnerável, desenvolvida para o aprendizado e a prática de segurança de aplicações.

Neste ambiente são investigados mecanismos de autenticação, processamento de requisições HTTP, gerenciamento de sessões e vulnerabilidades comuns em aplicações web.

A aplicação é executada localmente em um ambiente controlado, utilizando Docker e Kali Linux para os testes.

## 🎯 Objetivos

- 🔎 Investigar vulnerabilidades em aplicações web.
- 🌐 Analisar requisições e respostas HTTP.
- 🔐 Compreender mecanismos de autenticação e controle de acesso.
- 🍪 Investigar gerenciamento de sessões e cookies.
- 🔬 Analisar implementações vulneráveis por meio do código-fonte.
- ⚔️ Realizar testes controlados com ferramentas de segurança.
- 🛡️ Identificar limitações e estudar mecanismos de mitigação.
- 📸 Documentar procedimentos, evidências e resultados.

## 🖥️ Ambiente utilizado

| Componente | Configuração |
|---|---|
| Aplicação | DVWA |
| Sistema de análise | Kali Linux |
| Hospedagem | Docker |
| Gerenciamento | Docker Compose |
| Endereço local | `http://127.0.0.1:4280` |

## 🧪 Laboratórios

As investigações são organizadas em relatórios independentes. Cada laboratório reúne seus objetivos, procedimentos, análise técnica, evidências e referências.

### 1. 🔐 Brute Force Authentication

<sub>Web Application Security · Authentication Security · HTTP · Medusa</sub>

**Objetivo:** investigar a resistência do formulário de autenticação do DVWA a tentativas automatizadas de descoberta de credenciais.

**Escopo:**

- 🔎 Inspeção do formulário e dos parâmetros HTTP.
- 🍪 Análise dos cookies e do gerenciamento de sessões.
- 🔬 Análise do código-fonte PHP responsável pela autenticação.
- ⚔️ Testes controlados utilizando Medusa.
- 📊 Comparação dos níveis de segurança Low, Medium e Impossible.
- 🛡️ Estudo dos mecanismos de proteção e suas limitações.

**Progresso do laboratório:**

| Nível | Situação |
|---|---|
| Low | ✅ Concluído |
| Medium | ⏳ Pendente |
| Impossible | ⏳ Pendente |

**Documentação técnica:**

[📄 Acessar Brute Force Authentication](brute-force/README.md)

## 📈 Evolução dos estudos

Novas investigações serão adicionadas conforme o avanço dos estudos e a realização de novos testes práticos.

Cada relatório será atualizado com base nos resultados efetivamente observados. Etapas ainda não executadas serão identificadas como pendentes.

## ⚠️ Aviso legal e ético

Todas as atividades são realizadas exclusivamente em ambiente local e controlado, utilizando uma aplicação intencionalmente vulnerável para fins educacionais.

As técnicas documentadas não devem ser utilizadas contra sistemas ou serviços de terceiros sem autorização explícita.
