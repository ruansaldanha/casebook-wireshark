# Casebook Wireshark: Análise e Diagnóstico de Tráfego de Rede

## Sobre o projeto

Este repositório reúne análises práticas de tráfego de rede utilizando o Wireshark.

A proposta é observar protocolos fundamentais na prática, interpretar os pacotes capturados e relacionar cada análise com conceitos de redes, troubleshooting e segurança defensiva.

O projeto faz parte do meu processo de estudo e construção de portfólio em tecnologia, com foco em redes, suporte técnico, infraestrutura e Blue Team/SOC.

## Status

Projeto em andamento.

Até o momento, foram documentadas análises de ICMP/Ping, DNS/nslookup, ARP/Gateway, TCP Handshake, HTTP vs HTTPS, DHCP. As próximas etapas serão adicionadas conforme novas capturas forem realizadas e analisadas.

## Objetivos

- Identificar pacotes ICMP Echo Request e Echo Reply.
- Analisar consultas e respostas DNS.
- Observar o funcionamento do ARP em uma rede local.
- Entender a relação entre IP, MAC e gateway.
- Identificar o TCP Three-Way Handshake.
- Comparar diferenças entre tráfego HTTP e HTTPS.
- Observar o funcionamento básico do DHCP.
- Aplicar filtros de exibição no Wireshark.
- Documentar evidências técnicas com prints e explicações.
- Relacionar as capturas com troubleshooting e segurança defensiva.

## Estudos documentados

| Parte | Tema | Status |
|---|---|---|
| 00 | Ambiente e escopo do projeto | Concluído |
| 01 | ICMP / Ping | Concluído |
| 02 | DNS / nslookup | Concluído |
| 03 | ARP / Gateway | Concluído |
| 04 | TCP Handshake | Concluído |
| 05 | HTTP vs HTTPS | Concluído |
| 06 | DHCP | Concluído |
| 07 | Conclusão geral | Pendente |

## Metodologia

Em cada análise, procuro seguir uma estrutura simples:

1. Definir o objetivo da captura.
2. Gerar tráfego de rede de forma controlada.
3. Capturar os pacotes no Wireshark.
4. Aplicar filtros de exibição.
5. Identificar origem, destino, protocolo e informações relevantes.
6. Registrar evidências com prints.
7. Explicar o comportamento observado.
8. Relacionar a análise com redes, troubleshooting e segurança defensiva.
9. Registrar observações importantes e aprendizados.

A ideia não é apenas mostrar prints do Wireshark, mas explicar o que está acontecendo em cada captura e por que aquilo é relevante em um contexto real de redes e suporte.

## Ambiente utilizado

O ambiente principal utilizado neste projeto é:

- Sistema operacional: Windows
- Ferramenta principal: Wireshark
- Terminal: Windows PowerShell (x86)
- Interface de captura: Wi-Fi
- Rede: rede doméstica própria/autorizada

Em etapas futuras, também poderá ser utilizado um ambiente com máquina virtual Linux para testes mais controlados.

## Ferramentas utilizadas

- Wireshark
- Windows
- Windows PowerShell (x86)
- Navegador web
- Rede doméstica autorizada

## Estrutura do repositório

```text
casebook-wireshark/
├── docs/
│   ├── 00-ambiente-e-escopo.md
│   ├── 01-icmp-ping.md
│   ├── 02-dns-nslookup.md
│   ├── 03-arp-gateway.md
│   ├── 04-tcp-handshake.md
│   ├── 05-http-vs-https.md
│   ├── 06-dhcp.md
│   └── conclusao.md
├── images/
│   ├── 01-icmp/
│   ├── 02-dns/
│   ├── 03-arp/
│   ├── 04-tcp/
│   ├── 05-http-https/
│   └── 06-dhcp/
├── notes/
│   └── comandos-usados.md
├── captures-local/
├── .gitignore
└── README.md
```

A pasta `captures-local/` é usada apenas localmente para armazenar arquivos de captura brutos, como `.pcap` e `.pcapng`. Esses arquivos não são publicados no GitHub.

## Cuidados de privacidade

Arquivos de captura brutos, como `.pcap` e `.pcapng`, não serão publicados neste repositório, pois podem conter informações sensíveis da rede local. Esses arquivos ficam armazenados apenas localmente na pasta `captures-local/`, que está configurada no `.gitignore`.

Nos documentos publicados, serão usados apenas prints selecionados, com informações sensíveis parcialmente ocultadas quando necessário, como endereços MAC completos, IPs locais e nomes de dispositivos.

## Relação com segurança defensiva

A análise de tráfego de rede é uma habilidade importante para áreas como suporte técnico, redes, NOC, Blue Team e SOC.

Mesmo em capturas simples, como ICMP, DNS e ARP, já é possível praticar perguntas importantes:

```text
Quem está se comunicando?
Qual protocolo está sendo usado?
Qual porta aparece na comunicação?
O DNS está funcionando?
Houve resposta do destino?
Qual IP está associado a qual MAC?
O comportamento observado faz sentido?
```

Essas perguntas são úteis em troubleshooting, investigação de incidentes, análise de alertas e compreensão do comportamento normal de uma rede.

## Próximos passos

- Registrar os principais aprendizados do projeto.