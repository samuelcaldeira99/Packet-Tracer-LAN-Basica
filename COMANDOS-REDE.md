# Comandos Essenciais de Rede

## 1. PING

### Sintaxe
ping [endereço IP ou hostname]

### Exemplos
ping 192.168.1.100
ping 209.165.200.225
ping google.com


### O que Faz?
- Envia pacotes ICMP para um destino
- Aguarda resposta
- Mostra latência e taxa de perda

### Interpretação

**Sucesso:**
Reply from 192.168.1.100: bytes=32 time<1ms TTL=128
Packets: Sent = 4, Received = 4, Lost = 0 (0% loss)
✅ Dispositivo está acessível

**Falha:**
Request timed out.
Packets: Sent = 4, Received = 0, Lost = 4 (100% loss) 

❌ Dispositivo não está acessível

### Quando Usar
- Testar conectividade básica
- Verificar se um servidor está online
- Diagnosticar problemas de rede

---

## 2. IPCONFIG

### Sintaxe
ipconfig
ipconfig /all
FastEthernet0 Connection: (default port)
IPv4 Address: 192.168.1.2
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1
DNS Server: 209.165.200.225


### Informações Importantes

| Campo | Significado |
|---|---|
| IPv4 Address | Seu IP na rede |
| Subnet Mask | Tamanho da rede |
| Default Gateway | Roteador (saída para internet) |
| DNS Server | Servidor de nomes |

### Quando Usar
- Verificar seu IP
- Confirmar que DHCP funcionou
- Diagnosticar problemas de configuração

---

## 3. TRACERT (Trace Route)

### Sintaxe
tracert [endereço IP ou hostname]

### Exemplos
tracert 209.165.200.225
tracert google.com


### O que Faz?
- Mostra o caminho que os pacotes fazem até o destino
- Exibe cada "hop" (salto) na rota
- Mostra latência de cada salto

### Exemplo de Saída
Tracing route to 209.165.200.225 over a maximum of 30 hops:1    0 ms    0 ms    0 ms    192.168.1.1
2    0 ms    0 ms    0 ms    209.165.200.233
3    0 ms    0 ms    0 ms    209.165.200.225Trace complete.


### Interpretação

| Hop | IP | Latência | Significado |
|---|---|---|---|
| 1 | 192.168.1.1 | 0 ms | Seu gateway (router local) |
| 2 | 209.165.200.233 | 0 ms | Roteador intermediário |
| 3 | 209.165.200.225 | 0 ms | Servidor de destino |

### Quando Usar
- Diagnosticar problemas de roteamento
- Identificar onde a conexão falha
- Entender o caminho dos pacotes

---

## 4. IPCONFIG /ALL

### Sintaxe
ipconfig /all

### O que Faz?
- Mostra informações detalhadas de todas as interfaces
- Inclui MAC address, DHCP status, etc.

### Informações Adicionais
MAC Address: 00D0.97E3.7797
DHCP Enabled: Yes
DHCP Server: 192.168.1.1
Lease Obtained: [data/hora]
Lease Expires: [data/hora]


### Quando Usar
- Obter MAC address
- Verificar status do DHCP
- Diagnosticar problemas avançados

---

## Resumo Rápido

| Comando | Função | Exemplo |
|---|---|---|
| `ping` | Testar conectividade | `ping 192.168.1.100` |
| `ipconfig` | Ver configuração de IP | `ipconfig` |
| `tracert` | Ver caminho até destino | `tracert 209.165.200.225` |
| `ipconfig /all` | Ver detalhes completos | `ipconfig /all` |

---

## Dicas de Troubleshooting

### 1. Ping falha
Passo 1: Verifique o IP com ipconfig
Passo 2: Confirme que o IP está correto
Passo 3: Tente ping no gateway (192.168.1.1)
Passo 4: Se gateway responde, problema está no destino


### 2. Sem conectividade
Passo 1: Execute ipconfig
Passo 2: Verifique se tem IP (não 0.0.0.0)
Passo 3: Se 0.0.0.0, DHCP falhou
Passo 4: Configure IP manualmente

### 3. Servidor não responde
Passo 1: Faça ping no servidor
Passo 2: Se ping falha, use tracert
Passo 3: Identifique em qual hop falha
Passo 4: Verifique roteamento naquele ponto

