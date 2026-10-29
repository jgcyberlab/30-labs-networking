# 30-day-networking
# 🌐 Cisco Packet Tracer — 30 Labs de Redes

Trilha prática e progressiva de **30 laboratórios** no Cisco Packet Tracer, do switching básico até um projeto final dual-stack (IPv4 + IPv6) com redundância, segurança de borda e serviços de gerência.

Cada lab é construído do zero (topologia, endereçamento e configuração), validado com testes e acompanhado de uma **falha controlada**: eu quebro algo de propósito, diagnostico, corrijo e explico a causa.

> **Autor:** João Gabriel Machado Fernandes · [@jgcyberlab](https://github.com/jgcyberlab)
> **Ferramenta:** Cisco Packet Tracer `<versão>` · **Foco:** roteamento, switching, segurança de rede e troubleshooting

---

## 📊 Progresso

![Progresso](https://img.shields.io/badge/labs_concluídos-10%2F30-blue)
![Write-ups](https://img.shields.io/badge/write--ups-6%2F30-green)

| Legenda | Significado |
|---|---|
| ✅ | Concluído, com `.pkt`, configurações e write-up |
| 🛠️ | Concluído, write-up em andamento |
| ⏳ | Pendente |

### Fundamentos de switching

| # | Lab | Tópicos principais | Status |
|---|---|---|---|
| 01 | [Switching e VLANs](LAB%201.md) | VLANs, portas de acesso, SVI de gerência, tabela MAC | ✅ |
| 02 | [VLANs e DHCP no roteador](LAB%202.md) | Router-on-a-Stick, 802.1Q, pools DHCP | ✅ |
| 03 | [Trunks entre switches](LAB%203.md) | Trunk 802.1Q, VLANs permitidas, VLAN nativa | ✅ |
| 04 | [DHCP Relay](LAB%204.md) | `ip helper-address`, servidor DHCP centralizado, DORA | ✅ |
| 05 | [Port Security](LAB%205.md) | MAC sticky, violação `shutdown`, recuperação de porta | ✅ |
| 06 | [STP e eleição da raiz](LAB%206.md) | Bridge ID, papéis de porta, reconvergência | ✅ |

### Roteamento IPv4

| # | Lab | Tópicos principais | Status |
|---|---|---|---|
| 07 | Rotas estáticas e caminho de retorno | Sub-redes, rotas estáticas, rota de retorno, default | 🛠️ |
| 08 | Rotas flutuantes e sumarização | Distância administrativa, backup, sumarização /23 | 🛠️ |
| 09 | OSPF de área única | OSPFv2, router-id, vizinhanças, DR/BDR | 🛠️ |
| 10 | OSPF multiárea | ABR, rotas O IA, LSDB, área stub | 🛠️ |
| 11 | OSPF: custo, autenticação e interfaces passivas | Custo, `passive-interface`, autenticação MD5 | ⏳ |

### Segurança e NAT

| # | Lab | Tópicos principais | Status |
|---|---|---|---|
| 12 | ACL padrão na administração por SSH | SSHv2, VTY, `access-class` | ⏳ |
| 13 | ACL estendida por serviço | ACL nomeada, filtragem por protocolo/porta | ⏳ |
| 14 | NAT estático | Tradução 1:1, inside/outside | ⏳ |
| 15 | NAT dinâmico e PAT em etapas | Pool NAT, overload | ⏳ |

### Switching avançado e redundância

| # | Lab | Tópicos principais | Status |
|---|---|---|---|
| 16 | Roteamento inter-VLAN por SVI | Switch L3, `ip routing` | ⏳ |
| 17 | Rapid PVST+, PortFast e BPDU Guard | Convergência rápida, proteção de borda | ⏳ |
| 18 | EtherChannel L2 | LACP/PAgP, agregação de enlaces | ⏳ |
| 19 | EtherChannel L3 | Port-channel roteado | ⏳ |

### IPv6

| # | Lab | Tópicos principais | Status |
|---|---|---|---|
| 20 | IPv6 e SLAAC | Endereçamento /64, autoconfiguração | ⏳ |
| 21 | Rotas estáticas IPv6 | Roteamento estático IPv6 | ⏳ |
| 22 | OSPFv3 para IPv6 | OSPFv3 | ⏳ |

### Alta disponibilidade e gerência

| # | Lab | Tópicos principais | Status |
|---|---|---|---|
| 23 | HSRP e gateway virtual | FHRP, gateway ativo/standby | ⏳ |
| 24 | FHRP comparativo e redundância por VLAN | Balanceamento de gateway por VLAN | ⏳ |
| 25 | NTP | Sincronização de horário | ⏳ |
| 26 | Syslog centralizado | Logging remoto, níveis de severidade | ⏳ |
| 27 | SNMP para monitoramento | Comunidades, consultas SNMP | ⏳ |

### Integração e projetos

| # | Lab | Tópicos principais | Status |
|---|---|---|---|
| 28 | Integração: segurança de borda | ACL + NAT + hardening | ⏳ |
| 29 | Projeto: rede multicamada redundante | Sede/filial, HSRP, EtherChannel, OSPF multiárea | ⏳ |
| 30 | Projeto final: consolidação dual-stack | IPv4 + IPv6, NTP/Syslog/SNMP, matriz de testes | ⏳ |

---

## 🧪 Metodologia

Todo lab segue o mesmo ciclo:

1. **Planejar** — desenho da topologia, tabela de endereçamento e cálculo de sub-redes antes de configurar.
2. **Construir** — configuração dos equipamentos.
5. **Diagnosticar e corrigir** — seguindo a ordem: enlace → VLAN/trunk → IP/máscara/gateway → rota de ida e volta → ACL/NAT → serviço.
6. **Documentar** — causa e correção explicadas com minhas palavras.

### Convenções de endereçamento

| Uso | Padrão |
|---|---|
| LANs | `192.168.<VLAN>.0/24` ou `172.16.<VLAN>.0/24`|
| Enlaces de trânsito IPv4 | `/30` exclusivo por enlace |
| IPv6 | `2001:db8::/32` subdividido em `/64` |
| Switch L2 / L3 | 2960 / 3560 (conforme necessidade) |

*Exceção: quando o enunciado do lab fixa redes específicas.*

---

## 📁 Estrutura do repositório

```
packet-tracer-labs/
├── README.md        # este arquivo
├── LAB 1.md         # write-ups (um arquivo por lab)
├── LAB 2.md
├── ...
├── LabPics/         # imagens usadas nos write-ups
└── PKT/             # arquivos .pkt do Packet Tracer
```

### Como abrir e ver os labs por si próprio

1. Instale o [Cisco Packet Tracer](https://www.netacad.com/cisco-packet-tracer) (gratuito, requer conta NetAcad).
2. Clone o repositório:
   ```bash
   git clone https://github.com/jgcyberlab/packet-tracer-labs.git
   ```
3. Abra o `.pkt` do lab desejado na pasta `PKT/` e acompanhe pelo write-up correspondente (`LAB N.md`).

---

## ⚠️ Limitações

- O Packet Tracer é um **simulador**: nem todos os comandos e recursos do IOS real estão disponíveis, e os resultados não validam desempenho nem prontidão para produção.
- Quando um recurso não existe na versão usada, o write-up registra o modelo, o comando tentado e a mensagem obtida, e a extensão fica marcada como **não executada**.

---

## 📬 Contato

- GitHub: [@jgcyberlab](https://github.com/jgcyberlab)
- LinkedIn: `www.linkedin.com/in/joaogabrielmachado-cyber`
