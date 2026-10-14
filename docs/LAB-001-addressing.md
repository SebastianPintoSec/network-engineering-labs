# LAB-001 — Plan IP de laboratorio

Los segmentos siguientes son **propuestos**, no pertenecen a clientes.

| Zona | VLAN | Subred | IP CHR | Uso |
|---|---:|---|---|---|
| Usuarios | 10 | 10.60.10.0/24 | 10.60.10.1 | Estaciones |
| Servicios | 20 | 10.60.20.0/24 | 10.60.20.1 | Servidores |
| Gestión | 80 | 10.60.80.0/24 | 10.60.80.1 | Administración |
| Tránsito WAN1 | — | 198.18.0.0/30 | 198.18.0.2 | ISP1 198.18.0.1 |
| Tránsito WAN2 | — | 198.18.0.4/30 | 198.18.0.6 | ISP2 198.18.0.5 |

**Nota:** 198.18.0.0/15 es un bloque de benchmarking (RFC 2544), no direccionamiento público de producción. Mantener ISP simulados aislados. LAN usa RFC1918.

## Política objetivo (pendiente de prueba)
- VLAN10 → VLAN80: denegar nuevas sesiones.
- VLAN80 → administración CHR: limitar a administradores y servicios autorizados.
- VLAN10 → VLAN20: permitir solo flujos definidos, bloquear otros.
- WAN → LAN: negar conexiones entrantes nuevas por defecto.
- NAT y salida WAN: habilitar solo cuando el diseño lo requiera.

Conservar consola para recuperación antes de aplicar reglas restrictivas.
