# Instituto Federal de Alagoas
## Fundamentos de redes de computadores
## Grupo7
Emerson Gomes Vanderlei da Silva
Tainá Miranda Ferreira
Matheus Azafhi Goes de Souza 
Heitor Moreira Costa


# Tabelas de Configuração de Hardware, Endereçamento e Domínio

# 1. Tabela de Hardware das VMs

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

## 4. Usuŕios e senhas
admingrupo7 = 0123456789

taina.ferreira = 0123456789@

matheus.souza = 0123456789@

heitor.costa = 0123456789@

emerson.silva = 0123456789@

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

## 6. Prints de ping com alias

### vmlab01pc1 para vm02pc1

![ping vmlab01pc1 para vmlab02pc1](imagens/ping_prints/pc1/alias/srv1_to_srv02.png)

### vmlab01pc1 para vm01pc2

![ping vmlab01pc1 para vmlab01pc2](imagens/ping_prints/pc1/alias/srv1_to_srv03.png)

### vmlab01pc1 para vm02pc2

![ping vmlab01pc1 para vmlab02pc2](imagens/ping_prints/pc1/alias/srv1_to_srv04.png)

### vmlab01pc1 para vm01pc3

![ping vmlab01pc1 para vmlab01pc3](imagens/ping_prints/pc1/alias/srv1_to_srv05.png)

### vmlab01pc1 para vm02pc3

![ping vmlab01pc1 para vmlab02pc3](imagens/ping_prints/pc1/alias/srv1_to_srv06.png)

### vmlab01pc1 para vm01pc4

![ping vmlab01pc1 para vmlab01pc4](imagens/ping_prints/pc1/alias/srv1_to_srv07.png)

### vmlab01pc1 para vm02pc4

![ping vmlab01pc1 para vmlab02pc4](imagens/ping_prints/pc1/alias/srv1_to_srv08.png)


## 6.1 Ping com IP

![ping vmlab01pc1 para vmlab02pc1](imagens/ping_prints/pc1/ip/vmlab01pc1_to_192-168-26-98.png)

### vmlab01pc1 para vm01pc2

![ping vmlab01pc1 para vmlab01pc2](imagens/ping_prints/pc1/ip/vmlab01pc1_to_192-168-26-99.png)

### vmlab01pc1 para vm02pc2

![ping vmlab01pc1 para vmlab02pc2](imagens/ping_prints/pc1/ip/vmlab01pc1_to_192-168-26-100.png)

### vmlab01pc1 para vm01pc3

![ping vmlab01pc1 para vmlab01pc3](imagens/ping_prints/pc1/ip/vmlab01pc1_to_192-168-26-101.png)

### vmlab01pc1 para vm02pc3

![ping vmlab01pc1 para vmlab02pc3](imagens/ping_prints/pc1/ip/vmlab01pc1_to_192-168-26-102.png)

### vmlab01pc1 para vm01pc4

![ping vmlab01pc1 para vmlab01pc4](imagens/ping_prints/pc1/ip/vmlab01pc1_to_192-168-26-103.png)

### vmlab01pc1 para vm02pc4

![ping vmlab01pc1 para vmlab02pc4](imagens/ping_prints/pc1/ip/vmlab01pc1_to_192-168-26-104.png)
