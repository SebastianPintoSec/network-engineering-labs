# LAB-001 — Bitácora de ejecución

## 2026-10-16 — Baseline y OOB Management

| Componente | Resultado |
|---|---|
| CCR01 | RouterOS 7.23.7 long-term, 512 MiB |
| CCR02 | RouterOS 7.23.7 long-term, 512 MiB |
| SW-CORE | RouterOS 7.23.7 long-term, 256 MiB |
| SW-MGMT | RouterOS 7.23.7 long-term, 256 MiB |
| HA/Transit | PASS — CCR01↔CCR02, 0% pérdida |
| OOB-MGMT | PASS — CCR01↔CCR02 vía SW-MGMT, 0% pérdida |
| TAP management | PASS — tap-gns3-mgmt 10.50.250.1/24 |
| Persistencia post-reboot | PASS — TAP, IP y ruta reaparecen automáticamente |
| Tailscale subnet route | PASS — 10.50.250.0/24 anunciada por zn-server |
| WinBox CCR01 | PASS — 10.50.250.11:8291 |
| WinBox CCR02 | PASS — 10.50.250.12:8291 |
| SW-CORE VLAN filtering | Deshabilitado; VLANs aún no implementadas |

### Direcciones existentes
CCR01: WAN1 198.51.100.2/29, WAN2 203.0.113.2/29, HA 10.255.255.1/30, OOB 10.50.250.11/24.

CCR02: WAN1 198.51.100.3/29, WAN2 203.0.113.3/29, HA 10.255.255.2/30, OOB 10.50.250.12/24.

SW-MGMT: 10.50.250.31/24.

ZN Server TAP: 10.50.250.1/24.

### Validación post-reboot
Tras reiniciar zn-server, el servicio systemd dedicado recreó el TAP, aplicó 10.50.250.1/24 y dejó disponible la ruta local 10.50.250.0/24. El TAP quedó sin carrier hasta iniciar el laboratorio GNS3; una vez activo el enlace, recuperó conectividad hacia SW-MGMT y ambos CCR. Desde el Mac se validaron ICMP y TCP/8291 por Tailscale.

### Siguiente etapa
Implementar VLAN 10/20/30/99 y trunks entre CCR01/CCR02 y SW-CORE.
