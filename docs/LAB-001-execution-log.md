# LAB-001 — Bitácora de ejecución

## 2026-10-16 — Baseline

| Componente | Resultado |
|---|---|
| CCR01 | RouterOS 7.23.7 long-term, 512 MiB |
| CCR02 | RouterOS 7.23.7 long-term, 512 MiB |
| SW-CORE | RouterOS 7.23.7 long-term, 256 MiB |
| SW-MGMT | RouterOS 7.23.7 long-term, 256 MiB |
| HA/Transit | PASS — CCR01↔CCR02, 0% pérdida |
| OOB-MGMT | PASS — CCR01↔CCR02 vía SW-MGMT, 0% pérdida |
| SW-CORE VLAN filtering | Deshabilitado; VLANs aún no implementadas |
| VLAN interfaces CCR | Ninguna al inicio |

### Direcciones existentes
CCR01: WAN1 198.51.100.2/29, WAN2 203.0.113.2/29, HA 10.255.255.1/30, OOB 10.50.250.11/24.

CCR02: WAN1 198.51.100.3/29, WAN2 203.0.113.3/29, HA 10.255.255.2/30, OOB 10.50.250.12/24.

### Observaciones
Los reinicios previos sin apagado correcto aparecen en logs de RouterOS, pero no afectan las pruebas de conectividad del baseline. La siguiente etapa es VLAN/trunking en SW-CORE y subinterfaces VLAN en ambos CCR.
