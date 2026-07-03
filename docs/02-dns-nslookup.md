# 02 - DNS / nslookup

## Objetivo

Gerar uma consulta DNS utilizando o comando `nslookup` e analisar os pacotes DNS no Wireshark.

O objetivo desta análise é observar como um nome de domínio é resolvido para um endereço IP, identificando consulta, resposta, protocolo utilizado, porta e registros retornados.

## Ambiente

* Sistema operacional: Windows
* Terminal utilizado: Windows PowerShell (x86)
* Interface utilizada: Wi-Fi
* Ferramenta principal: Wireshark
* Rede utilizada: rede doméstica própria/autorizada
* VPN: desativada durante a captura

## Comando utilizado

```powershell
nslookup cisco.com
```

## Filtro utilizado no Wireshark

```text
dns
```

## Evidências

### Filtro DNS aplicado

![Filtro DNS aplicado](../images/02-dns/01-dns-filtro-aplicado.png)

### Detalhes da consulta DNS

![Detalhes da consulta DNS](../images/02-dns/02-dns-query-detalhes.png)

### Detalhes da resposta DNS

![Detalhes da resposta DNS](../images/02-dns/03-dns-response-detalhes.png)

### Resposta com registro A

![Resposta DNS com registro A](../images/02-dns/04-dns-response-answer.png)

## O que foi observado

Durante a captura, foram observados pacotes DNS entre o host local e o servidor DNS configurado na rede.

Foram identificados:

* consulta DNS saindo do host local;
* resposta DNS retornando do servidor DNS;
* uso do protocolo UDP;
* porta de destino `53` na consulta DNS;
* porta de origem `53` na resposta DNS;
* consulta DNS para o domínio `cisco.com`;
* registro do tipo `A`, relacionado a endereço IPv4;
* resposta DNS sem erro;
* endereço IPv4 `72.163.4.185` retornado para `cisco.com`;
* correspondência entre consulta e resposta por meio do Transaction ID.

Também foi possível observar consultas relacionadas a registros `A` e `AAAA`.

O registro `A` está relacionado a endereços IPv4, enquanto o registro `AAAA` está relacionado a endereços IPv6.

## Análise técnica

O comando `nslookup cisco.com` foi utilizado para gerar uma consulta DNS manualmente a partir do terminal.

Na captura, foi possível observar o host local enviando uma consulta DNS para o servidor DNS configurado na rede. Essa consulta utilizou o protocolo UDP, com porta de destino `53`, que é a porta padrão utilizada pelo DNS.

A resposta retornou do servidor DNS para o host local utilizando a porta de origem `53` e a porta de destino temporária utilizada pelo cliente.

A consulta analisada tinha como objetivo resolver o domínio `cisco.com` para um endereço IPv4, utilizando um registro do tipo `A`.

Na resposta DNS, foi possível observar que o domínio `cisco.com` foi resolvido para o endereço IPv4 `72.163.4.185`.

Também foi possível observar que a consulta e a resposta possuíam o mesmo Transaction ID. Isso indica que a resposta recebida corresponde à consulta enviada anteriormente.

## Relação com redes e segurança defensiva

A análise de tráfego DNS é importante para troubleshooting, redes, suporte técnico, NOC e SOC.

O DNS é responsável por traduzir nomes de domínio em endereços IP. Por isso, falhas nesse serviço podem impedir o acesso a sites, sistemas e serviços, mesmo quando a conectividade IP está funcionando.

Esse tipo de análise pode ajudar a responder perguntas como:

```text
O host está conseguindo consultar um servidor DNS?
O servidor DNS está respondendo?
Qual domínio foi consultado?
Qual endereço IP foi retornado?
A resposta DNS apresentou erro?
A consulta utilizou a porta esperada?
O comportamento observado faz sentido?
```

Em segurança defensiva, o DNS também é relevante porque muitas investigações começam pela análise de domínios acessados, consultas suspeitas, respostas incomuns ou tentativas de comunicação com destinos desconhecidos.

## Observações importantes

Durante a captura, foram observadas tentativas de resolução envolvendo o sufixo local `.home`, como `cisco.com.home`, que retornaram resposta indicando que o nome não existia.

Depois disso, a consulta direta para `cisco.com` foi realizada com sucesso.

Esse comportamento pode ocorrer quando o sistema ou a rede tenta aplicar um sufixo DNS local antes de consultar o domínio externo diretamente.

## Aprendizados

Nesta análise, foi possível praticar:

* uso do `nslookup` para gerar consultas DNS;
* captura de tráfego DNS no Wireshark;
* aplicação do filtro `dns`;
* identificação de consulta e resposta DNS;
* observação do uso de UDP;
* identificação da porta `53`;
* leitura de registros DNS do tipo `A`;
* diferença entre registros `A` e `AAAA`;
* interpretação básica de uma resposta DNS;
* relação entre consulta e resposta por meio do Transaction ID.

## Conclusão

A captura mostrou com sucesso o funcionamento básico de uma consulta DNS.

Foi possível observar o host local consultando o servidor DNS para resolver o domínio `cisco.com`, utilizando UDP e porta `53`.

A resposta DNS retornou sem erro e apresentou um endereço IPv4 associado ao domínio consultado.

Essa análise reforçou conceitos fundamentais de redes, como resolução de nomes, DNS, UDP, porta 53, registros `A` e `AAAA`, além da importância do DNS em troubleshooting e segurança defensiva.