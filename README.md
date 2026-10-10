# UC00631 — Planear e Instalar a Infraestrutura de Redes Locais

**Cisco Networking · Switching · Routing · Network Security**

![Cisco IOS](https://img.shields.io/badge/Cisco-IOS-1BA0D7) ![Packet Tracer](https://img.shields.io/badge/Labs-Packet%20Tracer-green) ![Network Security](https://img.shields.io/badge/Focus-Network%20Security-red) ![Language](https://img.shields.io/badge/Language-Portugu%C3%AAs-blue)

## Sobre o projeto

Este repositório apresenta o manual de estudo e os exercícios práticos da **UC00631 — Planear e Instalar a Infraestrutura de Redes Locais**, no âmbito da formação **Técnico/a Especialista em Cibersegurança (nível 5)**, no CINEL.

O manual reúne **195 páginas** com fundamentos, configurações Cisco IOS, topologias simuladas, capturas de ecrã, comandos de verificação e exercícios de diagnóstico. Os cenários são educativos e não representam uma implementação de produção.

## Conteúdos

| Módulo | Tema |
| --- | --- |
| 01 | Fundamentos de Cisco IOS e configuração inicial de routers e switches |
| 02 | Endereçamento IPv4, DHCP, DHCP Relay e encaminhamento |
| 03 | VLANs, portas access, trunks e segmentação |
| 04 | Inter-VLAN Routing e Router-on-a-Stick |
| 05 | Switching de camada 3, SVIs e rotas estáticas |
| 06 | Topologias práticas, VTP e testes de conectividade |
| 07 | VTP, STP e EtherChannel (PAgP e LACP) |
| 08 | Segurança de camada 2: Port Security, DHCP Snooping e Dynamic ARP Inspection |
| 09 | Preparação prática para avaliação — laboratório de 22/09/2026 |

## Tecnologias e conceitos

`Cisco IOS` · `Cisco Packet Tracer` · `IPv4` · `VLAN` · `802.1Q` · `SSH` · `DHCP` · `DHCP Relay` · `DNS` · `VTP` · `STP` · `EtherChannel` · `PAgP` · `LACP` · `SVI` · `Inter-VLAN Routing` · `Port Security` · `DHCP Snooping` · `Dynamic ARP Inspection`

## Exemplos de configuração

### VLANs e trunk 802.1Q

```cisco
configure terminal
vlan 10
 name ESTUDANTES
vlan 20
 name PROFESSORES
vlan 30
 name DIRECAO
interface fastEthernet0/24
 switchport mode trunk
 switchport trunk native vlan 40
 switchport trunk allowed vlan 10,20,30,40
 switchport nonegotiate
```

### Router-on-a-Stick

```cisco
interface gigabitEthernet0/0
 no shutdown
interface gigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0
interface gigabitEthernet0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0
```

### DHCP Snooping e Dynamic ARP Inspection

```cisco
ip dhcp snooping
ip dhcp snooping vlan 10
ip arp inspection vlan 10
interface gigabitEthernet0/1
 ip dhcp snooping trust
 ip arp inspection trust
interface fastEthernet0/10
 ip dhcp snooping limit rate 15
```

> **Atenção:** exemplos adaptados de diferentes exercícios do manual. Interfaces, VLANs, endereços e comandos devem ser ajustados à topologia e à plataforma Cisco utilizada. Apenas interfaces efetivamente fidedignas devem receber `trust`.

## Verificação e diagnóstico

```cisco
show running-config
show ip interface brief
show ip route
show vlan brief
show interfaces trunk
show vtp status
show spanning-tree
show etherchannel summary
show ip dhcp snooping
show ip dhcp snooping binding
show ip arp inspection interfaces
```

Os exercícios incluem testes de `ping`, atribuição de endereços por DHCP, resolução DNS e acesso remoto por SSH. **No exercício final, foi registada uma falha de conectividade na VLAN 30; a causa não ficou demonstrada no material original.** Este resultado deve ser tratado como um ponto de diagnóstico, não como um teste concluído com sucesso.

## Manual completo

📄 [Consultar o manual UC00631 (PDF)](docs/UC00631_Manual_Profissional_Reformatado.pdf)

Para que a ligação funcione, coloca o PDF na pasta `docs/` com o nome indicado acima.

## Estrutura sugerida

```text
Cisco-Networking-and-Network-Security-Labs/
├── README.md
└── docs/
    └── UC00631_Manual_Profissional_Reformatado.pdf
```

## Contexto académico

- **Instituição:** CINEL — Centro de Formação Profissional da Indústria Electrónica, Energia, Telecomunicações e Tecnologias da Informação
- **Curso:** Técnico/a Especialista em Cibersegurança
- **Nível:** 5
- **Unidade:** UC00631 — Planear e Instalar a Infraestrutura de Redes Locais
- **Ano da edição do manual:** 2026

## Autor

**Pedro Gonçalves** — Redes Informáticas, Cibersegurança e Segurança de Infraestruturas.

## Utilização responsável

Este repositório destina-se a estudo e demonstração de competências em ambientes próprios ou autorizados. Alguns exemplos do material original utilizam credenciais simples para fins didáticos; **não devem ser reutilizadas em redes reais**. Antes de aplicar qualquer configuração em produção, revê a compatibilidade, os privilégios e as políticas de segurança.
