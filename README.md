# redes-projeto-grupo7

# Tabelas de Configuração de Hardware, Endereçamento e Domínio

## 1. Tabela de Hardware das VMs
[cite_start]Esta tabela descreve as especificações técnicas configuradas para cada uma das Máquinas Virtuais[cite: 1, 2].

| Componente | Configuração por VM |
| :--- | :--- |
| **Sistema Operacional** | [cite_start]Ubuntu Server 22.04 LTS [cite: 2] |
| **Processador (vCPU)** | [cite_start]1 Core/Processador [cite: 2] |
| **Memória RAM** | [cite_start]1024 MB (1GB) [cite: 2] |
| **Disco Rígido (HD)** | [cite_start]10 GB (Alocação Dinâmica) [cite: 2] |
| **Placa de Rede** | [cite_start]1 Interface em modo bridge [cite: 2] |

---

## 2. Tabela de Endereçamento IP e Hardware
[cite_start]Esta tabela relaciona as Máquinas Virtuais aos seus respectivos hosts físicos, hostnames e endereços IP de rede com máscara[cite: 3, 4].

| Máquina Virtual | Host Físico | Nome do Host (Hostname) | Endereço IP / Máscara |
| :--- | :--- | :--- | :--- |
| VM Lab01@PC1 | [cite_start]PC1 [cite: 4] | [cite_start]`vmlab01pc1` [cite: 4] | [cite_start]192.168.26.97/28 [cite: 4] |
| VM Lab02@PC1 | [cite_start]PC1 [cite: 4] | [cite_start]`vmlab02pc1` [cite: 4] | [cite_start]192.168.26.98/28 [cite: 4] |
| VM Lab01@PC2 | [cite_start]PC2 [cite: 4] | [cite_start]`vmlab01pc2` [cite: 4] | [cite_start]192.168.26.99/28 [cite: 4] |
| VM Lab02@PC2 | [cite_start]PC2 [cite: 4] | [cite_start]`vmlab02pc2` [cite: 4] | [cite_start]192.168.26.100/28 [cite: 4] |
| VM Lab01@PC3 | [cite_start]PC3 [cite: 4] | [cite_start]`vmlab01pc3` [cite: 4] | [cite_start]192.168.26.101/28 [cite: 4] |
| VM Lab02@PC3 | [cite_start]PC3 [cite: 4] | [cite_start]`vmlab02pc3` [cite: 4] | [cite_start]192.168.26.102/28 [cite: 4] |
| VM Lab01@PC4 | [cite_start]PC4 [cite: 5] | [cite_start]`vmlab01pc4` [cite: 5] | [cite_start]192.168.26.103/28 [cite: 5] |
| VM Lab02@PC4 | [cite_start]PC4 [cite: 5] | [cite_start]`vmlab02pc4` [cite: 5] | [cite_start]192.168.26.104/28 [cite: 5] |

---

## 3. Tabela de Nomenclatura e Domínio (FQDN)
[cite_start]Esta tabela mapeia os endereços IP para o Nome de Domínio Completo (FQDN) e define os apelidos configurados para cada servidor[cite: 6, 7].

| Endereço IP | Hostname Curto | Nome de Domínio Completo (FQDN) | Apelidos (Aliases) |
| :--- | :--- | :--- | :--- |
| 192.168.26.97 | [cite_start]`vmlab01pc1` [cite: 7] | [cite_start]`vmlab01pc1.grupo7.bsi-26-1.maceio.lab` [cite: 7] [cite_start]| vm01pc1, srv1 [cite: 7] |
| 192.168.26.98 | [cite_start]`vmlab02pc1` [cite: 7] | [cite_start]`vmlab02pc1.grupo7.bsi-26-1.maceio.lab` [cite: 7] [cite_start]| vm02pc1, srv2 [cite: 7] |
| 192.168.26.99 | [cite_start]`vmlab01pc2` [cite: 7] | [cite_start]`vmlab01pc2.grupo7.bsi-26-1.maceio.lab` [cite: 7] [cite_start]| vm01pc2, srv3 [cite: 7] |
| 192.168.26.100 | [cite_start]`vmlab02pc2` [cite: 7] | [cite_start]`vmlab02pc2.grupo7.bsi-26-1.maceio.lab` [cite: 7] [cite_start]| vm02pc2, srv4 [cite: 7] |
| 192.168.26.101 | [cite_start]`vmlab01pc3` [cite: 7] | [cite_start]`vmlab01pc3.grupo7.bsi-26-1.maceio.lab` [cite: 7] [cite_start]| vm01pc3, srv5 [cite: 7] |
| 192.168.26.102 | [cite_start]`vmlab02pc3` [cite: 8] | [cite_start]`vmlab02pc3.grupo7.bsi-26-1.maceio.lab` [cite: 8] [cite_start]| vm02pc3, srv6 [cite: 8] |
| 192.168.26.103 | [cite_start]`vmlab01pc4` [cite: 8] | [cite_start]`vmlab01pc4.grupo7.bsi-26-1.maceio.lab` [cite: 8] [cite_start]| vm01pc4, srv7 [cite: 8] |
| 192.168.26.104 | [cite_start]`vmlab02pc4` [cite: 8] | [cite_start]`vmlab02pc4.grupo7.bsi-26-1.maceio.lab` [cite: 8] [cite_start]| vm02pc4, srv8 [cite: 8] |
