Sistema de Registro y Gestión de Baches
Bahía Blanca

1. Introducción
La ciudad de Bahía Blanca enfrenta problemas recurrentes relacionados con baches en la vía pública. Para mejorar la eficiencia en la reparación y el seguimiento de estos casos, se propone el desarrollo de un sistema que permita registrar, administrar y priorizar los reportes de baches realizados por los ciudadanos.

2. Objetivo del sistema
Diseñar un Sistema que permita:
. Registrar los datos de los usuarios que reportan baches, para asegurar el seguimiento de los casos y evitar duplicados.
. Registrar reportes ciudadanos sobre baches.
. Clasificarlos por nivel de gravedad y ubicación.
. Evitar duplicación de reportes.
. Asignar supervisores e inspectores según la prioridad.
. Llevar seguimiento técnico y presupuestario de cada intervención.

3. Usuarios del sistema
. Administradores / Personal municipal: gestionan los reportes, asignan cuadrillas, verifican datos, supervisan los trabajos.
. Ciudadanos / Usuarios externos: reportan baches con evidencia (foto, video) e información básica del lugar.

4. Datos que gestiona el sistema
. Ubicación del bache: barrio, calle, coordenadas aproximadas.
. IP del dispositivo o identificación del usuario (para evitar duplicados).
. Tipo de calle: asfalto, tierra, empedrada, etc
. Tipo de rotura: grieta superficial, pozo profundo, desmoronamiento, hundimiento, etc.
. Escala de gravedad del bache (1 a 10), según evidencia y cantidad de reportes.
. Evidencia: fotos, videos.
. Reportes relacionados (múltiples reclamos sobre la misma zona).
. Estado del bache: registrado, en evaluación, en reparación, resuelto.
. Daños a vehículos u objetos, si los hubo, con su respectiva documentación.
. Materiales necesarios para la reparación y presupuesto estimado.
. Tiempo desde el primer reporte.

5. Funcionalidades principales
. Registro de nuevos reportes con validación por IP o usuario.
. Asignación de prioridad en base a evidencia y volumen de reportes.
. Notificar al usuario cuando su reporte fue enviado exitosamente, y en caso de detectar un reporte previo del mismo usuario, informarle que ya existe un caso abierto asociado.
. Detectar si ya existe un caso abierto en la misma zona y notificar al usuario antes de    permitir   un nuevo reporte, para evitar duplicaciones innecesarias.
. Generación de estadísticas y reportes por zona.
. Asignación automática de supervisores cuando hay alta actividad en una misma área.
. Registro y seguimiento de costos, materiales y tiempo de obra.

6. Prevención de duplicados y abusos
El sistema implementará mecanismos para evitar reportes duplicados, como:
. Verificación por dirección e IP.
. Registro de usuarios frecuentes.
. Notificación al ciudadano si ya existe un caso abierto en esa zona.
. Limitación de múltiples reportes por día desde un mismo origen.

7. Técnicas utilizadas para el relevamiento de requerimientos
. Observación directa de zonas afectadas.
. Entrevistas a ciudadanos y empleados municipales.
. Revisión de reportes previos o sistemas similares.
. Prototipos conceptuales del sistema.
. Análisis de patrones de reclamos según barrio.
8. Consideraciones adicionales
. En caso de reclamos por daños, el sistema permitirá subir documentación de respaldo, aunque el tratamiento legal dependerá del municipio.
. La priorización automática considera tanto la gravedad técnica como la cantidad de reportes.
. Las zonas con múltiples baches serán agrupadas para evaluar intervenciones integrales.
