# Comandos usados no projeto

Este arquivo reúne os principais comandos, ações e filtros utilizados durante as análises do projeto.

---

## 01 - ICMP / Ping

### Objetivo

Gerar tráfego ICMP para verificar conectividade IP com um destino externo e analisar os pacotes no Wireshark.

### Comando utilizado

```powershell
ping 8.8.8.8
```

### Filtro utilizado no Wireshark

```text
icmp && ip.addr == 8.8.8.8
```

### Arquivo de captura local

```text
captures-local/01-icmp-ping-8.8.8.8.pcapng
```

### Evidências salvas

```text
images/01-icmp/01-icmp-filtro-aplicado.png
images/01-icmp/02-icmp-echo-request-detalhes.png
```

### Observação

A VPN foi desativada durante a captura, pois com a VPN ativa o tráfego poderia ser roteado por uma interface virtual, dificultando a visualização dos pacotes ICMP esperados na interface Wi-Fi.
