# Documentación del Proyecto

## Fundamentos de Seguridad y Auditoría

### 1. El estándar Syslog y su funcionamiento
El sistema de registro Syslog clasifica los eventos del sistema operativo cruzando dos dimensiones principales: la "Facilidad", que indica el subsistema de origen (como `auth` para autenticación o `cron` para tareas programadas), y la "Prioridad", que determina el nivel de criticidad del evento, desde mensajes de depuración (`debug`) hasta emergencias absolutas (`emerg`).

**Privacidad de los registros de autenticación:**
Mantener permisos de lectura públicos en archivos como `/var/log/auth.log` constituye una vulnerabilidad crítica ya que este archivo registra información sensible y su exposición permite a usuarios malintencionados mapear la infraestructura, identificar usuarios legítimos e interceptar credenciales introducidas erróneamente.

**Trazabilidad de conexiones:**
Al auditar los logs, un intento de acceso mediante SSH se distingue de uno local principalmente por la presencia de información de red. Mientras un fallo local registra la terminal física (`tty`), un fallo SSH registra el proceso `sshd` junto con la dirección IP de origen y el puerto, lo cual es vital para rastrear ataques de fuerza bruta externos.

### 2. Gestión Centralizada de Logs y Cumplimiento Normativo
La implementación de un sistema de *Log Management* centralizado es un pilar fundamental tanto para la ciberseguridad como para el cumplimiento normativo. A nivel técnico, extraer los logs de la máquina de producción y enviarlos a un servidor externo seguro garantiza su integridad; si la máquina es comprometida, el atacante no podrá eliminar la evidencia forense.

A nivel legal, en el marco del Reglamento General de Protección de Datos (RGPD) en España, esta práctica garantiza la trazabilidad y la responsabilidad proactiva. En caso de un incidente de seguridad, disponer de logs centralizados, inmutables y de alta disponibilidad permite realizar una auditoría forense rápida y precisa, requisito indispensable para notificar adecuadamente la brecha de seguridad a las autoridades competentes en los plazos legales establecidos.

## Referencias
A. A. Anton, P. Csereoka, E. A. Capota y R.-D. Cioargă, "Enhancing Syslog Message Security and Reliability over Unidirectional Fiber Optics", Sensors, vol. 24, no. 20, p. 6537, oct. 2024. [En línea]. Disponible: https://www.semanticscholar.org/reader/44f5072157858d0060f20c782506ca2e8553f8c2
