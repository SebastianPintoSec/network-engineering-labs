# Network Engineering Labs

Laboratorios reproducibles de ingeniería de redes centrados en **MikroTik RouterOS v7**, **GNS3** y Linux.

> **Estado actual: DESIGN / NOT VALIDATED.** La arquitectura aún no está implementada ni probada en GNS3.

## LAB-001 — Enterprise Network Architecture

Diseño de una red empresarial segmentada con VLAN 10 (usuarios), VLAN 20 (servicios), VLAN 80 (gestión), un CHR perimetral y dos ISP simulados. El primer hito es validar segmentación y firewall; el failover se incorpora después.

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

**Próximo paso:** verificar inventario real de GNS3 y CHR, mapear interfaces y ejecutar fase A.

**Licencia:** pendiente de definir; el acceso público no implica licencia de reutilización.
