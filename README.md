# 📘 Guia Básico de Comandos Cisco IOS

Este guia oferece uma referência rápida para os **comandos essenciais do Cisco IOS** (Internetwork Operating System), utilizado em **roteadores e switches Cisco**. A configuração é realizada por meio de uma hierarquia de modos de comando.

---

## 🧭 Modos de Comando Principais

A navegação entre os modos é fundamental para a configuração correta dos dispositivos Cisco.

| Modo | Prompt | Descrição |
|------|--------|-----------|
| **Execução do Usuário** | `Router>` | Acesso inicial. Comandos de visualização limitados. Use `enable` para avançar. |
| **Execução Privilegiado** | `Router#` | Acesso administrativo. Permite visualizar configurações e gerenciar arquivos. Use `configure terminal` para entrar no modo de configuração. |
| **Configuração Global** | `Router(config)#` | Onde a maioria das configurações globais são aplicadas. A partir daqui, acesse modos de configuração específicos (interfaces, protocolos, etc.). |

---

## 🔧 Comandos Básicos

### 🟡 Acesso e Navegação

| Comando | Descrição |
|--------|-----------|
| `Router> enable` | Usaado para entrar no modo privilegiado |
| `Router# configure terminal` | Usa para entrar no modo de configuração global |
| `Router(config)# end` | Retorna ao modo privilegiado |
| `Router# exit` | Pode ser usado em qualquer modo e retorna ao modo anterior |

---

### 📄 Verificação de Configurações

| Comando | Descrição |
|--------|-----------|
| `show running-config` | Exibe as configurações atuais do dispositivo disponiveis na memória volratil |
| `show startup-config` | Exibe as configurações salvas na memória não volátil do dispositivo(NVRAM)|
| `show ip interface brief` | Resumo das configuraçoes das interfaces IP |
| `show ip route` | Exibe a tabela de rotas do dispositivo|
| `show interface status` | Exibe o Status das interfaces do switch |
| `show mac address-table` | Mostra a tabela de endereços MAC |

---

### ⚙️ Configurações Básicas

| Comando | Descrição |
|--------|-----------|
| `hostname Roteador` | Define o nome do dispositivo onde Roteador é no nome|
| `banner motd @ ... @` | Exibe mensagem personalizada na tela de login | a mensagem deve ser digitada entre os 2 caracteres especiais|
| `enable secret senha` | Define senha para acesso ao modo privilegiado |
| `service password-encryption` | Ativa a criptografia de todas as senhas do dispositivo|

#### 🌐 Configurações de Interface

| Comando                                  | Descrição                                  |
| ---------------------------------------- | ------------------------------------------ |
| `interface f0/0`                         | Entra no modo de configuração da interface (neste caso na interface f0/0 |
| `ip address 192.168.0.254 255.255.255.0` | Atribui IP e máscara à interface                     |
| `description <texto>`                    | Adiciona uma descrição à interface             |
| `no shutdown`                            | Ativa a interface (por padrão as interfaces estão desativadas                         |
| `shutdown`                               | Desativa a interface                       |


### 💾 Salvando Configurações

| Comando                              | Descrição                                       |
| ------------------------------------ | ----------------------------------------------- |
| `copy running-config startup-config` | Salva as configurações na NVRAM (inicialização) |


### 🌐 Acesso Remoto via Telnet

| Comando             | Descrição                                |
| ------------------- | ---------------------------------------- |
| `line vty 0 15`     | Acesso às linhas virtuais (Telnet/SSH)   |
| `password p@ssw0rd` | Define senha de acesso remoto            |
| `login`             | Habilita autenticação para acesso remoto |
| `exec-timeout 0 0`  | Sessão remota sem tempo limite           |
| `exit`              | Retorna ao modo anterior                 |



## 🛰️ Configuração de Roteamento Estático

Roteamento estático é utilizado para definir manualmente o caminho que os pacotes devem seguir para alcançar outras redes. Ideal em redes pequenas ou para cenários de estudo.


| Comando             | Descrição                                |
| ------------------- | ---------------------------------------- |
| Router(config)# ip route <End.Rede> <Máscara> <Next_hop>     | Configuração de rota entre duas redes   |

📘 Parâmetros:

**<End.Rede>**: Endereço da rede de destino (ex: 192.168.2.0)

**<Máscara>**: Máscara de sub-rede (ex: 255.255.255.0)

**<Next_hop>**: Endereço IP do próximo salto (gateway), geralmente a interface de um roteador vizinho (ex: 192.168.1.1)

## 🛡️ Comandos Opcionais e Boas Práticas (Avançado)

Estes comandos não são obrigatórios, mas melhoram a **segurança, usabilidade e administração** do roteador. Recomendados para ambientes de produção ou estudos avançados.

---

### 🔐 Configuração de Linha AUX (Porta Auxiliar)

| Comando | Descrição |
|--------|-----------|
| `line aux 0` | Entra na configuração da linha auxiliar |
| `password aux123` | Define a senha para a porta AUX |
| `login` | Exige senha para acesso pela AUX |
| `exit` | Retorna ao modo anterior |

---
### ❌ Desativar Pesquisa DNS (Evita Lentidão com Comandos Incorretos)

| Comando | Descrição |
|--------|-----------|
| `no ip domain-lookup` | Desativa a tentativa de resolução DNS de comandos inválidos |

---

### ⏱️ Tempo de Inatividade da Sessão de Console

| Comando | Descrição |
|--------|-----------|
| `line console 0` | Acessa a configuração do console |
| `exec-timeout 5 0` | Define tempo limite para inatividade: 5 minutos |

---

### 🔎 Comandos de Verificação Avançada

| Comando | Descrição |
|--------|-----------|
| `show version` | Mostra informações do roteador e do IOS |
| `show ip protocols` | Lista os protocolos de roteamento configurados |
| `show interfaces` | Informações detalhadas de todas as interfaces |
| `show cdp neighbors` | Exibe dispositivos Cisco diretamente conectados |
| `show users` | Lista usuários atualmente conectados |
| `show clock` | Mostra a hora atual do roteador |
|`Sw (config)# show interfaces status`| Apresenta status das interfaces do switch | 


#### 🌐 Configurações de Interface Vlan no Switch

| Comando                                  | Descrição                                  |
| ---------------------------------------- | ------------------------------------------ |
| `Sw (config)# interface vlan 1`          | Interface de configuração global para acesso remoto |
| `Sw(config-if)# ip address 192.168.1.20 255.255.255` | Atribui endereço IP a interface Vlan 1                      |
| `description <texto>`                    | Adiciona uma descrição à interface             |
| `no shutdown`                            | Ativa a interface (por padrão as interfaces estão desativadas                         |
| `shutdown`                               | Desativa a interface                       |
| `Sw(config)# ip default-gateway 192.168.1.1` |Configura Endereço de gateway no Switch para gerenciar remotamente o dispositivo|
