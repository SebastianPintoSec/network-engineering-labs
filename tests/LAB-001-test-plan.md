# LAB-001 — Pruebas de aceptación

Registrar **PASS** únicamente con evidencia de ejecución física.

| ID | Caso | Criterio | Estado |
|---|---|---|---|
| T-01 | Inventario físico | Modelos, versiones, interfaces y roles registrados | IN PROGRESS |
| T-02 | ISP-A upstream | Gateway ISP-A operativo y alcanzable desde Edge | PARTIAL |
| T-03 | ISP-B upstream | Gateway ISP-B operativo y alcanzable desde Edge | PARTIAL |
| T-04 | Aislamiento WAN | ISP-A e ISP-B permanecen en dominios L2 separados | NOT RUN |
| T-05 | EDGE01 dual-WAN | RB4011 EDGE01 alcanza Internet por ambos ISP de forma independiente | NOT RUN |
| T-06 | EDGE02 dual-WAN | CCR1009 EDGE02 alcanza Internet por ambos ISP de forma independiente | NOT RUN |
| T-07 | Failover ISP | Caída de ISP preferido conmuta al ISP alternativo sin intervención manual | NOT RUN |
| T-08 | Failover Edge | Caída de EDGE01 permite continuidad mediante EDGE02 | NOT RUN |
| T-09 | Recuperación | Retorno de ISP/router no produce flapping ni pérdida sostenida | NOT RUN |
| T-10 | Core L3 | Cisco 3850 enruta las VLAN definidas según política | NOT RUN |
| T-11 | Segmentación | USERS/IoT/GUEST/MGMT respetan la matriz de acceso | NOT RUN |
| T-12 | WLAN | SSID U6 se mapean correctamente a VLANs | NOT RUN |
| T-13 | Branch isolation | Branch no alcanza HQ sin túnel/routing explícito | NOT RUN |
| T-14 | IPsec HQ↔Branch | Redes autorizadas se comunican por túnel cifrado | NOT RUN |
| T-15 | Observabilidad | Eventos, rutas, counters y fallas quedan registrados | NOT RUN |
| T-16 | Reinicio | Configuración y comportamiento sobreviven reboot controlado | NOT RUN |

## Matriz mínima de fallas

Las pruebas de resiliencia deberán incluir al menos:

- desconexión física ISP-A;
- desconexión física ISP-B;
- apagado de EDGE01;
- apagado de EDGE02;
- falla de un enlace WAN individual;
- recuperación y reconvergencia;
- pérdida del túnel Branch;
- validación de que una falla del laboratorio no afecta la red doméstica/upstream.

Por prueba documentar fecha, versiones, equipo de origen, resultado PASS/FAIL/BLOCKED, evidencia sanitizada, tiempos de convergencia y medidas correctivas.

**Seguridad:** ejecutar solo en entorno autorizado y aislado; preservar acceso de administración y rollback antes de introducir firewall, routing dinámico o cambios de alta disponibilidad.
