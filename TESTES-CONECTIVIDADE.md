# Testes de Conectividade

## Teste 1: Ping para Impressora

### Objetivo
Verificar se o Admin PC consegue alcançar a Printer

### Passo a Passo

1. **Clique no Admin PC**
2. Abra a aba **"Desktop"**
3. Clique em **"Command Prompt"**
4. Digite:ping 192.168.1.100
5. Pressione **Enter**

### Resultado Esperado ✅
C:>ping 192.168.1.100
Pinging 192.168.1.100 with 32 bytes of data:Reply from 192.168.1.100: bytes=32 time<1ms TTL=128
Reply from 192.168.1.100: bytes=32 time<1ms TTL=128
Reply from 192.168.1.100: bytes=32 time<1ms TTL=128
Reply from 192.168.1.100: bytes=32 time<1ms TTL=128Ping statistics for 192.168.1.100:
Packets: Sent = 4, Received = 4, Lost = 0 (0% loss)
Approximate round trip times in milli-seconds:
Minimum = 0ms, Maximum = 0ms, Average = 0ms


### O que Significa?

- **Reply from 192.168.1.100** = Printer respondeu ✅
- **0% loss** = Todos os pacotes chegaram
- **time<1ms** = Latência muito baixa (rede local)
- **TTL=128** = Número de saltos restantes

### Resultado Inesperado ❌
Request timed out. (4 vezes)
Packets: Sent = 4, Received = 0, Lost = 4 (100% loss)


**Causa:** IP da Printer está errado ou não está conectada

**Solução:** Verifique se o IP é 192.168.1.100 (não 192.169.1.100)

---

## Teste 2: Acesso ao Navegador Web

### Objetivo
Verificar se o Admin PC consegue acessar um servidor web

### Passo a Passo

1. **Clique no Admin PC**
2. Abra a aba **"Desktop"**
3. Clique em **"Web Browser"**
4. Na barra de endereço, digite:209.165.200.225
5. Clique em **"Go"**

### Resultado Esperado ✅

Uma página web aparece com:
- Título: **"Cisco Packet Tracer"**
- Mensagem: **"Welcome to Cisco Packet Tracer"**
- Links: "A small page", "Copyrights", "Image page", "Image"

### O que Significa?

- Admin PC conseguiu alcançar o servidor
- Servidor respondeu com uma página HTML
- Conectividade com a internet está funcionando ✅

### Resultado Inesperado ❌

Página em branco ou "Connection refused"

**Causa:** Servidor não está acessível ou IP está errado

**Solução:** Verifique se o IP é 209.165.200.225

---

## Teste 3: Verificar Configuração de IP

### Objetivo
Visualizar a configuração de IP do Admin PC

### Passo a Passo

1. **Clique no Admin PC**
2. Abra a aba **"Desktop"**
3. Clique em **"Command Prompt"**
4. Digite:ipconfig
5. Pressione **Enter**

### Resultado Esperado ✅ 
FastEthernet0 Connection: (default port)
Connection-specific DNS Suffix..:
Link-local IPv6 Address.........: FE80::260:5CFF:FE88:4291
IPv6 Address....................: ::
IPv4 Address....................: 192.168.1.2
Subnet Mask.....................: 255.255.255.0
Default Gateway.................: 192.168.1.1


### O que Verificar

- ✅ IPv4 Address: 192.168.1.2
- ✅ Subnet Mask: 255.255.255.0
- ✅ Default Gateway: 192.168.1.1

---

## Teste 4: Rastrear Caminho até Servidor

### Objetivo
Ver o caminho que os pacotes fazem até o servidor

### Passo a Passo

1. **Clique no Admin PC**
2. Abra a aba **"Desktop"**
3. Clique em **"Command Prompt"**
4. Digite:tracert 209.165.200.225
5. Pressione **Enter**

### Resultado Esperado ✅
C:>tracert 209.165.200.225
Tracing route to 209.165.200.225 over a maximum of 30 hops:1    0 ms    0 ms    0 ms    192.168.1.1
2    0 ms    0 ms    0 ms    209.165.200.233
3    0 ms    0 ms    0 ms    209.165.200.225Trace complete.


### O que Significa?

- **Hop 1:** 192.168.1.1 (Office Router - seu gateway)
- **Hop 2:** 209.165.200.233 (Roteador intermediário)
- **Hop 3:** 209.165.200.225 (Servidor web de destino)
- **0 ms:** Latência (rede simulada é muito rápida)

### Interpretação

O pacote faz **3 saltos** para chegar ao servidor:
1. Sai do Admin PC
2. Passa pelo Office Router
3. Passa por um roteador intermediário
4. Chega ao servidor

---

## Resumo dos Testes

| Teste | Comando | Resultado | Status |
|---|---|---|---|
| Ping Printer | `ping 192.168.1.100` | 0% loss | ✅ |
| Navegador Web | Acessar 209.165.200.225 | Página carregada | ✅ |
| ipconfig | `ipconfig` | IP correto | ✅ |
| tracert | `tracert 209.165.200.225` | 3 hops | ✅ |

---

## Troubleshooting

### Ping falha
1. Verifique se o IP está correto
2. Verifique se o dispositivo está ligado
3. Verifique se o cabo está conectado

### Navegador não carrega
1. Verifique se o servidor está acessível
2. Tente fazer ping primeiro
3. Verifique o IP do servidor

### ipconfig mostra 0.0.0.0
1. DHCP não funcionou
2. Verifique se o roteador está ligado
3. Tente configurar IP manualmente
