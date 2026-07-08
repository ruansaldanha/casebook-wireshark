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

---

## 03 - ARP / Gateway

### Objetivo

Gerar e observar tráfego ARP para analisar a associação entre endereços IP e endereços MAC na rede local.

### Comandos utilizados

```powershell
ipconfig
arp -a
ping 192.168.1.1
```

### Filtro utilizado no Wireshark

```text
arp
```

### Arquivo de captura local

```text
captures-local/03-arp-gateway.pcapng
```

### Evidências salvas

```text
images/03-arp/01-arp-filtro-aplicado.png
images/03-arp/02-arp-request-detalhes.png
images/03-arp/03-arp-reply-detalhes.png
```

### Observação

Durante a captura, foi observado tráfego ARP envolvendo o gateway e o host local. Como o endereço do gateway já estava presente na tabela ARP do host, a análise destacou um fluxo em que o gateway consultou o endereço MAC associado ao IP do host local, seguido pela resposta ARP correspondente.

---

## 04 - TCP Handshake

### Objetivo

Gerar tráfego TCP para observar o processo de estabelecimento de conexão por meio do Three-Way Handshake.

### Comando utilizado

```powershell
curl.exe -4 http://example.com
```

### Filtro utilizado no Wireshark

```text
tcp.port == 80
```

### Arquivo de captura local

```text
captures-local/04-tcp-handshake.pcapng
```

### Evidências salvas

```text
images/04-tcp/01-tcp-filtro-aplicado.png
images/04-tcp/02-tcp-syn-detalhes.png
images/04-tcp/03-tcp-syn-ack-detalhes.png
images/04-tcp/04-tcp-ack-detalhes.png
```

### Observação

Durante a captura, foi possível observar a sequência `SYN`, `SYN, ACK` e `ACK`, que representa o TCP Three-Way Handshake. Após o estabelecimento da conexão, também apareceu tráfego HTTP relacionado à requisição feita com `curl.exe`.

---

## 05 - HTTP vs HTTPS

### Objetivo

Comparar o tráfego HTTP e HTTPS no Wireshark, observando a diferença entre uma comunicação em texto claro e uma comunicação protegida por TLS.

### Comandos utilizados

```powershell
curl.exe -4 http://example.com
curl.exe -4 https://example.com
```

### Filtros utilizados no Wireshark

Para visualizar o tráfego HTTP:

```text
http
```

Para visualizar o tráfego HTTPS/TLS:

```text
tls
```

Filtro utilizado para isolar o fluxo TLS relacionado ao servidor acessado:

```text
tls && ip.addr == 172.66.147.243
```

### Arquivo de captura local

```text
captures-local/05-http-vs-https.pcapng
```

### Evidências salvas

```text
images/05-http-https/01-http-filtro-aplicado.png
images/05-http-https/02-http-get-detalhes.png
images/05-http-https/03-http-response-detalhes.png
images/05-http-https/04-https-filtro-aplicado.png
images/05-http-https/05-https-client-hello-detalhes.png
images/05-http-https/06-https-application-data.png
```

### Observação

Durante a captura HTTP, foi possível visualizar diretamente a requisição `GET / HTTP/1.1` e a resposta `HTTP/1.1 200 OK` no Wireshark.

Na captura HTTPS, o conteúdo da comunicação não apareceu em texto claro. Em vez disso, foram observados pacotes relacionados à negociação TLS, como `Client Hello`, `Server Hello` e `Application Data`. No pacote `Client Hello`, também foi possível observar o SNI indicando o domínio `example.com`.

A principal diferença observada foi que, no HTTP, a requisição e a resposta ficam legíveis na captura. Já no HTTPS, o conteúdo da aplicação fica protegido pelo TLS e aparece como dados criptografados.

---

## 06 - DHCP

### Objetivo

Gerar tráfego DHCP para observar o processo de liberação e renovação da configuração IP do host na rede local.

### Comandos utilizados

```powershell
ipconfig /release
ipconfig /renew
```

### Filtro utilizado no Wireshark

```text
dhcp
```

### Arquivo de captura local

```text
captures-local/06-dhcp.pcapng
```

### Evidências salvas

```text
images/06-dhcp/01-dhcp-filtro-aplicado.png
images/06-dhcp/02-dhcp-discover-detalhes.png
images/06-dhcp/03-dhcp-offer-detalhes.png
images/06-dhcp/04-dhcp-request-detalhes.png
images/06-dhcp/05-dhcp-ack-detalhes.png
```

### Observação

Durante a captura, foi observado o processo de liberação e renovação da configuração IP do host. O pacote `DHCP Release` apareceu após o uso do comando `ipconfig /release`, indicando que a configuração anterior foi liberada.

Em seguida, foi possível observar a sequência principal do DHCP:

```text
Discover → Offer → Request → ACK
```

Essa sequência mostra o host procurando um servidor DHCP, recebendo uma oferta de configuração, solicitando o uso dessa configuração e recebendo a confirmação final do servidor.

Nos pacotes analisados, também apareceram informações como endereço IP oferecido, identificador do servidor DHCP, máscara de sub-rede, gateway, DNS e tempo de lease.