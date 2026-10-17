# LAB-001 — Plan de direccionamiento

**Estado:** diseño físico en construcción. Solo se marcan como implementadas las redes ya configuradas.

## WAN simulada

| Dominio | Red | Gateway upstream | EDGE01 | EDGE02 | Estado |
|---|---|---:|---:|---:|---|
| ISP-A | 198.51.100.0/29 | 198.51.100.1 | 198.51.100.2 | 198.51.100.3 | Gateway configurado |
| ISP-B | 203.0.113.0/29 | 203.0.113.1 | 203.0.113.2 | 203.0.113.3 | Gateway configurado |

Las redes 198.51.100.0/24 y 203.0.113.0/24 pertenecen a TEST-NET y se utilizan únicamente para simulación/documentación.

## HQ — redes internas objetivo

| Función | VLAN | Red | Gateway lógico objetivo |
|---|---:|---|---|
| USERS | 10 | 10.50.10.0/24 | 10.50.10.1 |
| SERVERS | 20 | 10.50.20.0/24 | 10.50.20.1 |
| CCTV / IoT | 30 | 10.50.30.0/24 | 10.50.30.1 |
| GUEST | 40 | 10.50.40.0/24 | 10.50.40.1 |
| MANAGEMENT | 99 | 10.50.99.0/24 | 10.50.99.1 |

La ubicación definitiva de los gateways (Core L3, VRRP u otro mecanismo) se validará durante la fase de diseño del Cisco 3850 y la alta disponibilidad Edge.

## Branch

Se reserva 10.60.0.0/16 para redes de la sede simulada detrás del Cisco ISR 4451.

Ejemplo inicial:

- Branch Users: 10.60.10.0/24
- Branch Servers: 10.60.20.0/24
- Branch Management: 10.60.99.0/24

## Transit / infraestructura

Se reserva 10.255.0.0/16 para enlaces punto a punto, loopbacks, routing dinámico y servicios de infraestructura del laboratorio.

## Estado de validación

- ISP-A gateway 198.51.100.1/29 en RB4011 upstream: IMPLEMENTED.
- ISP-B gateway 203.0.113.1/29 en RB4011 upstream: IMPLEMENTED.
- RB5009 WAN distribution: NOT CONFIGURED.
- EDGE01 dual-WAN: NOT CONFIGURED.
- EDGE02 dual-WAN: NOT CONFIGURED.
- HQ VLANs: NOT CONFIGURED.
- Branch: NOT CONFIGURED.
