# Instituto Federal de Alagoas
## Fundamentos de redes de computadores
## Grupo7
Emerson Gomes Vanderlei da Silva <br>
Tainá Ferreira Miranda <br>
Matheus Azafhi Goes de Souza <br>
Heitor Moreira Costa

---

## Sumário
* [1. Tabela de Hardware das VMs](#1-tabela-de-hardware-das-vms)
* [2. Tabela de Endereçamento IP e Hardware](#2-tabela-de-endereçamento-ip-e-hardware)
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

## 1. Tabela de Hardware das VMs

| Componente | Configuração por VM |
| :--- | :--- |
| **Sistema Operacional** | Ubuntu Server 22.04 LTS |
| **Processador (vCPU)** | 1 Core/Processador |
| **Memória RAM** | 2048 MB (1GB) |
| **Disco Rígido (HD)** | 25 GB (Alocação Dinâmica) |
| **Placa de Rede** | 1 Interface em modo bridge |

---

## 2. Tabela de Endereçamento IP e Hardware

| Máquina Virtual | Host Físico | Nome do Host (Hostname) | Endereço IP / Máscara |
| :--- | :--- | :--- | :--- |
| VM Lab01@PC1 | PC1 | `vmlab01pc1` | 192.168.26.97/28 |
| VM Lab02@PC1 | PC1 | `vmlab02pc1` | 192.168.26.98/28 |
| VM Lab01@PC2 | PC2 | `vmlab01pc2` | 192.168.26.99/28 |
| VM Lab02@PC2 | PC2 | `vmlab02pc2` | 192.168.26.100/28 |
| VM Lab01@PC3 | PC3 | `vmlab01pc3` | 192.168.26.101/28 |
| VM Lab02@PC3 | PC3 | `vmlab02pc3` | 192.168.26.102/28 |
| VM Lab01@PC4 | PC4 | `vmlab01pc4` | 192.168.26.103/28 |
| VM Lab02@PC4 | PC4 | `vmlab02pc4` | 192.168.26.104/28 |

---

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