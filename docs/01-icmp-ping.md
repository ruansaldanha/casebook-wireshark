# 01 - ICMP / Ping

## Objetivo

Verificar conectividade IP com um destino externo usando o comando `ping` e analisar os pacotes ICMP no Wireshark.

Nesta primeira análise, a ideia foi observar como um teste simples de conectividade aparece na rede e quais informações podem ser interpretadas a partir dos pacotes capturados.

## Ambiente

* Sistema operacional: Windows
* Terminal utilizado: Windows PowerShell
* Interface utilizada: Wi-Fi
* Ferramenta principal: Wireshark
* Rede utilizada: rede doméstica própria/autorizada
* VPN: desativada durante a captura

## Comando utilizado

```powershell
ping 8.8.8.8
```

## Filtro utilizado no Wireshark

```text
icmp && ip.addr == 8.8.8.8
```

## Evidências

### Filtro ICMP aplicado

![Filtro ICMP aplicado](../images/01-icmp/01-icmp-filtro-aplicado.png)

### Detalhes do Echo Request

![Detalhes do Echo Request](../images/01-icmp/02-icmp-echo-request-detalhes.png)

## O que foi observado

Durante a captura, apareceram pacotes ICMP entre o host local e o endereço `8.8.8.8`.

O comportamento observado foi o esperado para o comando `ping`: o host local enviou pacotes **Echo Request** para o destino e recebeu pacotes **Echo Reply** como resposta.

Foram identificados:

* pacotes **Echo Request** saindo do host local;
* pacotes **Echo Reply** retornando do destino;
* endereço IP de origem local;
* endereço IP de destino `8.8.8.8`;
* protocolo ICMP encapsulado em IPv4;
* campo TTL;
* tipo ICMP `Echo Request (8)` nas requisições;
* tipo ICMP `Echo Reply (0)` nas respostas;
* código ICMP `0`.

Nos detalhes do pacote, foi possível visualizar as camadas:

* Ethernet II;
* Internet Protocol Version 4;
* Internet Control Message Protocol.

## Análise técnica

O comando `ping` utiliza o protocolo ICMP para testar conectividade entre dois hosts.

Na prática, o host local envia uma mensagem **Echo Request** para o destino e aguarda uma mensagem **Echo Reply** como resposta. Na captura realizada, esse fluxo apareceu claramente: o computador enviou requisições ICMP para `8.8.8.8` e recebeu respostas do mesmo endereço.

Esse resultado indica que havia conectividade IP entre o host local e o destino externo testado.

Um ponto importante observado na análise foi a diferença entre o destino IP e a comunicação local em Ethernet. Embora o IP de destino fosse `8.8.8.8`, o quadro Ethernet utiliza endereços MAC relacionados ao enlace local. Isso acontece porque, para alcançar um destino fora da rede local, o host envia o tráfego para o próximo salto, normalmente o gateway.

Esse detalhe ajuda a reforçar uma ideia importante em redes:

```text
IP identifica origem e destino lógico da comunicação.
MAC é usado para entrega dentro do enlace local.
```

## Relação com redes e segurança defensiva

A análise de tráfego ICMP é útil em troubleshooting, redes, suporte técnico, NOC e SOC.

Mesmo sendo um teste simples, o `ping` ajuda a responder perguntas importantes:

```text
O host consegue alcançar o destino?
Existe resposta do destino?
O tráfego está saindo pela interface esperada?
O protocolo observado corresponde ao teste realizado?
```

Em segurança defensiva, entender ICMP ajuda a interpretar testes de conectividade, diagnosticar falhas de comunicação e reconhecer comportamentos básicos de rede. Esse tipo de base é importante antes de analisar tráfegos mais complexos.

## Observações importantes

Durante os testes iniciais, a VPN estava ativa e isso dificultou a visualização dos pacotes ICMP esperados na interface Wi-Fi.

A VPN foi desativada para a captura oficial, pois o tráfego poderia ser roteado por uma interface virtual, alterando o caminho dos pacotes e dificultando a análise.

Os prints utilizados na documentação foram anonimizados para ocultar informações sensíveis da rede local, como endereços MAC completos, nomes de dispositivos/fabricantes e partes do IP local.

## Aprendizados

Nesta análise, pratiquei:

* uso do Wireshark para capturar tráfego ICMP;
* aplicação de filtros de exibição;
* identificação de pacotes Echo Request e Echo Reply;
* leitura de informações básicas em IPv4 e ICMP;
* interpretação do campo TTL;
* diferença entre destino lógico em IP e entrega local em Ethernet;
* importância de controlar variáveis do ambiente, como o uso de VPN.

## Conclusão

A captura mostrou o funcionamento do comando `ping` na prática.

Foi possível observar pacotes ICMP Echo Request saindo do host local em direção ao endereço `8.8.8.8` e pacotes Echo Reply retornando do destino.

A análise confirmou conectividade IP com o destino externo e ajudou a reforçar conceitos fundamentais de redes, como ICMP, IPv4, TTL, endereço de origem, endereço de destino e comunicação em camadas.