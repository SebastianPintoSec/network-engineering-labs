# Network Engineering Labs

Laboratorios reproducibles de ingeniería de redes con foco en **MikroTik RouterOS v7, Cisco IOS/IOS-XE, Ubiquiti, alta disponibilidad, routing, switching, Wi-Fi y seguridad**.

> **Estado actual: PHYSICAL LAB / BUILD IN PROGRESS.**  
> LAB-001 migró desde una maqueta GNS3 a una implementación física multivendor. El entorno virtual se conserva como sandbox/twin para diseño y pruebas rápidas.


## LAB-001 — Enterprise Physical Network Architecture

Laboratorio empresarial físico orientado a validar una arquitectura **dual-ISP + dual-edge + core/distribution + access + WLAN + branch**.

### Inventario principal

- MikroTik RB4011 #1 — upstream real / ISP simulator.
- MikroTik RB5009 — distribución de los dominios WAN simulados.
- MikroTik RB4011 #2 — edge router 01.
- MikroTik CCR1009 — edge router 02.
- Cisco Catalyst 3850 — core/distribution.
- Ubiquiti Pro Switch — access layer.
- Ubiquiti U6 — WLAN.
- Cisco ISR 4451 — branch router.
- Clientes/servidores físicos para validación.

### Objetivo de alta disponibilidad

Los dos routers Edge tendrán acceso a **ISP-A e ISP-B**. La primera implementación utilizará un modelo **activo-pasivo**:

- RB4011 EDGE01: router preferido.
- CCR1009 EDGE02: router de respaldo.
- Si falla un ISP, el router activo puede continuar por el otro.
- Si falla el router activo, el router secundario conserva acceso a ambos ISP.

Una fase posterior podrá comparar este diseño con active-active.

### Documentación

- [Arquitectura y fases](docs/LAB-001-architecture.md)
- [Plan IP](docs/LAB-001-addressing.md)
- [Seguridad](docs/LAB-001-security.md)
- [Pruebas de aceptación](tests/LAB-001-test-plan.md)
- [Bitácora de implementación](docs/LAB-001-execution-log.md)
- [Configuraciones](configs/README.md)
- [Diagramas](diagrams/README.md)

## Reglas de publicación

No publicar credenciales, direcciones de clientes, respaldos binarios, secretos ni configuraciones operativas reales. Documentar versiones, prerequisitos, pruebas, evidencias y limitaciones. No afirmar resultados sin ejecutarlos.

**Próximo paso:** implementar la distribución física WAN en RB5009 y validar ISP-A/ISP-B hacia ambos routers Edge.

**Licencia:** pendiente de definir; el acceso público no implica licencia de reutilización.
