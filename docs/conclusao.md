# Conclusão

Este projeto teve como objetivo estudar protocolos e comportamentos de rede a partir de capturas reais feitas no Wireshark.

Ao longo das análises, observei diferentes partes da comunicação em rede: conectividade com ICMP, resolução de nomes com DNS, associação entre IP e MAC com ARP, estabelecimento de conexões TCP, comparação entre HTTP e HTTPS e obtenção automática de configuração IP com DHCP.

A proposta não foi apenas reunir prints, mas entender o que estava acontecendo em cada captura e relacionar essas observações com redes, troubleshooting, infraestrutura e segurança defensiva.

---

## Etapas realizadas

Durante o projeto, foram analisados os seguintes temas:

- ICMP/Ping;
- DNS/nslookup;
- ARP/Gateway;
- TCP Three-Way Handshake;
- HTTP vs HTTPS;
- DHCP.

Cada etapa mostrou uma parte importante da comunicação em rede. Quando vistas em conjunto, elas ajudam a entender melhor o caminho que um dispositivo percorre para conseguir se comunicar.

Antes de acessar um site, por exemplo, o host precisa ter uma configuração de rede válida, resolver nomes de domínio, comunicar-se com o gateway, estabelecer conexões e trocar dados com o servidor de destino.

---

## Principais aprendizados

Com o ICMP, foi possível observar pacotes de teste de conectividade, como Echo Request e Echo Reply.

Com o DNS, ficou mais claro como nomes de domínio são resolvidos para endereços IP e como esse processo é essencial para o acesso a sites e serviços.

Com o ARP, observei a relação entre endereços IP e endereços MAC dentro da rede local, reforçando a diferença entre comunicação lógica e entrega no enlace local.

Com o TCP Handshake, analisei a sequência `SYN`, `SYN, ACK` e `ACK`, usada para estabelecer uma conexão TCP antes da troca de dados.

Na comparação entre HTTP e HTTPS, a diferença ficou evidente: no HTTP, a requisição e a resposta aparecem em texto claro; no HTTPS, o conteúdo da aplicação fica protegido por TLS e aparece como dados criptografados.

Com o DHCP, observei como um host recebe automaticamente informações essenciais para participar da rede, como endereço IP, máscara de sub-rede, gateway, DNS e tempo de lease.

---

## Teoria e prática

Uma das partes mais importantes deste projeto foi perceber como a prática ajuda a consolidar a teoria.

Antes das capturas, muitos conceitos já eram conhecidos de forma teórica. Porém, ao observar esses protocolos funcionando no Wireshark, ficou muito mais fácil entender o papel de cada um na comunicação real.

Aplicar filtros, analisar campos, comparar pacotes e interpretar o comportamento observado tornou o aprendizado mais concreto.

Esse projeto reforçou que, para mim, estudar a base primeiro e depois aplicar em um laboratório prático é uma forma muito eficiente de aprender.

---

## Relação com troubleshooting

O projeto também ajudou a enxergar melhor como uma análise de rede pode ser usada para investigar problemas.

Em um cenário real, quando um dispositivo não consegue acessar um site ou serviço, é possível seguir uma linha de raciocínio como:

```text
O host recebeu IP corretamente via DHCP?
Ele consegue se comunicar com o gateway?
A resolução DNS está funcionando?
Existe conectividade com o destino?
A conexão TCP está sendo estabelecida?
O problema está na aplicação, no protocolo ou na criptografia?
```

Essa forma de pensar ajuda a separar possibilidades e evita conclusões precipitadas.

Em vez de apenas dizer que “a internet não funciona”, a análise permite investigar em qual etapa a comunicação pode estar falhando.

---

## Relação com segurança defensiva

Embora o foco principal do projeto tenha sido redes e troubleshooting, várias análises também se conectam com segurança defensiva.

Entender tráfego de rede ajuda a identificar comportamentos esperados e perceber quando algo foge do normal.

Algumas perguntas importantes que podem surgir em uma análise são:

```text
Quais hosts estão se comunicando?
Quais domínios estão sendo consultados?
Houve tentativa de conexão TCP?
O tráfego está em texto claro ou protegido por TLS?
Qual IP foi entregue ao host?
Qual DNS está sendo utilizado?
O comportamento observado faz sentido?
```

Esses conhecimentos são úteis para suporte técnico, infraestrutura, NOC, Blue Team e SOC, porque ajudam na interpretação de eventos, logs, alertas e problemas de conectividade.

---

## Considerações finais

Gostei bastante de desenvolver este projeto, principalmente porque ele transformou conceitos que antes estavam mais na teoria em algo visível e prático. Usar o Wireshark me ajudou a enxergar os protocolos funcionando de verdade, entender melhor o papel de cada um e perceber como eles se conectam dentro da comunicação em rede.

Esse projeto também reforçou (ainda mais) meu interesse por redes, infraestrutura e segurança defensiva. Além disso, mostrou que aprender a base com calma e depois aplicar em projetos práticos é um caminho que funciona bem para o meu desenvolvimento.

A partir daqui, pretendo continuar construindo projetos que conectem teoria e prática, aprofundando conhecimentos em Linux, logs, troubleshooting, infraestrutura e segurança defensiva.