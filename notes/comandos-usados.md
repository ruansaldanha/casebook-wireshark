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

---

## 02 - DNS / nslookup

### Objetivo

Gerar tráfego DNS para observar consultas e respostas de resolução de nomes no Wireshark.

### Comando utilizado

```powershell
nslookup cisco.com
```

### Filtro utilizado no Wireshark

```text
dns
```

### Arquivo de captura local

```text
captures-local/02-dns-nslookup-cisco.pcapng
```

### Evidências salvas

```text
images/02-dns/01-dns-filtro-aplicado.png
images/02-dns/02-dns-query-detalhes.png
images/02-dns/03-dns-response-detalhes.png
images/02-dns/04-dns-response-answer.png
```

### Observação

Durante a captura, foram observadas tentativas de resolução com sufixo local, como `cisco.com.home`, que retornaram resposta indicando que o nome não existia. Em seguida, a consulta direta para `cisco.com` foi realizada com sucesso.