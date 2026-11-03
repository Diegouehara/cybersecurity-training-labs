# 🔐 Metasploitable 2 — FTP Authentication Security Assessment

> Investigação prática de segurança sobre autenticação FTP, credenciais padrão, ataques de dicionário, gerenciamento de conexões TCP e exposição de informações por meio de comunicação sem criptografia.

## 📌 1. Visão geral

Este laboratório documenta uma investigação de segurança realizada contra o serviço FTP do Metasploitable 2, com foco nos mecanismos de autenticação, nas proteções contra tentativas consecutivas de login e nas permissões de acesso disponibilizadas pelo servidor.

A investigação começou com a identificação do serviço vsFTPd 2.3.4 e avançou para a análise do comportamento da autenticação, avaliação das configurações do servidor e realização de testes controlados utilizando Hydra e Medusa.

Posteriormente, foi realizada uma análise do tráfego de rede com Wireshark, permitindo observar os comandos de autenticação FTP, a transmissão de credenciais em texto claro e o estabelecimento e encerramento de conexões TCP.

Toda a atividade foi realizada em um ambiente virtualizado e isolado.

### 🎯 Objetivos

- Identificar e enumerar o serviço FTP.
- Investigar os mecanismos de autenticação disponíveis.
- Analisar o comportamento do servidor após falhas consecutivas de login.
- Verificar se novas conexões são aceitas após o encerramento de uma sessão.
- Analisar as configurações relevantes do vsFTPd.
- Avaliar a resistência da autenticação a ataques de dicionário.
- Utilizar Hydra e Medusa para testes controlados.
- Validar manualmente as credenciais identificadas.
- Investigar as permissões e a navegação pelo sistema de arquivos.
- Analisar o tráfego FTP utilizando Wireshark.
- Compreender os riscos da transmissão de credenciais sem criptografia.

### 🔎 Escopo da investigação

| Informação | Resultado |
|---|---|
| Sistema alvo | Metasploitable 2 |
| Serviço | FTP |
| Implementação | vsFTPd 2.3.4 |
| Porta | TCP/21 |
| Técnicas investigadas | Online Password Guessing / Dictionary Attack |
| Ferramentas principais | Nmap, Hydra, Medusa e Wireshark |
| Principal descoberta | Credenciais padrão válidas para uma conta local |

**Classificação da investigação:** avaliação de configuração e segurança da autenticação FTP. Não foi associada uma CVE específica a esta investigação.

---

## 🖥️ 2. Ambiente de laboratório

Os testes foram realizados utilizando duas máquinas virtuais conectadas por uma rede isolada.

| Máquina | Sistema | Endereço IP |
|---|---|---|
| Atacante | Kali Linux | `192.168.100.20` |
| Alvo | Metasploitable 2 | `192.168.100.10` |

### 🧰 Ferramentas utilizadas

- Kali Linux
- Metasploitable 2
- Nmap
- Hydra 9.7
- Medusa 2.3
- Wireshark
- Cliente FTP (`tnftp`)
- Terminal Linux

---

## 🔍 3. Reconhecimento e enumeração

O reconhecimento inicial foi realizado utilizando Nmap para identificar os serviços disponíveis no sistema alvo.

### 3.1. Identificação de serviços

Comando utilizado:

```bash
nmap -sV 192.168.100.10
```

Após identificar o serviço FTP, a investigação foi direcionada especificamente para a porta TCP/21.

```bash
nmap -sV -p 21 -A 192.168.100.10
```

### Resultado observado

```text
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 2.3.4
```

O resultado identificou o serviço vsFTPd 2.3.4.

A análise também apresentou informações adicionais:

```text
| ftp-syst:
|   STAT:
| FTP server status:
|      Connected to 192.168.100.20
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      vsFTPd 2.3.4 - secure, fast, stable
```

Outro resultado relevante:

```text
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)
```

### 📊 Interpretação

Foram identificadas as seguintes características:

- Serviço FTP disponível na porta TCP/21.
- Servidor utilizando vsFTPd 2.3.4.
- Autenticação anônima habilitada.
- Conexão de controle sem criptografia.
- Conexões de dados também sem criptografia.
- Tempo de inatividade da sessão configurado para 300 segundos.

A identificação da versão permitiu direcionar a investigação para o comportamento específico do serviço FTP.

O acesso anônimo representou uma característica adicional do servidor, mas a investigação principal foi direcionada à autenticação de usuários locais.

---

## 🔐 4. Análise do comportamento da autenticação

Após identificar o serviço, foram realizadas tentativas manuais de autenticação utilizando credenciais inválidas.

Comando utilizado:

```bash
ftp 192.168.100.10
```

### Resultado observado

```text
220 (vsFTPd 2.3.4)

Name (192.168.100.10:jsc333): dsadas

331 Please specify the password.
530 Login incorrect.

ftp> user 123

331 Please specify the password.
530 Login incorrect.

ftp> user 123

331 Please specify the password.
530 Login incorrect.

ftp> user 1

421 Service not available, remote server has closed connection.
Login failed.
```

### 📊 Interpretação

As respostas apresentadas pelo servidor demonstraram dois comportamentos principais:

| Código FTP | Significado | Observação |
|---|---|---|
| `331` | User name okay, need password | O servidor solicita a senha. |
| `530` | Not logged in | A autenticação foi recusada. |
| `421` | Service not available, closing control connection | A conexão FTP foi encerrada. |
| `230` | User logged in, proceed | A autenticação foi concluída com sucesso. |

Após três falhas consecutivas, a sessão FTP foi encerrada pelo servidor.

Esse comportamento é compatível com o parâmetro `max_login_fails` do vsFTPd, que controla a quantidade de falhas de autenticação permitidas antes de encerrar a sessão.

É importante diferenciar o encerramento da sessão de um bloqueio de endereço IP. O primeiro interrompe a conexão atual; o segundo impede ou restringe novas conexões originadas daquele endereço.

### 4.1. Verificação de novas conexões

Após receber a resposta `421`, foi encerrada a sessão do cliente FTP:

```text
ftp> bye
```

Em seguida, foi realizada uma nova conexão:

```bash
ftp 192.168.100.10
```

**Resultado observado:** o servidor aceitou novamente a conexão originada do mesmo endereço IP.

Isso demonstrou que o encerramento da sessão anterior não impediu o estabelecimento de uma nova conexão.

Não foi observado bloqueio persistente do endereço IP durante os testes realizados.

---

## ⚙️ 5. Análise das configurações do vsFTPd

Foi consultado o arquivo de configuração:

```text
/etc/vsftpd.conf
```

A análise identificou algumas diretivas relevantes:

| Diretiva | Configuração | Função |
|---|---|---|
| `anonymous_enable` | `YES` | Permite autenticação anônima. |
| `local_enable` | `YES` | Permite autenticação de usuários locais. |
| `write_enable` | `YES` | Habilita comandos FTP de escrita, sujeitos às permissões do sistema. |
| `local_umask` | `022` | Define a máscara de permissões para arquivos e diretórios criados por usuários locais. |
| `connect_from_port_20` | `YES` | Utiliza a porta TCP/20 como origem da conexão de dados no modo ativo. |

Não foram encontradas diretivas explicitamente declaradas para:

```text
max_login_fails
max_per_ip
max_clients
```

A ausência dessas diretivas no arquivo não comprova, isoladamente, que os mecanismos correspondentes estejam desabilitados. O vsFTPd utiliza valores padrão quando determinadas opções não são configuradas explicitamente.

O comportamento observado foi compatível com o encerramento da sessão após três falhas consecutivas.

Também não foi realizada uma auditoria completa das regras de firewall ou de eventuais ferramentas externas de bloqueio, como Fail2Ban.

---

## 👤 6. Preparação e validação de uma conta local

Para verificar a autenticação de usuários locais, foi criada uma conta específica para o laboratório.

```text
ftp-lab
```

A criação dessa conta permitiu testar a diretiva:

```ini
local_enable=YES
```

### Validação manual

Na máquina Kali:

```bash
ftp 192.168.100.10
```

Foi informado o usuário `ftp-lab` e a senha definida durante a criação da conta.

### Resultado observado

```text
220 (vsFTPd 2.3.4)
331 Please specify the password.
230 Login successful.
```

A autenticação foi concluída com sucesso.

Isso confirmou que o serviço permitia autenticação FTP utilizando contas locais do sistema operacional.

---

## 🧪 7. Avaliação da autenticação com Hydra

Após a análise manual do comportamento do serviço, foi escolhido o Hydra para avaliar a resistência da autenticação a tentativas automatizadas.

### 7.1. Preparação das wordlists

Foram preparados dois arquivos:

```text
ftp-user.txt
ftp-passwords.txt
```

O primeiro continha usuários candidatos e o segundo uma lista reduzida de senhas.

### 7.2. Execução do Hydra

Comando utilizado:

```bash
hydra -L ftp-user.txt -P ftp-passwords.txt -t 1 -c 2 -f ftp://192.168.100.10
```

### Parâmetros utilizados

| Parâmetro | Função |
|---|---|
| `-L` | Carrega uma lista de usuários. |
| `-P` | Carrega uma lista de senhas. |
| `-t 1` | Utiliza uma tarefa paralela por vez. |
| `-c 2` | Define o intervalo configurado entre tentativas de login. |
| `-f` | Interrompe a execução após encontrar uma combinação válida. |

### Resultado observado

```text
[DATA] max 1 task per 1 server, overall 1 task,
595 login tries (l:85/p:7), ~595 tries per task

[DATA] attacking ftp://192.168.100.10:21/

[STATUS] 18.00 tries/min, 18 tries in 00:01h

[21][ftp] host: 192.168.100.10
login: msfadmin
password: msfadmin

[STATUS] attack finished for 192.168.100.10
(valid pair found)

1 of 1 target successfully completed,
1 valid password found
```

O Hydra identificou uma combinação válida:

| Campo | Resultado |
|---|---|
| Usuário | `msfadmin` |
| Senha | `msfadmin` |
| Serviço | FTP |
| Porta | TCP/21 |

### 📊 Interpretação

A mensagem:

```text
595 login tries (l:85/p:7)
```

representava a quantidade máxima de combinações possíveis entre os arquivos utilizados:

- 85 usuários.
- 7 senhas.
- 595 combinações possíveis.

Como o parâmetro `-f` foi utilizado, o Hydra encerrou a execução após encontrar uma combinação válida. Portanto, não significa que todas as 595 combinações foram testadas.

O resultado demonstrou que uma credencial padrão e fraca estava presente entre as combinações fornecidas.

### 7.3. Gerenciamento de conexões pelo Hydra

Durante a investigação, foi observado que o encerramento de uma sessão FTP não impediu a continuidade do teste.

A análise do módulo FTP do Hydra 9.7 demonstrou que a ferramenta possui lógica própria para gerenciamento de conexões TCP.

Quando uma conexão deixa de funcionar, o fluxo do módulo pode retornar à etapa de conexão e estabelecer um novo socket.

Isso permite que o processamento continue quando o servidor aceita novas conexões.

É importante distinguir:

| Mecanismo | Comportamento |
|---|---|
| `max_login_fails` | Encerra a sessão FTP após falhas consecutivas. |
| Bloqueio de IP | Impede ou restringe novas conexões originadas de determinado endereço. |
| Hydra | Gerencia as conexões e pode estabelecer uma nova conexão quando a anterior deixa de funcionar. |

O encerramento de uma sessão não representa, necessariamente, a interrupção definitiva de um teste de autenticação.

**Limitação da evidência:** a saída do Hydra não informa quantas reconexões ocorreram durante essa execução. O funcionamento do módulo explica a possibilidade de recuperação da conexão, mas não foi realizada uma captura individualizada dessa execução para contar os fluxos TCP.

---

## ⚔️ 8. Comparação prática: Hydra e Medusa

Após o teste com Hydra, foi realizada uma segunda avaliação utilizando Medusa.

O objetivo foi observar outra implementação de ferramenta de auditoria de autenticação e comparar seu comportamento com o resultado anterior.

### 8.1. Execução do Medusa

Comando utilizado:

```bash
medusa -h 192.168.100.10 -U ftp-user.txt -P ftp-passwords.txt -M ftp -t 6
```

### Parâmetros utilizados

| Parâmetro | Função |
|---|---|
| `-h` | Endereço do sistema alvo. |
| `-U` | Arquivo contendo usuários candidatos. |
| `-P` | Arquivo contendo senhas candidatas. |
| `-M ftp` | Seleciona o módulo FTP. |
| `-t 6` | Permite até seis tarefas simultâneas. |

### Resultado observado

```text
2026-11-03 03:32:57 ACCOUNT CHECK:
[ftp] Host: 192.168.100.10
User: 1234
Password: admin

...

2026-11-03 03:33:19 ACCOUNT FOUND:
[ftp] Host: 192.168.100.10
User: msfadmin
Password: msfadmin
[SUCCESS]
```

O Medusa também identificou a combinação:

```text
User: msfadmin
Password: msfadmin
```

A ferramenta apresentou mensagens `ACCOUNT CHECK` durante a execução, permitindo acompanhar as combinações avaliadas.

Após identificar a credencial válida, a execução ainda apresentou outras verificações. Isso ocorreu porque não foi selecionada a opção de interrupção após a primeira descoberta.

### 8.2. Análise comparativa

| Característica | Hydra | Medusa |
|---|---|---|
| Protocolo testado | FTP | FTP |
| Credencial encontrada | `msfadmin:msfadmin` | `msfadmin:msfadmin` |
| Tarefas paralelas | 1 | 6 |
| Usuários contabilizados | 85 | 7 |
| Senhas contabilizadas | 7 | 7 |
| Resultado | Autenticação válida identificada | Autenticação válida identificada |
| Saída apresentada | Resultado de credencial encontrada | Verificações individuais e descoberta da conta |

**Observação:** as execuções não constituem uma comparação controlada de desempenho, pois utilizaram quantidades diferentes de usuários e níveis diferentes de concorrência.

O Medusa apresentou uma saída mais detalhada durante a execução e concluiu sua investigação em menos tempo no teste realizado. Entretanto, não é possível afirmar que seja universalmente mais rápido ou superior ao Hydra com base nesses resultados.

### 8.3. Gerenciamento de conexões pelo Medusa

A documentação do Medusa descreve mecanismos para identificar quando uma conexão FTP deixa de estar disponível e estabelecer outra conexão quando necessário.

Esse comportamento é relevante em servidores que encerram sessões após determinadas falhas de autenticação.

A investigação permitiu compreender a diferença entre:

- Reutilizar uma conexão enquanto ela permanece disponível.
- Detectar que a conexão foi encerrada.
- Estabelecer outra conexão TCP.
- Continuar o processamento das combinações restantes.

O parâmetro `-t 6` também contribuiu para a execução de várias tarefas simultâneas.

---

## 📡 9. Análise do tráfego FTP com Wireshark

Após os testes de autenticação com Hydra e Medusa, foi realizada uma captura de tráfego utilizando Wireshark para observar a comunicação entre as máquinas.

O objetivo foi compreender como o Medusa estabelecia conexões TCP, transmitia credenciais e lidava com o encerramento dos fluxos de comunicação.

### 9.1. Identificação das conexões TCP

Durante a execução do Medusa com o parâmetro `-t 6`, foram observadas múltiplas conexões entre:

| Campo | Valor |
|---|---|
| Origem | `192.168.100.20` |
| Destino | `192.168.100.10` |
| Porta de destino | TCP/21 |
| Serviço | FTP |

Foram identificadas diferentes portas de origem:

```text
56314 → 21 [SYN]
56318 → 21 [SYN]
56324 → 21 [SYN]
56340 → 21 [SYN]
56350 → 21 [SYN]
```

Também foi identificada uma conexão utilizando a porta de origem `56304`.

Essas conexões foram estabelecidas por meio do TCP Three-Way Handshake:

1. `SYN`: solicitação de estabelecimento de conexão.
2. `SYN, ACK`: resposta do servidor.
3. `ACK`: confirmação do cliente.

A utilização de diferentes portas de origem demonstrou a existência de fluxos TCP independentes, comportamento compatível com a execução de múltiplas tarefas paralelas.

### 9.2. Identificação dos comandos de autenticação

A captura permitiu visualizar diretamente os comandos FTP transmitidos pelo Medusa.

Exemplo observado:

```text
Request: USER 1234
Response: 331 Please specify the password.
Request: PASS kali
```

Também foram identificadas outras senhas candidatas:

```text
PASS ubuntu
PASS admin
PASS 1234
PASS user
PASS root
```

O servidor respondeu às tentativas inválidas com:

```text
Response: 530 Login incorrect.
```

Essa análise confirmou que os comandos `USER` e `PASS` estavam disponíveis para inspeção na captura de tráfego.

Como o FTP tradicional não utiliza criptografia na conexão de controle, os valores transmitidos puderam ser visualizados diretamente no Wireshark.

### 9.3. Encerramento e estabelecimento de novas conexões

Durante a análise dos pacotes, foram identificadas mensagens `FIN, ACK` enviadas pelo Kali:

```text
56318 → 21 [FIN, ACK]
56340 → 21 [FIN, ACK]
56304 → 21 [FIN, ACK]
```

Esses pacotes indicaram que o cliente iniciou o encerramento das respectivas conexões TCP.

Na sequência, foram observadas novas solicitações de conexão:

```text
56354 → 21 [SYN]
56370 → 21 [SYN]
56376 → 21 [SYN]
```

Pelo menos uma dessas novas tentativas recebeu resposta `SYN, ACK` do servidor.

Isso confirmou novas tentativas de estabelecimento de conexões TCP após os encerramentos observados.

O comportamento é compatível com o gerenciamento de conexões realizado pelo Medusa durante o processamento das tentativas de autenticação.

**Limitação da evidência:** os pacotes `FIN, ACK` apresentados partiram do Kali, e não do servidor. Portanto, não é correto afirmar que o vsFTPd encerrou essas conexões específicas ao atingir o limite de tentativas. Também não foi possível determinar, somente por esse trecho, quantas reconexões resultaram em sessões FTP completas.

### 9.4. Exposição das credenciais em texto claro

Um dos resultados mais relevantes foi a possibilidade de visualizar os dados utilizados na autenticação FTP.

Os comandos `USER` e `PASS` estavam disponíveis para inspeção na captura, demonstrando que a comunicação de controle não utilizava criptografia.

Essa característica representa um risco de confidencialidade, pois um terceiro com capacidade de capturar o tráfego de rede pode obter credenciais transmitidas pelo FTP tradicional.

### 9.5. Relação com a investigação anterior da CVE-2011-2523

A análise do tráfego também permitiu relacionar o funcionamento normal da autenticação FTP com o mecanismo de acionamento da backdoor investigada anteriormente.

Na autenticação convencional, foram observados comandos como:

```text
USER 1234
PASS kali
```

Na investigação da CVE-2011-2523, o gatilho utilizado pela distribuição comprometida do vsFTPd 2.3.4 apresentava a seguinte sequência:

```text
USER X:)
PASS X
```

A diferença está no conteúdo específico enviado no campo do usuário.

Na distribuição comprometida, a presença da sequência especial no comando `USER` acionava a lógica maliciosa inserida no servidor, permitindo iniciar o mecanismo de shell remoto na porta TCP/6200.

A captura atual não demonstra o acionamento da backdoor.

Entretanto, permitiu compreender a estrutura dos comandos utilizados pelo protocolo FTP e relacionar essa estrutura ao mecanismo investigado no primeiro laboratório.

É importante distinguir os dois problemas:

| FTP tradicional | Backdoor CVE-2011-2523 |
|---|---|
| Transmite credenciais sem criptografia. | Contém lógica maliciosa inserida na distribuição comprometida. |
| Expõe comandos `USER` e `PASS`. | Interpreta uma sequência especial no campo de usuário. |
| Risco de interceptação de credenciais. | Possibilidade de execução remota de comandos. |

### 📊 Resultados da análise com Wireshark

- Múltiplas conexões TCP identificadas.
- Fluxos TCP independentes observados.
- Comandos FTP `USER` e `PASS` identificados.
- Senhas candidatas visualizadas em texto claro.
- Respostas `530` do servidor identificadas.
- Encerramentos TCP iniciados pelo Kali observados.
- Novas solicitações de conexão identificadas.
- Relação entre os comandos FTP convencionais e o gatilho da backdoor compreendida.

A análise do Wireshark complementou os resultados obtidos com Nmap, Hydra e Medusa, permitindo observar diretamente o comportamento da comunicação entre cliente e servidor.

---

## 📂 10. Análise da navegação pelo sistema de arquivos

Após a identificação das credenciais, foi realizada uma conexão FTP utilizando o usuário `msfadmin`.

### 10.1. Validação manual das credenciais

Comando:

```bash
ftp 192.168.100.10
```

Usuário informado:

```text
msfadmin
```

Resultado observado:

```text
220 (vsFTPd 2.3.4)
331 Please specify the password.
230 Login successful.
```

A autenticação foi concluída com sucesso.

A combinação identificada pelo Hydra e pelo Medusa também foi confirmada manualmente.

### 10.2. Diretório inicial

Foi utilizado:

```text
ftp> pwd
```

Resultado:

```text
Remote directory: /home/msfadmin
```

O usuário autenticado iniciou a sessão em seu diretório pessoal.

A listagem apresentou:

```text
ftp> ls

drwxr-xr-x 6 1000 1000 4096 Apr 28 2010 vulnerable
```

### 10.3. Navegação para a raiz do sistema

Em seguida, foi executado:

```text
ftp> cd /
```

O servidor confirmou a alteração:

```text
250 Directory successfully changed.
```

Ao executar:

```text
ftp> ls
```

Foi apresentada uma listagem contendo diretórios da estrutura principal do Linux:

```text
bin
boot
dev
etc
home
lib
lost+found
media
mnt
opt
proc
root
sbin
srv
sys
tmp
usr
var
```

Também foram observados metadados de permissões, proprietários e grupos.

Posteriormente, foi acessado o diretório `/home`:

```text
ftp> cd /home
ftp> ls
```

A listagem apresentou diferentes diretórios pessoais:

```text
ftp
ftp-lab
msfadmin
service
user
```

### 📊 Interpretação

A possibilidade de navegar de `/home/msfadmin` até `/` demonstrou que o usuário FTP não estava restrito ao seu diretório pessoal por um mecanismo de confinamento (*chroot jail*).

Isso permitiu visualizar a estrutura principal do sistema operacional, nomes de diretórios pessoais e metadados de permissões e proprietários.

Entretanto, listar um diretório não significa necessariamente possuir permissão para acessar todo o seu conteúdo.

A investigação confirmou a possibilidade de navegação pela estrutura de diretórios, mas não demonstrou acesso irrestrito a todos os arquivos do sistema.

Também não foi obtido um shell remoto nem foram comprovados privilégios de root durante essa etapa.

---

## 📉 11. Análise de impacto

Os resultados demonstraram fragilidades importantes na configuração e na utilização do serviço FTP.

| Dimensão | Risco identificado |
|---|---|
| Confidencialidade | Credenciais padrão permitem autenticação não autorizada. |
| Confidencialidade | A comunicação sem criptografia permite visualizar credenciais transmitidas. |
| Confidencialidade | A listagem de diretórios expõe informações sobre a estrutura do sistema. |
| Integridade | O acesso autenticado pode permitir operações de escrita quando habilitadas e autorizadas pelas permissões do sistema. |
| Disponibilidade | Tentativas repetidas podem consumir recursos e gerar encerramento de sessões. |

### Principais problemas identificados

1. Autenticação anônima habilitada.
2. Utilização de credenciais padrão em uma conta local.
3. Ausência de criptografia na comunicação FTP.
4. Ausência de confinamento do usuário FTP ao diretório pessoal.
5. Encerramento de sessões após falhas, sem bloqueio persistente de IP observado durante os testes.

A descoberta mais relevante foi a utilização de credenciais padrão, identificadas por meio de ferramentas de auditoria de autenticação e confirmadas manualmente.

---

## 🛡️ 12. Recomendações de mitigação

As seguintes medidas podem reduzir os riscos identificados:

1. Desabilitar o acesso anônimo quando não for necessário.
2. Substituir credenciais padrão por senhas fortes, únicas e não reutilizadas.
3. Remover ou alterar credenciais padrão de contas existentes.
4. Desabilitar a autenticação FTP de usuários locais que não necessitam desse serviço.
5. Implementar controles de limitação e monitoramento de tentativas de autenticação.
6. Adotar bloqueio temporário de IP diante de comportamento suspeito, considerando os riscos de falsos positivos.
7. Restringir os diretórios acessíveis por usuários FTP.
8. Utilizar contas dedicadas com privilégios mínimos.
9. Desabilitar operações de escrita quando não forem necessárias.
10. Substituir FTP tradicional por SFTP ou FTPS, conforme os requisitos do ambiente.
11. Atualizar o servidor para uma versão mantida e segura.

---

## 🏁 13. Conclusão

O laboratório demonstrou como uma investigação de segurança pode evoluir desde a identificação de um serviço até a avaliação de seus mecanismos de autenticação, comunicação e controle de acesso.

Inicialmente, o Nmap identificou o vsFTPd 2.3.4 na porta TCP/21 e confirmou a disponibilidade de autenticação anônima.

Posteriormente, foram realizadas tentativas manuais de autenticação inválidas, nas quais o servidor encerrou a sessão após três falhas consecutivas. Entretanto, uma nova conexão originada do mesmo IP foi aceita.

A análise das configurações permitiu identificar a possibilidade de autenticação de usuários locais.

Com o Hydra, foi realizado um teste de dicionário utilizando uma lista de usuários e uma lista de senhas. Uma combinação válida foi encontrada para a conta `msfadmin`.

Posteriormente, o Medusa foi utilizado para realizar uma segunda avaliação. A ferramenta também identificou a combinação `msfadmin:msfadmin`, apresentando as verificações individuais durante a execução.

A análise com Wireshark permitiu observar múltiplas conexões TCP, comandos `USER` e `PASS`, respostas de autenticação e novas solicitações de conexão. Também foi possível visualizar as senhas candidatas em texto claro, demonstrando o risco de confidencialidade associado ao FTP tradicional.

A investigação ainda demonstrou que o usuário autenticado conseguia navegar da pasta pessoal até a raiz do sistema de arquivos, visualizando diretórios e metadados do Linux.

### ✅ Resultados alcançados

- Serviço FTP identificado e enumerado.
- Versão vsFTPd 2.3.4 confirmada.
- Acesso anônimo identificado.
- Comportamento após falhas consecutivas de autenticação observado.
- Encerramento de sessão confirmado.
- Nova conexão pelo mesmo IP validada.
- Autenticação de usuário local confirmada.
- Teste de dicionário realizado com Hydra.
- Teste de dicionário realizado com Medusa.
- Credenciais padrão identificadas e validadas manualmente.
- Gerenciamento de conexões das ferramentas analisado.
- Múltiplos fluxos TCP identificados no Wireshark.
- Comandos FTP e credenciais transmitidas em texto claro observados.
- Relação entre os comandos FTP convencionais e o gatilho da backdoor compreendida.
- Estrutura do sistema de arquivos acessada por meio do FTP.

O principal aprendizado foi compreender que a avaliação de segurança não deve se limitar à identificação de portas abertas ou à execução de ferramentas. É necessário investigar o comportamento dos serviços, compreender os protocolos envolvidos, analisar as conexões de rede, validar as descobertas e interpretar as permissões efetivamente disponibilizadas.

---

## 📚 14. Referências técnicas

- [Nmap — Official Documentation](https://nmap.org/book/man.html)
- [THC Hydra — Official Repository](https://github.com/vanhauser-thc/thc-hydra)
- [Medusa — Official Repository](https://github.com/jmk-foofus/medusa)
- [Wireshark — Official Documentation](https://www.wireshark.org/docs/)
- [vsFTPd — Configuration Reference](https://security.appspot.com/vsftpd/vsftpd_conf.html)
- [RFC 959 — File Transfer Protocol](https://www.rfc-editor.org/rfc/rfc959)
- [RFC 2577 — FTP Security Considerations](https://www.rfc-editor.org/rfc/rfc2577)
- [CVE Program](https://www.cve.org/)
- [OWASP Foundation](https://owasp.org/)

---

- **Ambiente:** laboratório virtual isolado.
- **Alvo:** Metasploitable 2.
- **Serviço investigado:** vsFTPd 2.3.4 — TCP/21.
- **Status:** investigação prática concluída.
