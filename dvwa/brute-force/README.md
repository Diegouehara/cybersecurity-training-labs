# 🔐 DVWA — Brute Force Authentication

> Investigação prática de autenticação web, tentativas automatizadas de descoberta de credenciais e análise dos mecanismos de proteção implementados em diferentes níveis de segurança.

## 📌 1. Visão geral

Este laboratório investiga o formulário de autenticação do módulo **Brute Force** do Damn Vulnerable Web Application (DVWA).

O objetivo é compreender como a aplicação recebe e valida credenciais, como as requisições HTTP são construídas e de que maneira os mecanismos de segurança influenciam a resistência a tentativas automatizadas.

A investigação está dividida em três etapas: **Low**, **Medium** e **Impossible**. Cada nível será analisado por meio de testes controlados e, quando aplicável, inspeção do código-fonte.

Atualmente, a etapa Low foi concluída. Os níveis Medium e Impossible permanecem pendentes.

## 🎯 2. Objetivos

- 🔎 Analisar o funcionamento do formulário de autenticação.
- 🌐 Identificar parâmetros, métodos e respostas HTTP.
- 🍪 Compreender o papel dos cookies e do gerenciamento de sessões.
- 🔬 Investigar a implementação da autenticação no código-fonte PHP.
- ⚔️ Utilizar Medusa para auditoria controlada de credenciais.
- ✅ Validar manualmente os resultados obtidos pelas ferramentas.
- 📊 Comparar os mecanismos de proteção dos diferentes níveis.
- 🛡️ Identificar medidas de mitigação contra ataques de força bruta.
- 📸 Registrar evidências e documentar os resultados.

## 🖥️ 3. Ambiente de laboratório

| Componente | Configuração |
|---|---|
| Aplicação | DVWA |
| Sistema de análise | Kali Linux |
| Hospedagem | Docker |
| Gerenciamento | Docker Compose |
| Endereço local | `http://127.0.0.1:4280` |
| Módulo | Brute Force |
| Ferramenta principal | Medusa 2.3 |
| Inspeção HTTP | Firefox DevTools |
| Protocolo observado | HTTP |

### 🧰 Ferramentas utilizadas

- 🐧 Kali Linux
- 🐳 Docker e Docker Compose
- 🔐 Medusa
- 🌐 Firefox DevTools
- 💻 Terminal Linux

## 🧪 4. Etapas da investigação

### 4.1. 🔓 Security Level — Low

**Status: ✅ Concluído**

**Objetivo:** analisar o comportamento do formulário de autenticação no nível Low e verificar sua resistência a tentativas automatizadas de descoberta de credenciais.

#### Atividades realizadas

- 🔎 Inspeção do formulário de autenticação.
- 🌐 Identificação dos parâmetros `username`, `password` e `Login`.
- 🔍 Identificação do método HTTP GET.
- 🍪 Análise dos cookies `PHPSESSID` e `security`.
- 🔬 Análise do código-fonte PHP responsável pela autenticação.
- 🔐 Investigação do processamento de senhas com MD5.
- ⚔️ Configuração e utilização do módulo `web-form` do Medusa.
- 📊 Inspeção das respostas HTTP e das mensagens de falha.
- ✅ Identificação automatizada de uma combinação válida para a conta `admin`.
- 🧪 Validação manual da autenticação no navegador.

#### Análise técnica

**1. Requisição HTTP**

O formulário envia os parâmetros de autenticação por meio de uma requisição GET. Os campos observados foram:

| Parâmetro | Finalidade |
|---|---|
| `username` | Nome da conta submetida |
| `password` | Senha submetida |
| `Login` | Identificação da ação de autenticação |

Como os dados são enviados na URL, os parâmetros podem ser observados na requisição HTTP e no painel de rede do navegador.

**2. Gerenciamento de sessão**

Durante a análise foram identificados dois cookies relevantes:

- `PHPSESSID`: identificador utilizado para manter a sessão da aplicação.
- `security`: indica o nível de segurança configurado no DVWA, neste caso `low`.

O identificador de sessão foi ocultado na evidência da configuração do Medusa. O valor completo não é necessário para compreender o procedimento.

**3. Análise do código-fonte**

O trecho analisado utiliza o método GET para receber os dados, aplica MD5 à senha e monta a consulta SQL por concatenação de valores.

Foram observados dois pontos relevantes:

- **MD5:** é uma função de hash considerada inadequada para armazenamento seguro de senhas. Não é criptografia reversível.
- **Concatenação SQL:** a construção da consulta com valores recebidos diretamente da requisição pode introduzir risco de SQL Injection. Essa possibilidade foi identificada na análise do código, mas não foi explorada neste laboratório.

**4. Comportamento da autenticação**

O formulário apresentou a mensagem:

`Username and/or password incorrect.`

A mensagem foi utilizada como sinal de falha na configuração do módulo `web-form` do Medusa.

O Medusa identificou uma combinação válida para a conta `admin`. A descoberta foi confirmada manualmente no navegador, onde a aplicação apresentou a mensagem:

`Welcome to the password protected area admin`

A resposta HTTP `200 OK` foi observada durante a validação, mas o código de status, isoladamente, não foi tratado como prova de autenticação bem-sucedida. A confirmação foi feita pela resposta funcional da própria aplicação.

**5. Interpretação do Medusa**

Durante os testes, foi observado que:

- A opção `-f` encerra a execução após a identificação de uma combinação válida.
- O parâmetro `-t` controla a quantidade de tarefas concorrentes. A intercalação das tentativas causada pelo paralelismo não significa que a ordem foi aleatorizada.
- A identificação de uma combinação pelo Medusa deve ser validada contra o comportamento real da aplicação.

#### Resultado obtido

O nível Low permitiu a identificação automatizada de uma combinação válida para a conta `admin`, posteriormente confirmada por autenticação manual.

Durante os testes realizados, não foi observado um mecanismo efetivo de limitação de tentativas, bloqueio temporário ou atraso progressivo no fluxo analisado.

#### 📸 Evidências — Security Level Low

| Arquivo | Descrição |
|---|---|
| [01 — Invalid Authentication](evidence/low/01-invalid-authentication.png) | Mensagem exibida após uma tentativa de autenticação inválida. |
| [02 — HTTP GET Parameters](evidence/low/02-http-get-parameters.png) | Identificação dos parâmetros enviados pelo formulário. |
| [03 — HTTP Request Inspection](evidence/low/03-http-request-inspection.png) | Inspeção da requisição GET realizada pelo navegador. |
| [04 — Medusa Configuration](evidence/low/04-medusa-configuration.png) | Configuração do módulo `web-form` e dos parâmetros utilizados no teste. |
| [05 — Credential Discovery](evidence/low/05-medusa-credential-discovery.png) | Resultado do Medusa indicando uma combinação válida. |
| [06 — Manual Credential Validation](evidence/low/06-manual-credential-validation.png) | Preparação da validação manual no formulário. |
| [07 — Successful Authentication](evidence/low/07-successful-authentication.png) | Confirmação da autenticação e inspeção da resposta da aplicação. |

---

### 4.2. ⏱️ Security Level — Medium

**Status: ⏳ Pendente**

**Objetivo:** investigar os mecanismos adicionais de proteção implementados no nível Medium e comparar seu comportamento com o nível Low.

#### Atividades previstas

- 🔬 Análise do código-fonte `medium.php`.
- 🔎 Identificação das alterações em relação ao nível Low.
- ⏱️ Investigação de atrasos aplicados após falhas de autenticação.
- 🌐 Observação do comportamento e do tempo de resposta HTTP.
- ⚔️ Repetição controlada dos testes de autenticação.
- 📊 Comparação dos resultados com o nível Low.
- 🛡️ Avaliação das limitações dos mecanismos implementados.

As conclusões desta etapa serão registradas somente após a realização e análise dos testes.

---

### 4.3. 🛡️ Security Level — Impossible

**Status: ⏳ Pendente**

**Objetivo:** investigar os mecanismos de proteção implementados no nível Impossible e compreender como eles alteram o processo de autenticação.

#### Atividades previstas

- 🔬 Análise do código-fonte `impossible.php`.
- 🌐 Investigação do método HTTP e dos parâmetros utilizados.
- 🧩 Análise do mecanismo anti-CSRF.
- 🔐 Investigação do uso de consultas parametrizadas (*Prepared Statements*).
- 🚫 Análise do controle de tentativas de autenticação.
- 🔒 Investigação de possíveis mecanismos de bloqueio temporário.
- ⏱️ Observação dos atrasos aplicados após falhas.
- 📊 Comparação com os níveis Low e Medium.

As conclusões desta etapa serão registradas somente após a realização e análise dos testes.

## 📊 5. Comparação dos níveis de segurança

A tabela será atualizada à medida que as etapas forem concluídas.

| Característica | Low | Medium | Impossible |
|---|---|---|---|
| Teste prático | ✅ Realizado | ⏳ Pendente | ⏳ Pendente |
| Método HTTP | GET observado | A verificar | A verificar |
| Atraso após falha | Não observado nos testes | A verificar | A verificar |
| Controle de tentativas | Não observado nos testes | A verificar | A verificar |
| Bloqueio temporário | Não observado nos testes | A verificar | A verificar |
| Proteção anti-CSRF | Não identificada no fluxo analisado | A verificar | A verificar |
| Prepared Statements | Não utilizados no trecho analisado | A verificar | A verificar |

Os resultados serão baseados nas observações práticas e na análise do código-fonte de cada nível.

## 🔬 6. Interpretação técnica

Durante a investigação, os seguintes aspectos serão considerados:

### Requisições HTTP

- Método utilizado pelo formulário.
- Parâmetros enviados.
- Cabeçalhos HTTP.
- Cookies de sessão.
- Códigos de resposta.
- Redirecionamentos e mensagens retornadas.

### Mecanismos de autenticação

- Processamento e validação de credenciais.
- Armazenamento e comparação de senhas.
- Controle de falhas consecutivas.
- Limitação de frequência das tentativas.
- Proteções contra automação.

### Validação dos resultados

Uma resposta HTTP `200 OK`, isoladamente, não comprova que a autenticação foi bem-sucedida.

Os resultados obtidos pelas ferramentas devem ser comparados com o comportamento funcional da aplicação e, sempre que possível, validados manualmente.

## 🛡️ 7. Mecanismos de mitigação

Entre as medidas que serão estudadas durante o laboratório estão:

- **Rate Limiting:** limitação da frequência de tentativas.
- **Account Lockout:** bloqueio temporário após sucessivas falhas, com atenção aos riscos de negação de serviço.
- **Progressive Delay:** aumento progressivo do intervalo entre tentativas.
- **CAPTCHA:** mecanismo adicional para dificultar automação.
- **Multi-Factor Authentication:** camada adicional de autenticação.
- **Password Hashing:** utilização de algoritmos próprios para armazenamento de senhas, como Argon2id ou bcrypt.
- **Prepared Statements:** separação entre instruções SQL e dados fornecidos pelo usuário.
- **HTTPS/TLS:** proteção dos dados durante a transmissão.

HTTPS protege os dados em trânsito, mas não impede, por si só, tentativas automatizadas de adivinhação de credenciais. Da mesma forma, tokens anti-CSRF têm como finalidade principal mitigar ataques de falsificação de requisições, não substituir controles contra brute force.

## 📚 8. Referências técnicas

As fontes utilizadas como apoio à investigação estão organizadas em:

[📚 Acessar referências técnicas](references/README.md)

## 🏁 9. Conclusão

A etapa Low demonstrou, por meio de testes controlados, que foi possível identificar uma combinação válida de credenciais utilizando Medusa e confirmar manualmente a autenticação na aplicação.

Além da execução prática, a investigação permitiu observar o envio de parâmetros por GET, compreender o papel dos cookies de sessão, analisar o processamento de senhas e interpretar corretamente as respostas HTTP.

As próximas etapas serão dedicadas à análise dos níveis Medium e Impossible, permitindo comparar os mecanismos de proteção e compreender suas diferenças de implementação e comportamento.

## ⚠️ Aviso legal e ético

Todos os testes foram realizados em ambiente local e controlado, utilizando uma aplicação intencionalmente vulnerável para fins educacionais.

As técnicas documentadas não devem ser utilizadas contra sistemas ou aplicações de terceiros sem autorização explícita.

---

<p align="center">
  <strong>🔎 Investigar · 🔬 Compreender · ⚔️ Validar · 🛡️ Proteger</strong>
</p>
