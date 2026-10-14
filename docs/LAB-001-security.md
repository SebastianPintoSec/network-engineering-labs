# LAB-001 — Seguridad y alcance

**Activos:** CHR, dispositivos simulados, servicios de prueba, redes de gestión y host GNS3.

## Riesgos
- Exposición accidental de WinBox/SSH en WAN.
- Contaminación entre redes simuladas y redes reales del operador.
- Bloqueo del único acceso administrativo por cambios de firewall.
- Filtración de secretos, identificadores o configuraciones de clientes.
- Failover falsamente asumido como probado.

## Controles
1. Aislar el entorno y verificar consola.
2. Nunca almacenar claves ni contraseñas reales en Git.
3. Restringir administración a VLAN80 y orígenes autorizados.
4. Revisar/sanitizar exports y evidencias antes de subirlos.
5. Documentar mecanismo de rollback y repetir pruebas tras cambios.

Laboratorio de entrenamiento autorizado; no certifica comportamiento de equipos físicos ni cumplimiento normativo.
