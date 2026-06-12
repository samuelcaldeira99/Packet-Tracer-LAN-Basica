# Configuração de Endereços IP

## Visão Geral

Neste lab, configuramos **3 tipos de IP**:
- **DHCP** nos PCs (automático)
- **IP Estático** na Printer (fixo)
- **IP Estático** no Router (gateway)

---

## 1. Configurar Admin PC com DHCP

### Passo a Passo

1. **Clique no Admin PC**
2. Abra a aba **"Desktop"**
3. Clique em **"IP Configuration"**
4. Selecione **"DHCP"** (radio button)
5. Aguarde a mensagem: **"DHCP request successful"**

### Resultado Esperado

Interface: FastEthernet0
IP Configuration: DHCP ✅IPv4 Address: 192.168.1.2
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1
DNS Server: 209.165.200.225



### O que Acontece?

- O Admin PC envia uma solicitação DHCP
- O Office Router (servidor DHCP) responde
- O Admin PC recebe o IP **192.168.1.2**
- Configuração automática completa!

---

## 2. Configurar Manager PC com DHCP

### Passo a Passo

1. **Clique no Manager PC**
2. Abra a aba **"Desktop"**
3. Clique em **"IP Configuration"**
4. Selecione **"DHCP"** (radio button)
5. Aguarde a mensagem: **"DHCP request successful"**

### Resultado Esperado

Interface: FastEthernet0
IP Configuration: DHCP ✅IPv4 Address: 192.168.1.3
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1
DNS Server: 209.165.200.225


### Diferença do Admin PC

- Mesmo protocolo (DHCP)
- IP diferente (192.168.1.3 em vez de 192.168.1.2)
- Cada dispositivo recebe um IP único

---

## 3. Configurar Printer com IP Estático

### ⚠️ IMPORTANTE: Usar a aba "Config", não "Desktop"!

### Passo a Passo

1. **Clique na Printer**
2. Abra a aba **"Config"** (não Desktop!)
3. No painel esquerdo, clique em **"FastEthernet0"**
4. Selecione **"Static"** (radio button)
5. Configure:
   - **IPv4 Address:** 192.168.1.100
   - **Subnet Mask:** 255.255.255.0

### Resultado Esperado

Interface: FastEthernet0
IP Configuration: Static ✅IPv4 Address: 192.168.1.100
Subnet Mask: 255.255.255.0
MAC Address: 00D0.97E3.7797


### Por que IP Estático na Printer?

- Impressoras precisam de IP **fixo**
- Outros dispositivos precisam saber onde encontrá-la
- Se o IP mudasse, ninguém conseguiria imprimir!

---

## 4. Verificar Configuração do Router

### Passo a Passo

1. **Clique no Office Router**
2. Abra a aba **"Config"**
3. Procure por **"FastEthernet0"** ou **"VLAN1"**
4. Verifique se o IP é **192.168.1.1**

### Configuração Esperada

Interface: FastEthernet0 / VLAN1
IP Address: 192.168.1.1
Subnet Mask: 255.255.255.0


---

## Resumo da Configuração

| Dispositivo | IP | Máscara | Gateway | Tipo | Status |
|---|---|---|---|---|---|
| Office Router | 192.168.1.1 | 255.255.255.0 | - | Estático | ✅ |
| Admin PC | 192.168.1.2 | 255.255.255.0 | 192.168.1.1 | DHCP | ✅ |
| Manager PC | 192.168.1.3 | 255.255.255.0 | 192.168.1.1 | DHCP | ✅ |
| Printer | 192.168.1.100 | 255.255.255.0 | - | Estático | ✅ |

---

## Troubleshooting

### Problema: "DHCP request failed"
**Solução:** Verifique se o roteador está ligado e se o cabo está conectado

### Problema: IP não aparece
**Solução:** Aguarde alguns segundos e clique em "Refresh"

### Problema: IP errado (ex: 192.169.1.100)
**Solução:** Verifique se digitou corretamente. Deve ser **192.168** (não 192.169)

---

## Conceitos-Chave

### DHCP (Dynamic Host Configuration Protocol)
- Protocolo que **distribui IPs automaticamente**
- Servidor DHCP: Office Router
- Clientes DHCP: Admin PC, Manager PC
- Vantagem: Não precisa configurar manualmente

### IP Estático
- Endereço IP **fixo e permanente**
- Configurado manualmente
- Ideal para: Servidores, Impressoras, Roteadores
- Vantagem: Sempre no mesmo endereço

### Gateway Padrão
- Roteador que conecta a rede local à internet
- Todos os dispositivos precisam conhecer
- Neste caso: 192.168.1.1
- Função: Encaminhar pacotes para fora da rede local

### Subnet Mask
- Define o tamanho da rede
- 255.255.255.0 = Rede /24
- Todos os dispositivos usam a mesma máscara
