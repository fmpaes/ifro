# Atividade 04 — Rede Hierárquica

Curso Superior de Tecnologia em Redes de Computadores — IFRO
Disciplina: Comutação de redes locais
Prazo de entrega: 27/08/2026

## Objetivo

Simular, no Cisco Packet Tracer, um ambiente de rede local com estrutura hierárquica de três camadas (núcleo, distribuição e borda), aplicando conceitos de escalabilidade, redundância e disponibilidade previstos nos padrões 802.3.

## Topologia

A rede foi montada com a seguinte estrutura:

- **Borda (Router):** 1x roteador (Cisco 1941) com 2 interfaces FastEthernet, cada uma conectada a um switch de núcleo diferente.
- **Núcleo:** 2x switches (Cisco 3650-24PS), conectados entre si por 4 links físicos GigabitEthernet em paralelo, preparados para uma futura agregação de link (EtherChannel) de 4 Gbps.
- **Distribuição:** 2x switches (Cisco 3650-24PS), conectados individualmente a cada switch de núcleo via fibra óptica. Cada uma das 4 conexões núcleo↔distribuição possui 2 links físicos de fibra em paralelo, preparados para uma futura agregação de 2 Gbps.
- **Borda (acesso):** 4x switches (Cisco 2960-24TT), cada um conectado a apenas um switch de distribuição, sem qualquer recurso de redundância.
- **Dispositivos finais:** 4 desktops, 4 notebooks e 1 servidor, todos conectados com fio aos switches de borda.

Nenhuma configuração lógica foi exigida nos equipamentos nesta etapa — apenas as ligações físicas foram realizadas, conforme o escopo da atividade.

## Configuração extra (endereçamento IP)

Como item opcional, foi configurado um esquema de IP estático nos dispositivos finais, todos na mesma sub-rede `192.168.10.0/24`, permitindo comunicação direta via ping entre eles (borda → distribuição → núcleo → distribuição → borda).

| Dispositivo | IP | Máscara |
|---|---|---|
| SRV-01 (servidor) | 192.168.10.10 | 255.255.255.0 |
| PC-01 a PC-04 | 192.168.10.21 – 192.168.10.24 | 255.255.255.0 |
| NB-01 a NB-04 | 192.168.10.41 – 192.168.10.44 | 255.255.255.0 |

Não foi necessário configurar gateway padrão, já que não há roteamento entre sub-redes nesta topologia.

## Arquivos desta pasta

- `topologia.pkt` — arquivo salvo do Cisco Packet Tracer com a topologia completa.
- `print-topologia.png` — captura de tela do diagrama da rede.
