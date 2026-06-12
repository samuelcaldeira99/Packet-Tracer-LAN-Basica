# Diagramas Visuais

## 1. Topologia da Rede
    [Internet]
         |
    [Router]
         |
    [Switch]
    /   |   \
[PC1] [PC2] [Printer]

---

## 2. Ping - Falha ❌
C:>ping 192.168.1.100
Request timed out. (4x)
Packets: Sent=4, Received=0, Lost=4 (100% loss)


---

## 3. Ping - Sucesso ✅
C:>ping 192.168.1.100
Reply from 192.168.1.100: time<1ms (4x)
Packets: Sent=4, Received=4, Lost=0 (0% loss)
---

## 4. Navegador Web ✅
URL: 209.165.200.225
Status: Conectado ✅
Página: Cisco Packet Tracer
---

## 5. ipconfig
IPv4 Address: 192.168.1.2
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1
---

## 6. Tracert
Hop 1: 192.168.1.1 (0ms)
Hop 2: 209.165.200.233 (0ms)
Hop 3: 209.165.200.225 (0ms)
Trace complete ✅
