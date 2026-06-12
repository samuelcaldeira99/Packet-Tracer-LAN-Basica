# Topologia da Rede

## Diagrama Visual

                ☁️ Internet (ISP1)
                       |
                🔀 Office Router
                (192.168.1.1)
                       |
                📦 Switch
                /      |      \
          💻 Admin PC  💻 Manager PC  🖨️ Printer
          192.168.1.2  192.168.1.3  192.168.1.100
          (DHCP)       (DHCP)       (Estático)

          
## Descrição dos Dispositivos

### 1. Office Router
- **Tipo:** Roteador Cisco
- **Função:** Gateway da rede, conecta LAN à internet
- **IP:** 192.168.1.1 (Gateway padrão)
- **Portas:**
  - G0/0: Conecta à Internet (ISP1)
  - G0/1: Conecta ao Switch

### 2. Switch
- **Tipo:** Switch Layer 2 (L2)
- **Função:** Distribuidor de conexões na LAN
- **Portas Usadas:**
  - G0/1: Conecta ao Office Router
  - F0/1: Conecta ao Admin PC
  - F0/2: Conecta ao Manager PC
  - F0/24: Conecta à Printer

### 3. Admin PC
- **Tipo:** Computador pessoal
- **IP:** 192.168.1.2 (DHCP)
- **Função:** Máquina de trabalho
- **Interface:** FastEthernet0

### 4. Manager PC
- **Tipo:** Computador pessoal
- **IP:** 192.168.1.3 (DHCP)
- **Função:** Máquina de trabalho
- **Interface:** FastEthernet0

### 5. Printer
- **Tipo:** Impressora de rede
- **IP:** 192.168.1.100 (Estático)
- **Função:** Dispositivo compartilhado na rede
- **Interface:** FastEthernet0

### 6. Internet (ISP1)
- **Tipo:** Provedor de Internet
- **Função:** Conecta a rede local ao mundo exterior
- **Representação:** Nuvem (Cloud)

---

## Tabela de Endereçamento

| Dispositivo | Interface | IP | Máscara | Gateway | Tipo |
|---|---|---|---|---|---|
| Office Router | G0/1 | 192.168.1.1 | 255.255.255.0 | - | Estático |
| Admin PC | FastEthernet0 | 192.168.1.2 | 255.255.255.0 | 192.168.1.1 | DHCP |
| Manager PC | FastEthernet0 | 192.168.1.3 | 255.255.255.0 | 192.168.1.1 | DHCP |
| Printer | FastEthernet0 | 192.168.1.100 | 255.255.255.0 | - | Estático |

---

## Análise da Sub-rede

- **Rede:** 192.168.1.0/24
- **Máscara:** 255.255.255.0
- **Gateway:** 192.168.1.1
- **Primeiro IP:** 192.168.1.1
- **Último IP:** 192.168.1.254
- **Total de IPs:** 254 (256 - 2)
- **IPs Usados:** 4 (Router, 2 PCs, Printer)
- **IPs Disponíveis:** 250

---

## Fluxo de Dados

### Comunicação Interna (Admin PC → Printer)
1. Admin PC envia pacote para 192.168.1.100
2. Switch recebe e encaminha para Printer
3. Printer responde diretamente ao Admin PC
4. Latência: ~0ms (rede local)

### Comunicação Externa (Admin PC → Internet)
1. Admin PC envia pacote para 209.165.200.225
2. Switch encaminha para Office Router
3. Office Router roteia para Internet (ISP1)
4. Resposta volta pelo mesmo caminho

---

## Conexões de Cabo

| De | Para | Tipo | Status |
|---|---|---|---|
| Office Router G0/1 | Switch G0/1 | Copper Straight-Through | ✅ Conectado |
| Office Router G0/0 | Internet ISP1 | Copper Straight-Through | ✅ Conectado |
| Admin PC NIC | Switch F0/1 | Copper Straight-Through | ✅ Conectado |
| Manager PC NIC | Switch F0/2 | Copper Straight-Through | ✅ Conectado |
| Printer NIC | Switch F0/24 | Copper Straight-Through | ✅ Conectado |

---

## Observações

- Todos os cabos são **Copper Straight-Through** (diretos)
- Todos os links estão **ativos** (triângulos verdes no Packet Tracer)
- A rede usa **IPv4** (IPv6 não configurado)
- Não há **VLAN** configurada (todos na VLAN padrão)
- Não há **ACL** ou **Firewall** configurado
