# LAB-001 — Arquitectura real y fases

**Plataforma:** GNS3 + MikroTik CHR RouterOS 7.23.7 long-term.

```mermaid
flowchart TB
 INET[INTERNET-SIM]
 ISP1[ISP01] --- INET
 ISP2[ISP02] --- INET
 ISP1 --- W1[SW-WAN1]
 ISP2 --- W2[SW-WAN2]
 W1 --- C1[CCR01]
 W1 --- C2[CCR02]
 W2 --- C1
 W2 --- C2
 C1 ---|HA/Transit 10.255.255.0/30| C2
 C1 --- CORE[SW-CORE]
 C2 --- CORE
 MG[ZN-SERVER-MGMT] --- SM[SW-MGMT]
 SM --- C1
 SM --- C2
 CORE --- U[VLAN10 USERS]
 CORE --- S[VLAN20 SERVERS]
 CORE --- I[VLAN30 CCTV/IoT]
 CORE --- M[VLAN99 INFRA-MGMT]
```

## Baseline confirmado
- CCR01 y CCR02: CHR, RouterOS 7.23.7 long-term, 512 MiB RAM.
- SW-CORE y SW-MGMT: CHR, RouterOS 7.23.7 long-term, 256 MiB RAM.
- SW-CORE: bridge1, vlan-filtering=no al inicio.
- SW-MGMT: bridge-MGMT, red OOB 10.50.250.0/24.
- Enlaces HA y OOB verificados con 0% de pérdida.

## Fases
1. Baseline e inventario — EN CURSO.
2. VLAN 10/20/30/99 y trunks CCR↔SW-CORE.
3. VRRP por VLAN.
4. Routing interno y OSPF área 0 donde aporte valor.
5. Dual WAN y failover.
6. Firewall y segmentación.
7. Observabilidad y fallos controlados.
8. Evidencia y cierre.
