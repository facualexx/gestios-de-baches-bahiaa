# *Sistema de Registro y Gestión de Baches Bahía Blanca*                                          creado por facundo dies
                                                                                                              lucas garce
## Introducción
La ciudad de Bahía Blanca enfrenta problemas recurrentes relacionados con baches en la vía pública.  
Para mejorar la eficiencia en la reparación y el seguimiento de estos casos, se propone el desarrollo de un sistema que permita registrar, administrar y priorizar los reportes de baches realizados por los ciudadanos.

### Objetivo del sistema
Diseñar un Sistema que permita:
 * Registrar los datos de los usuarios que reportan baches, para asegurar el seguimiento de los casos y evitar duplicados.
 * Registrar reportes ciudadanos sobre baches.
 * Clasificarlos por nivel de gravedad y ubicación.
 * Evitar duplicación de reportes.
 * Asignar supervisores e inspectores según la prioridad.
 * Llevar seguimiento técnico y presupuestario de cada intervención.

---

## Usuarios del sistema
 * **Administradores / Personal municipal**: gestionan los reportes, asignan cuadrillas, verifican datos, supervisan los trabajos.  
 * **Ciudadanos / Usuarios externos**: reportan baches con evidencia (foto, video) e información básica del lugar.  

---

## Datos que gestiona el sistema
* Ubicación del bache: barrio, calle, coordenadas aproximadas.  
* IP del dispositivo o identificación del usuario (para evitar duplicados).  
* Tipo de calle: asfalto, tierra, empedrada, etc.  
* Tipo de rotura: grieta superficial, pozo profundo, desmoronamiento, hundimiento, etc.  
* Escala de gravedad del bache (1 a 10), según evidencia y cantidad de reportes.  
* Evidencia: fotos, videos.  
* Reportes relacionados (múltiples reclamos sobre la misma zona).  
* Estado del bache: registrado, en evaluación, en reparación, resuelto.  
* Daños a vehículos u objetos, si los hubo, con su respectiva documentación.  
* Materiales necesarios para la reparación y presupuesto estimado.  
* Tiempo desde el primer reporte.  

---

## Funcionalidades principales
* Registro de nuevos reportes con validación por IP o usuario.  
* Asignación de prioridad en base a evidencia y volumen de reportes.  
* Notificar al usuario cuando su reporte fue enviado exitosamente, y en caso de detectar un reporte previo del mismo usuario, informarle que ya existe un caso abierto asociado.  
* Detectar si ya existe un caso abierto en la misma zona y notificar al usuario antes de permitir un nuevo reporte, para evitar duplicaciones innecesarias.  
* Generación de estadísticas y reportes por zona.  
* Asignación automática de supervisores cuando hay alta actividad en una misma área.  
* Registro y seguimiento de costos, materiales y tiempo de obra.  

---

## Prevención de duplicados y abusos
El sistema implementará mecanismos para evitar reportes duplicados, como:
- Verificación por dirección e IP.  
- Registro de usuarios frecuentes.  
- Notificación al ciudadano si ya existe un caso abierto en esa zona.  
- Limitación de múltiples reportes por día desde un mismo origen.  

---

## Técnicas utilizadas para el relevamiento de requerimientos
* Observación directa de zonas afectadas.  
* Entrevistas a ciudadanos y empleados municipales.  
* Revisión de reportes previos o sistemas similares.  
* Prototipos conceptuales del sistema.  
* Análisis de patrones de reclamos según barrio.  

---

## Consideraciones adicionales
En caso de reclamos por daños, el sistema permitirá subir documentación de respaldo, aunque el tratamiento legal dependerá del municipio.  
La priorización automática considera tanto la gravedad técnica como la cantidad de reportes.  
Las zonas con múltiples baches serán agrupadas para evaluar intervenciones integrales.  

---

# Diagramas

##  Diagrama de Contexto 



<img width="1536" height="1024" alt="diagrama de contexto" src="https://github.com/user-attachments/assets/76f2b43a-033b-4842-bd66-4efc838a496b" />


##  Diagrama de caso de uso

<img width="1536" height="1024" alt="caso de uso 1" src="https://github.com/user-attachments/assets/d27dba90-dda0-454f-a7a3-ca49a1d5d074" />
<img width="1536" height="1024" alt="caso de uso 2" src="https://github.com/user-attachments/assets/8dfd6fdb-a4f1-4906-9fb8-36e37b79a74e" />


# Documentación de Casos de Uso  
**Sistema de Registro y Gestión de Baches - Bahía Blanca**

---

## Caso de Uso 1: Reportar Bache

| Campo | Descripción |
|-------|--------------|
| **Identificador** | CU-01 |
| **Nombre** | Reportar Bache |
| **Actor Principal** | Ciudadano |
| **Descripción** | El ciudadano utiliza el sistema para reportar un bache detectado en la vía pública. El sistema permite registrar la ubicación exacta mediante GPS o mapa interactivo, adjuntar una fotografía y una breve descripción del daño. Una vez enviado, el reporte se almacena con un identificador único para su posterior seguimiento y verificación. |
| **Precondiciones** | El ciudadano debe tener acceso a internet y una cuenta activa (opcional). El sistema debe estar disponible y operativo. |
| **Flujo Principal** | 1. El ciudadano accede a la aplicación web o móvil del sistema.<br>2. Selecciona la opción “Reportar bache”.<br>3. El sistema muestra un formulario con campos para ubicación, descripción y carga de imagen.<br>4. El ciudadano permite el acceso al GPS o marca la ubicación manualmente.<br>5. El ciudadano adjunta una foto opcional y completa la descripción.<br>6. El sistema valida los campos obligatorios (ubicación y descripción).<br>7. El ciudadano confirma el envío del reporte.<br>8. El sistema guarda los datos, genera un identificador único y asigna el estado “Pendiente de verificación”.<br>9. El sistema muestra un mensaje de confirmación y número de seguimiento. |
| **Flujo Alternativo** | 4a. Si el GPS no está disponible, el sistema permite ingresar la dirección manualmente.<br>6a. Si faltan campos obligatorios, el sistema muestra un mensaje de error y no permite continuar.<br>8a. Si hay un error en la conexión, el sistema guarda temporalmente el reporte para reintento automático. |
| **Postcondiciones** | El reporte queda almacenado en la base de datos y disponible para revisión por parte del inspector. |
| **Requerimientos Especiales** | El sistema debe validar la ubicación dentro del área urbana de Bahía Blanca. Las imágenes deben comprimirse automáticamente para optimizar el almacenamiento. |

---

## Caso de Uso 2: Asignar Reparación

| Campo | Descripción |
|-------|--------------|
| **Identificador** | CU-02 |
| **Nombre** | Asignar Reparación |
| **Actor Principal** | Inspector / Área de Obras Públicas |
| **Descripción** | Este caso de uso permite a los inspectores o al personal de Obras Públicas revisar los reportes de baches validados, asignar una cuadrilla de trabajo y establecer un nivel de prioridad. El objetivo es garantizar una planificación eficiente y ordenada de las reparaciones. |
| **Precondiciones** | Debe existir al menos un reporte verificado. El sistema debe tener cuadrillas disponibles registradas. |
| **Flujo Principal** | 1. El inspector inicia sesión en el sistema.<br>2. Accede al módulo de “Gestión de reportes”.<br>3. El sistema muestra la lista de reportes pendientes de reparación, con información de ubicación, gravedad y fecha del reporte.<br>4. El inspector selecciona un reporte para asignar.<br>5. El sistema muestra los equipos de trabajo disponibles y sus cargas actuales.<br>6. El inspector elige una cuadrilla y asigna prioridad (Alta, Media, Baja).<br>7. El sistema registra la asignación y actualiza el estado del reporte a “En reparación”.<br>8. Se genera una notificación automática para la cuadrilla asignada. |
| **Flujo Alternativo** | 5a. Si no hay cuadrillas disponibles, el sistema permite dejar el reporte en estado “En espera” y muestra una alerta informativa.<br>7a. Si ocurre un error de registro, el sistema conserva los datos temporales y solicita reintento. |
| **Postcondiciones** | El reporte queda vinculado a una cuadrilla específica y visible en el panel de seguimiento de obras. |
| **Requerimientos Especiales** | El sistema debe permitir filtrar los reportes por zona, fecha y prioridad. Las asignaciones deben registrarse con sello de tiempo (timestamp) para trazabilidad. |

---

## Caso de Uso 3: Generar Informe

| Campo | Descripción |
|-------|--------------|
| **Identificador** | CU-03 |
| **Nombre** | Generar Informe |
| **Actor Principal** | Administrador Municipal |
| **Descripción** | Este caso de uso permite generar reportes estadísticos sobre la gestión de baches, con información como cantidad de reportes, tiempos de reparación, zonas más afectadas y porcentaje de finalización. Los datos se pueden visualizar en gráficos y exportar a formatos estándar. |
| **Precondiciones** | Debe existir un historial de reportes en el sistema y el usuario debe tener permisos de administrador. |
| **Flujo Principal** | 1. El administrador accede al sistema y se autentica.<br>2. Selecciona el módulo “Generar informes”.<br>3. El sistema muestra los filtros disponibles: rango de fechas, zona, tipo de bache, estado, prioridad, etc.<br>4. El administrador configura los filtros y solicita el informe.<br>5. El sistema procesa la información y genera un resumen estadístico con tablas y gráficos.<br>6. El informe se muestra en pantalla con opción de exportar a PDF, Excel o CSV.<br>7. El sistema guarda una copia del informe generado para control histórico. |
| **Flujo Alternativo** | 3a. Si no hay datos que cumplan los filtros seleccionados, el sistema informa que no existen registros disponibles.<br>5a. Si ocurre un error en la generación, el sistema permite reintentar la operación. |
| **Postcondiciones** | Se genera y almacena un informe con la información solicitada, disponible para consulta futura. |
| **Requerimientos Especiales** | El sistema debe generar los informes en menos de 10 segundos y permitir su exportación a formatos estándar (PDF, XLSX, CSV). Los gráficos deben actualizarse dinámicamente. |

-

