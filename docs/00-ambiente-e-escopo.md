# 00 - Ambiente e Escopo do Projeto

## Objetivo

Este documento apresenta o ambiente utilizado, o escopo do projeto e os cuidados adotados durante as análises de tráfego de rede.

A ideia deste projeto é praticar análise de pacotes no Wireshark a partir de capturas simples e controladas, observando protocolos fundamentais de redes e relacionando cada análise com troubleshooting e segurança defensiva.

Este arquivo serve como ponto de partida para deixar claro onde as capturas foram feitas, quais limites foram definidos e quais cuidados de privacidade serão seguidos ao longo do projeto.

## Ambiente utilizado

O ambiente principal utilizado nas análises é:

- Sistema operacional: Windows
- Ferramenta principal: Wireshark
- Interface de captura: Wi-Fi
- Rede utilizada: rede doméstica própria/autorizada
- Terminal utilizado: Windows PowerShell (x86)
- Navegador utilizado: navegador web local
- VPN: desativada durante capturas básicas, quando necessário

A VPN foi mantida desligada nas capturas iniciais porque ela pode alterar o caminho do tráfego, usar interfaces virtuais ou encapsular pacotes, dificultando a visualização do comportamento esperado na interface Wi-Fi.

Em etapas futuras, também poderá ser utilizado um ambiente com máquina virtual Linux para testes mais controlados.

## Protocolos e temas analisados

Neste projeto, serão analisados:

- ICMP / Ping
- DNS / nslookup
- ARP
- TCP Handshake
- HTTP e HTTPS
- DHCP

A ordem das análises foi pensada para começar pelos fundamentos de conectividade e, aos poucos, avançar para comportamentos mais detalhados de comunicação em rede.

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

O foco não é apenas capturar pacotes, mas entender o que eles mostram e como esse tipo de análise pode ajudar na investigação de problemas de rede.

## Fora do escopo

Este projeto não tem como objetivo:

- realizar ataques;
- explorar vulnerabilidades;
- executar testes em redes de terceiros;
- capturar tráfego de pessoas sem autorização;
- publicar capturas brutas contendo dados sensíveis;
- realizar varreduras ofensivas em ambientes públicos.

Todas as capturas serão feitas em ambiente próprio ou autorizado, com foco em aprendizado, troubleshooting e segurança defensiva.

## Cuidados de privacidade

Arquivos de captura brutos, como `.pcap` e `.pcapng`, não serão publicados no repositório.

Esses arquivos serão armazenados apenas localmente na pasta `captures-local/`, que está configurada no `.gitignore`.

Quando necessário, informações como endereços MAC, IPs locais, nomes de dispositivos e outros identificadores serão parcialmente ocultadas nos prints e na documentação.

A intenção é manter o valor técnico das evidências sem expor detalhes desnecessários da rede utilizada.

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

Esse padrão ajuda a manter as análises organizadas e facilita a leitura de cada etapa do projeto.

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
```

Essas perguntas ajudam a transformar a captura em análise, evitando que o projeto seja apenas uma coleção de prints.

## Relação com segurança defensiva

A análise de tráfego é uma habilidade importante para áreas como suporte técnico, redes, NOC, Blue Team e SOC.

Mesmo em capturas simples, como ICMP, DNS e ARP, já é possível praticar raciocínio investigativo: entender quem está se comunicando, qual protocolo está sendo usado, se houve resposta e se o comportamento observado faz sentido.

Esse tipo de base é importante para troubleshooting, investigação de incidentes, análise de alertas e compreensão do comportamento normal de uma rede.