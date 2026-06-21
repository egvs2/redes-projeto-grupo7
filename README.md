# Instituto Federal de Alagoas
## Fundamentos de redes de computadores
## Grupo7
Emerson Gomes Vanderlei da Silva <br>
Tainá Ferreira Miranda <br>
Matheus Azafhi Goes de Souza <br>
Heitor Moreira Costa

---

## Sumário
* [1. Planejamento da Infraestrutura e Hardware](#1-planejamento-da-infraestrutura-e-hardware)
* [2. Arquitetura de Endereçamento IP (Sub-rede /28)](#2-arquitetura-de-endereçamento-ip-sub-rede-28)
  * [2.1 Descobrindo o tamanho dos blocos](#21-descobrindo-o-tamanho-dos-blocos)
  * [2.2 Mapeamento das Sub-redes (Como chegamos ao Grupo 7)](#22-mapeamento-das-sub-redes-como-chegamos-ao-grupo-7)
  * [2.3 Anatomia da Faixa do Grupo 7](#23-anatomia-da-faixa-do-grupo-7)
  * [2.4 Distribuição de Endereçamento IP do Grupo](#24-distribuição-de-endereçamento-ip-do-grupo)
* [3. Tabela de Nomenclatura e Domínio (FQDN)](#3-tabela-de-nomenclatura-e-domínio-fqdn)
* [4. Usuários e senhas](#4-usuários-e-senhas)
* [5. Prints netplan](#5-prints-netplan)
* [6. Prints de ping](#6-prints-de-ping)
  * [6.1 PC1](#61-pc1)
    * [6.1.1 Ping com FQDN](#611-ping-com-fqdn)
    * [6.1.2 Ping com hostname](#612-ping-com-hostname)
    * [6.1.3 Ping com IP](#613-ping-com-ip)
  * [6.2 PC2](#62-pc2)
    * [6.2.1 Ping com FQDN](#621-ping-com-fqdn)
    * [6.2.2 Ping com hostname](#622-ping-com-hostname)
    * [6.2.3 Ping com IP](#623-ping-com-ip)
  * [6.3 PC3](#63-pc3)
    * [6.3.1 Ping com FQDN](#631-ping-com-fqdn)
    * [6.3.2 Ping com hostname](#632-ping-com-hostname)
    * [6.3.3 Ping com IP](#633-ping-com-ip)
  * [6.4 PC4](#64-pc4)
    * [6.4.1 Ping com FQDN](#641-ping-com-fqdn)
    * [6.4.2 Ping com hostname](#642-ping-com-hostname)
    * [6.4.3 Ping com IP](#643-ping-com-ip)
* [7. Conexão SSH](#7-conexão-ssh)

---

# Tabelas de Configuração de Hardware, Endereçamento e Domínio

## 1. Planejamento da Infraestrutura e Hardware

Para garantir a replicação idêntica deste laboratório, cada uma das 8 Máquinas Virtuais (MVs) deve ser criada no VirtualBox utilizando estritamente a seguinte especificação técnica:

| Componente | Configuração por VM | Função no Laboratório |
| :--- | :--- | :--- |
| **Sistema Operacional** | Ubuntu Server 26.04 LTS | Sistema operacional base (sem interface gráfica). |
| **Processador (vCPU)** | 1 Core / 1 Processador | Suficiente para a execução de serviços básicos CLI. |
| **Memória RAM** | 2048 MB (2GB) | Alocação ideal para evitar travamentos em sistemas locais. |
| **Disco Rígido (HD)** | 25 GB (Alocação Dinâmica) | Espaço para armazenamento de logs e arquivos do sistema. |
| **Placa de Rede** | 1 Interface em Modo Bridge | Vinculada à interface física ativa (Wi-Fi ou Cabo) do host real. |

---

## 2. Arquitetura de Endereçamento IP (Sub-rede /28)

A turma utilizou a rede mãe `192.168.26.0/24`. Seguindo a regra de segmentação, o **Grupo 7** recebeu a 7ª sub-rede calculada através da máscara de sub-rede `/28` (`255.255.255.240`), o que nos fornece blocos de 16 endereços IP (14 úteis para hosts).

### Memória de Cálculo e Regra de Segmentação

Para fatiar a rede mãe `192.168.26.0/24` em sub-redes menores para a turma, utilizamos a técnica de CIDR (Classless Inter-Domain Routing) com a máscara `/28`. 

#### 2.1 Descobrindo o tamanho dos blocos
A máscara `/24` original possui 24 bits destinados à rede e 8 bits para os hosts. Ao alterá-la para `/28`, "pegamos emprestado" 4 bits da parte dos hosts para criar as sub-redes.

* **Máscara em bits:** `11111111.11111111.11111111.11110000` (28 bits ligados)
* **Máscara em formato decimal:** `255.255.255.240`
* **Quantidade de sub-redes possíveis ($2^n$):** Como pegamos 4 bits emprestados ($n=4$), temos $2^4 = 16$ sub-redes disponíveis para a turma.
* **Tamanho de cada bloco ($2^h$):** Como restaram 4 bits para os hosts ($32 - 28 = 4$), cada sub-rede terá um tamanho fixo de $2^4 = 16$ endereços IP totais.

Cada bloco perde sempre 2 endereços IPs obrigatórios (o primeiro é o ID da Rede e o último é o Broadcast), restando exatamente **14 IPs úteis** para configurar as máquinas.

#### 2.2 Mapeamento das Sub-redes (Como chegamos ao Grupo 7)
Sabendo que os blocos saltam de 16 em 16 números no último octeto, a divisão oficial das sub-redes da turma ficou organizada da seguinte forma:

* **Sub-rede 1 (Grupo 1):** `192.168.26.0` a `192.168.26.15`
* **Sub-rede 2 (Grupo 2):** `192.168.26.16` a `192.168.26.31`
* **Sub-rede 3 (Grupo 3):** `192.168.26.32` a `192.168.26.47`
* **Sub-rede 4 (Grupo 4):** `192.168.26.48` a `192.168.26.63`
* **Sub-rede 5 (Grupo 5):** `192.168.26.64` a `192.168.26.79`
* **Sub-rede 6 (Grupo 6):** `192.168.26.80` a `192.168.26.95`
* **Sub-rede 7 (Grupo 7):** **`192.168.26.96` a `192.168.26.111`** 👈 *Nossa faixa alocada*
* **Sub-rede 8 (Grupo 8):** `192.168.26.112` a `192.168.26.127`
*(... e assim por diante até a Sub-rede 16)*

#### 2.3 Anatomia da Faixa do Grupo 7
Aplicando as regras do protocolo IPv4 sobre o nosso bloco, mapeamos os seguintes parâmetros de rede:

* **ID de Rede (Endereço de Rede):** `192.168.26.96` (Identifica a nossa sub-rede no roteamento, não pode ser atribuído a nenhuma máquina).
* **Primeiro IP utilizável:** `192.168.26.97` (Atribuído à primeira VM do projeto).
* **Último IP utilizável:** `192.168.26.110` (Limite físico utilizável para hosts nesta rede).
* **Endereço de Broadcast:** `192.168.26.111` (Utilizado para comunicação simultânea com todos os hosts da sub-rede).

---

### 2.4 Distribuição de Endereçamento IP do Grupo

Abaixo está a distribuição de IP fixa adotada e distribuída entre as máquinas físicas (Hosts) dos integrantes da equipe para as 8 MVs do projeto:

| Máquina Virtual | Host Físico | Nome do Host (Hostname) | Endereço IP / Máscara |
| :--- | :--- | :--- | :--- |
| VM Lab01@PC1 | PC1 (Emerson) | `vmlab01pc1` | 192.168.26.97/28 |
| VM Lab02@PC1 | PC1 (Emerson) | `vmlab02pc1` | 192.168.26.98/28 |
| VM Lab01@PC2 | PC2 (Tainá) | `vmlab01pc2` | 192.168.26.99/28 |
| VM Lab02@PC2 | PC2 (Tainá) | `vmlab02pc2` | 192.168.26.100/28 |
| VM Lab01@PC3 | PC3 (Matheus) | `vmlab01pc3` | 192.168.26.101/28 |
| VM Lab02@PC3 | PC3 (Matheus) | `vmlab02pc3` | 192.168.26.102/28 |
| VM Lab01@PC4 | PC4 (Heitor) | `vmlab01pc4` | 192.168.26.103/28 |
| VM Lab02@PC4 | PC4 (Heitor) | `vmlab02pc4` | 192.168.26.104/28 |

## 3. Tabela de Nomenclatura e Domínio (FQDN)

| Endereço IP | Hostname Curto | Nome de Domínio Completo (FQDN) | Apelidos (Aliases) |
| :--- | :--- | :--- | :--- |
| 192.168.26.97 | `vmlab01pc1` | `vmlab01pc1.grupo7.bsi-26-1.maceio.lab` | vm01pc1, srv1 |
| 192.168.26.98 | `vmlab02pc1` | `vmlab02pc1.grupo7.bsi-26-1.maceio.lab` | vm02pc1, srv2 |
| 192.168.26.99 | `vmlab01pc2` | `vmlab01pc2.grupo7.bsi-26-1.maceio.lab` | vm01pc2, srv3 |
| 192.168.26.100 | `vmlab02pc2` | `vmlab02pc2.grupo7.bsi-26-1.maceio.lab` | vm02pc2, srv4 |
| 192.168.26.101 | `vmlab01pc3` | `vmlab01pc3.grupo7.bsi-26-1.maceio.lab` | vm01pc3, srv5 |
| 192.168.26.102 | `vmlab02pc3` | `vmlab02pc3.grupo7.bsi-26-1.maceio.lab` | vm02pc3, srv6 |
| 192.168.26.103 | `vmlab01pc4` | `vmlab01pc4.grupo7.bsi-26-1.maceio.lab` | vm01pc4, srv7 |
| 192.168.26.104 | `vmlab02pc4` | `vmlab02pc4.grupo7.bsi-26-1.maceio.lab` | vm02pc4, srv8 |

---

## 4. Usuários e senhas
admingrupo7 = 0123456789

taina.ferreira = 0123456789@

matheus.souza = 0123456789@

heitor.costa = 0123456789@

emerson.silva = 0123456789@

---

## 5. Prints netplan

### Netplan vmlab01pc1
![netplan_vmlab01pc1](imagens/netplan_prints/netplan_vmlab01pc1.jpg)

### Netplan vmlab02pc1
![netplan_vmlab02pc1](imagens/netplan_prints/netplan_vmlab02pc1.png)

### Netplan vmlab01pc2
![netplan_vmlab02pc1](imagens/netplan_prints/netplan_vmlab01pc2.png)

### Netplan vmlab02pc2
![netplan_vmlab02pc1](imagens/netplan_prints/netplan_vmlab02pc2.png)

### Netplan vmlab01pc3
![netplan_vmlab02pc1](imagens/netplan_prints/netplan_vmlab01pc3.png)

### Netplan vmlab02pc3
![netplan_vmlab02pc1](imagens/netplan_prints/netplan_vmlab02pc3.png)

### Netplan vmlab01pc4
![netplan_vmlab02pc1](imagens/netplan_prints/netplan_vmlab01pc4.png)

### Netplan vmlab02pc4
![netplan_vmlab02pc1](imagens/netplan_prints/netplan_vmlab02pc4.png)

---

## 6. Prints de ping

## 6.1 PC1

### 6.1.1 Ping com FQDN

### vmlab01pc1 para vm02pc1
![ping vmlab01pc1 para vmlab02pc1](imagens/ping_prints/pc1/FQDN/srv1_to_srv2.png)

### vmlab01pc1 para vm01pc3
![ping vmlab01pc1 para vmlab01pc3](imagens/ping_prints/pc1/FQDN/srv1_to_srv5.png)

### vmlab01pc1 para vm02pc3
![ping vmlab01pc1 para vmlab02pc3](imagens/ping_prints/pc1/FQDN/srv1_to_srv6.png)


### 6.1.2 Ping com hostname

### vmlab01pc1 para vm02pc1
![ping vmlab01pc1 para vmlab02pc1](imagens/ping_prints/pc1/hostname/mvlab01pc1_to_vmlab02pc2.png)

### vmlab01pc1 para vm01pc3
![ping vmlab01pc1 para vmlab02pc3](imagens/ping_prints/pc1/hostname/mvlab01pc1_to_vmlab01pc3.png)

### vmlab01pc1 para vm02pc3
![ping vmlab01pc1 para vmlab02pc1](imagens/ping_prints/pc1/hostname/mvlab01pc1_to_vmlab02pc3.png)



### 6.1.3 Ping com IP

### vmlab01pc1 para vmlab02pc1
![ping vmlab01pc1 para vmlab02pc1](imagens/ping_prints/pc1/ip/vmlab01pc1_to_192-168-26-98.png)

### vmlab01pc1 para vm01pc3
![ping vmlab01pc1 para vmlab01pc3](imagens/ping_prints/pc1/ip/vmlab01pc1_to_192-168-26-101.png)

### vmlab01pc1 para vm02pc3
![ping vmlab01pc1 para vmlab02pc3](imagens/ping_prints/pc1/ip/vmlab01pc1_to_192-168-26-102.png)
---

## 6.2 PC2

### 6.2.1 Ping com FQDN

### vmlab01pc2 para vm02pc2
![ping vmlab01pc1 para vmlab02pc2](imagens/ping_prints/pc2/FQDN/srv3_to_srv04.jpeg)

### vmlab01pc1 para vm01pc4
![ping vmlab01pc1 para vmlab01pc4](imagens/ping_prints/pc2/FQDN/srv3_to_srv7.jpeg)

### 6.2.2 Ping com hostname

### vmlab01pc2 para vm02pc2
![ping vmlab01pc1 para vmlab02pc2](imagens/ping_prints/pc2/hostname/mvlab01pc2_to_vmlab02pc2.jpeg)

### vmlab01pc1 para vm01pc4
![ping vmlab01pc1 para vmlab01pc4](imagens/ping_prints/pc2/hostname/vmlab01pc1_to_vmlab01pc4.jpeg)

### 6.2.3 Ping com IP

### vmlab01pc2 para vm02pc2
![ping vmlab01pc1 para vmlab02pc2](imagens/ping_prints/pc2/ip/vmlab01pc1_to_192-168-26-100.jpeg)

### vmlab01pc1 para vm01pc4
![ping vmlab01pc1 para vmlab01pc4](imagens/ping_prints/pc2/ip/vmlab01pc1_to_192-168-26-103.jpeg)

---

## 6.3 PC3

### 6.3.1 Ping com FQDN

### vmlab01pc3 para vm02pc3

![ping vmlab01pc1 para vmlab02pc2](imagens/ping_prints/pc3/FQDN/srv5_to_srv6.png)

### vmlab01pc3 para vm01pc4
![ping vmlab01pc1 para vmlab01pc4](imagens/ping_prints/pc3/FQDN/srv5_to_srv7.png)

### vmlab01pc3 para vm02pc4
![ping vmlab01pc1 para vmlab02pc4](imagens/ping_prints/pc3/FQDN/srv5_to_srv8.png)


### 6.3.2 Ping com hostname

### vmlab01pc3 para vm02pc3
![ping vmlab01pc3 para vmlab02pc3](imagens/ping_prints/pc3/hostname/vmlab01pc3_to_vmlab02pc3.png)

### vmlab01pc3 para vm01pc4
![ping vmlab01pc3 para vmlab01pc4](imagens/ping_prints/pc3/FQDN/srv5_to_srv7.png)

### vmlab01pc3 para vm02pc4
![ping vmlab01pc3 para vmlab02pc4](imagens/ping_prints/pc3/FQDN/srv5_to_srv8.png)


### 6.3.3 Ping com IP

### vmlab01pc3 para vm01pc3
![ping vmlab01pc3 para vmlab02pc3](imagens/ping_prints/pc3/ip/vmlab01pc3_to_192-168-26-102.png)

### vmlab01pc3 para vm01pc4
![ping vmlab01pc3 para vmlab01pc4](imagens/ping_prints/pc3/ip/vmlab01pc3_to_192-168-26-103.png)

### vmlab01pc3 para vm01pc4
![ping vmlab01pc3 para vmlab02pc4](imagens/ping_prints/pc3/ip/vmlab01pc3_to_192-168-26-104.png)


---

## 6.4 PC4

### 6.4.1 Ping com FQDN

### vmlab01pc4 para vm02pc4
![ping vmlab01pc4 para vmlab02pc4](imagens/ping_prints/pc4/FQDN/srv7_to_srv8.png)

### vmlab01pc4 para vm01pc2
![ping vmlab01pc4 para vmlab01pc2](imagens/ping_prints/pc4/FQDN/srv7_to_srv3.png)

### vmlab01pc4 para vm02pc2
![ping vmlab01pc4 para vmlab02pc2](imagens/ping_prints/pc4/FQDN/srv7_to_srv4.png)


### 6.4.2 Ping com hostname

### vmlab01pc4 para vm02pc4
![ping vmlab01pc4 para vmlab02pc4](imagens/ping_prints/pc4/hostname/vmlab01pc4_to_vmlab02pc4.png)

### vmlab01pc4 para vm01pc2
![ping vmlab01pc4 para vmlab01pc2](imagens/ping_prints/pc4/hostname/vmlab01pc4_to_vmlab02pc4.png)

### vmlab01pc4 para vm02pc2
![ping vmlab01pc4 para vmlab02pc2](imagens/ping_prints/pc4/hostname/vmlab01pc4_to_vmlab02pc2.png)


### 6.4.3 Ping com IP

### vmlab01pc4 para vm02pc4
![ping vmlab01pc4 para vmlab02pc4](imagens/ping_prints/pc4/ip/vmlab01pc4_to_192-168-26-99.png)

### vmlab01pc4 para vm01pc2
![ping vmlab01pc4 para vmlab01pc2](imagens/ping_prints/pc4/ip/vmlab01pc4_to_192-168-26-100.png)

### vmlab01pc4 para vm02pc2
![ping vmlab01pc4 para vmlab02pc2](imagens/ping_prints/pc4/ip/vmlab01pc4_to_192-168-26-104.png)

---

## 7. Conexão SSH
Nesta seção estão documentados os testes de acesso remoto via SSH, comprovando a conectividade entre os nós do Grupo 7 utilizando tanto o usuário administrador quanto os usuários dos integrantes da equipe.

---

### SSH vmlab01pc1 para vmlab1pc1
![SSH vmlab01pc1](imagens/ssh/vmlab01pc1_to_vmlab01pc2.jpeg)

### SSH vmlab01pc1 para vmlab02pc1
![SSH vmlab01pc2](imagens/ssh/vmlab01pc1_to_vmlab02pc1.jpeg)

### SSH vmlab01pc2 para vmlab02pc2
![SSH vmlab01pc3](imagens/ssh/vmlab01pc2_to_vmlab02pc2.jpeg)

### SSH vmlab01pc3 para vmlab01pc4
![SSH vmlab01pc4](imagens/ssh/vmlab01pc3_to_vmlab01pc4.png)

### SSH vmlab01pc3 para vmlab02pc3
![SSH vmlab02pc1](imagens/ssh/vmlab01pc3_to_vmlab02pc3.png)

### SSH vmlab01pc3 para vmlab02pc4
![SSH vmlab02pc2](imagens/ssh/vmlab01pc3_to_vmlab02pc4.png)