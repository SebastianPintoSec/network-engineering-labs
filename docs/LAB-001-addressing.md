# LAB-001 — Plan IP real del laboratorio

**Estado:** baseline validado parcialmente en GNS3.

| Función | VLAN | Red | CCR01 | CCR02 | VIP/uso |
|---|---:|---|---|---|---|
| USERS | 10 | 10.50.10.0/24 | 10.50.10.2 | 10.50.10.3 | 10.50.10.1 VRRP |
| SERVERS | 20 | 10.50.20.0/24 | 10.50.20.2 | 10.50.20.3 | 10.50.20.1 VRRP |
| CCTV / IoT | 30 | 10.50.30.0/24 | 10.50.30.2 | 10.50.30.3 | 10.50.30.1 VRRP |
| INFRA-MGMT | 99 | 10.50.99.0/24 | 10.50.99.2 | 10.50.99.3 | 10.50.99.1 VRRP |
| OOB-MGMT | — | 10.50.250.0/24 | 10.50.250.11 | 10.50.250.12 | gestión fuera de banda |
| HA/Transit | — | 10.255.255.0/30 | 10.255.255.1 | 10.255.255.2 | enlace directo CCR↔CCR |
| ISP01 | — | 198.51.100.0/29 | 198.51.100.2 | 198.51.100.3 | TEST-NET-2 |
| ISP02 | — | 203.0.113.0/29 | 203.0.113.2 | 203.0.113.3 | TEST-NET-3 |

Las redes 198.51.100.0/24 y 203.0.113.0/24 son rangos reservados para documentación (TEST-NET), adecuados para simulación.

## Estado de validación
- HA/Transit CCR01↔CCR02: PASS, 0% pérdida.
- OOB-MGMT CCR01↔CCR02 vía SW-MGMT: PASS, 0% pérdida.
- VLAN 10/20/30/99: pendiente de implementación.
- VRRP: pendiente.
- WAN/failover: pendiente.
