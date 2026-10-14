# LAB-001 — Pruebas de aceptación

**Estado: NOT RUN**. Registrar PASS solo con evidencia.

| ID | Caso | Criterio | Estado |
|---|---|---|---|
| T-01 | Inventario | Versión, licencia, interfaces/MAC y recursos registrados | NOT RUN |
| T-02 | Gateways VLAN | Cada cliente alcanza gateway esperado | NOT RUN |
| T-03 | Aislamiento | VLAN10 no accede al plano de gestión | NOT RUN |
| T-04 | Administración | Solo orígenes autorizados en VLAN80 acceden | NOT RUN |
| T-05 | Flujo permitido | VLAN10 → servicio autorizado en VLAN20 funciona, resto bloqueado | NOT RUN |
| T-06 | WAN1 | Tráfico autorizado circula por ISP1 simulado | NOT RUN |
| T-07 | Falla WAN1 | Fase B: conmutación medida con evidencia | NOT RUN |
| T-08 | Recuperación | Fase B: retorno estable sin flapping | NOT RUN |
| T-09 | Observabilidad | Rutas, contadores y eventos registrados | NOT RUN |
| T-10 | Reinicio | Configuración y comportamiento persisten | NOT RUN |

Por prueba documentar fecha, versiones, comandos, equipo de origen, resultado PASS/FAIL/BLOCKED, evidencia sanitizada y medidas correctivas.

**Seguridad:** ejecutar solo en entorno autorizado y aislado; asegurar consola/rollback antes de firewall.
