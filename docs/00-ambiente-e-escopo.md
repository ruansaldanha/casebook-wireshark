# 00 - Ambiente e Escopo do Projeto

## Objetivo

Este documento descreve o ambiente utilizado, o escopo do projeto e os cuidados adotados durante as análises de tráfego de rede.

O projeto tem como objetivo documentar capturas práticas no Wireshark, observando protocolos fundamentais de redes e relacionando cada análise com troubleshooting e segurança defensiva.

## Ambiente utilizado

- Sistema operacional: Windows
- Ferramenta principal: Wireshark
- Interface de captura: Wi-Fi
- Rede utilizada: rede doméstica própria/autorizada
- Terminal utilizado: Windows PowerShell (x86)
- Navegador utilizado: navegador web local
- VPN: desativada durante capturas básicas, quando necessário

Em etapas futuras, poderá ser utilizado um ambiente com máquina virtual Linux para testes mais controlados.

## Protocolos e temas analisados

Neste projeto, serão analisados:

- ICMP / Ping
- DNS / nslookup
- ARP
- TCP Handshake
- HTTP e HTTPS
- DHCP

## Escopo

Este projeto analisará tráfego gerado em ambiente próprio, com foco educacional e defensivo.

As análises terão como foco:

- identificação de origem e destino;
- observação de protocolos;
- uso de filtros no Wireshark;
- interpretação básica de pacotes;
- relação com conceitos de redes;
- aplicação em troubleshooting e segurança defensiva;
- registro de evidências técnicas;
- registro de aprendizados e observações relevantes.

## Fora do escopo

Este projeto não tem como objetivo:

- realizar ataques;
- explorar vulnerabilidades;
- executar testes em redes de terceiros;
- capturar tráfego de pessoas sem autorização;
- publicar capturas brutas contendo dados sensíveis;
- realizar varreduras ofensivas em ambientes públicos.

## Cuidados de privacidade

Arquivos de captura brutos, como `.pcap` e `.pcapng`, não serão publicados no repositório.

Esses arquivos serão armazenados apenas localmente na pasta `captures-local/`, que está configurada no `.gitignore`.

Quando necessário, informações como endereços MAC, IPs locais, nomes de dispositivos e outros identificadores poderão ser parcialmente ocultadas nos prints e na documentação.

## Padrão de análise

Cada estudo seguirá, sempre que possível, o seguinte padrão:

1. Objetivo da captura.
2. Ambiente utilizado.
3. Comando ou ação utilizada para gerar tráfego.
4. Filtro aplicado no Wireshark.
5. Evidências salvas.
6. Pacotes observados.
7. Análise do comportamento.
8. Relação com redes e segurança defensiva.
9. Observações importantes.
10. Aprendizados.
11. Conclusão.

## Perguntas-guia

Durante as análises, o foco será responder perguntas como:

```text
Quem está se comunicando?
Qual é o endereço de origem?
Qual é o endereço de destino?
Qual protocolo está sendo usado?
Existe resposta do destino?
O comportamento observado é esperado?
Como isso se relaciona com troubleshooting ou segurança defensiva?
O que foi aprendido com essa captura?