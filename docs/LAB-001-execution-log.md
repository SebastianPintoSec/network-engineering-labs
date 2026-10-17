# LAB-001 — Bitácora de ejecución

## 2026-10-16 — Cambio de arquitectura: GNS3 → laboratorio físico

Se decidió utilizar la topología física multivendor como implementación principal de LAB-001. GNS3 se conserva como sandbox/twin para diseño, reproducción de fallas y pruebas rápidas.

### Inventario físico confirmado

| Equipo | Rol previsto |
|---|---|
| MikroTik RB4011 #1 | Upstream real / ISP simulator |
| MikroTik RB5009 | WAN distribution |
| MikroTik RB4011 #2 | EDGE01 |
| MikroTik CCR1009 | EDGE02 |
| Cisco Catalyst 3850 | Core / Distribution |
| Ubiquiti Pro Switch | Access |
| Ubiquiti U6 | WLAN |
| Cisco ISR 4451 | Branch |

### RB4011 upstream — baseline

Se revisó la configuración existente y se determinó que debe tratarse como infraestructura protegida: no modificar WAN actual, LAN principal, DHCP, NAT base, VLAN80 ni la política de firewall existente salvo objetos aditivos requeridos para LAB-001.

Configuración relevante observada:

- WAN real por wan-bridge, DHCP desde el router/ONT upstream.
- LAN principal 192.168.88.0/24.
- VLAN80 existente 192.168.80.0/24.
- Política de firewall con default drop.
- NAT masquerade hacia la lista WAN.
- ether7 y ether8 estaban disponibles físicamente pero pertenecían a bridge-lan.

### Cambios ejecutados

1. ether7 y ether8 fueron removidos de bridge-lan.
2. ether7 fue renombrado a ISP-A-LAB.
3. Se configuró 198.51.100.1/29 en ISP-A-LAB.
4. ether8 fue renombrado a ISP-B-LAB.
5. Se configuró 203.0.113.1/29 en ISP-B-LAB.

Estado verificado mediante `/ip address print`:

- ISP-A-LAB — 198.51.100.1/29.
- ISP-B-LAB — 203.0.113.1/29.

### Decisión de alta disponibilidad

Se adopta inicialmente una arquitectura **active-passive** en la capa Edge:

- RB4011 EDGE01 será el router preferido/activo.
- CCR1009 EDGE02 será el router secundario.
- Ambos routers recibirán ISP-A e ISP-B.
- Una falla de proveedor no requiere necesariamente cambiar de router.
- Una falla del router activo permitirá que EDGE02 asuma conservando ambos proveedores.

### Próximo hito

Configurar RB5009 como distribuidor WAN manteniendo dos dominios L2 aislados:

- ISP-A: entrada upstream + salida hacia EDGE01 + salida hacia EDGE02.
- ISP-B: entrada upstream + salida hacia EDGE01 + salida hacia EDGE02.

No se considera validado ningún failover hasta ejecutar pruebas físicas con evidencia.

---

## 2026-10-16 — Baseline histórico GNS3 / OOB Management

La maqueta GNS3 previa logró validar conectividad HA/OOB, acceso WinBox remoto por Tailscale y persistencia del TAP de management tras reboot. Estos resultados se conservan como evidencia histórica del sandbox, pero no sustituyen las pruebas de la implementación física.
