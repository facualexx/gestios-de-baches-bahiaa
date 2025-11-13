### Creado por $${\color{red}Facundo \space \color{orange}Diez \space :star: \space \color{blue}Lucas \space \color{lightblue}Garcé}$$

<h1 align="center"><i> Sistema de Registro y Gestión de Baches Bahía Blanca </i></h1>

&nbsp;

## Introducción
La ciudad de Bahía Blanca enfrenta problemas recurrentes relacionados con baches en la vía pública.<br>
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
* Ubicación y Tipo
    * Ubicación del bache: barrio, calle, coordenadas aproximadas.  
    * Tipo de calle: asfalto, tierra, empedrada, etc.
    * Ubicación dentro de la calzada: Medio, Cuneta, Bordillo.
    * Tipo de rotura: grieta superficial, pozo profundo, desmoronamiento, hundimiento, etc.
* Identificación y Gravedad  
    * IP del dispositivo o identificación del usuario (para evitar duplicados).
    * Escala de gravedad del bache (1 a 10), según evidencia y cantidad de reportes.
* Evidencia Y Estado
    * Evidencia: Fotos y/o videos (máx. 30 segundos).
    * El sistema debe limpiar la metadata (p.ej., GPS, modelo de dispositivo) de las imágenes y videos al momento de la carga para proteger la privacidad del usuario.
    * Reportes relacionados (múltiples reclamos sobre la misma zona).
    * Estado del bache: registrado, en evaluación, en reparación, resuelto.
* Logística y Costos
    * Daños a vehículos u objetos, si los hubo, con su respectiva documentación.
    * Materiales necesarios para la reparación y presupuesto estimado.  
    * Tiempo desde el primer reporte.
    * Detalle de la Orden de Trabajo: Equipo asignado, cantidad de material de relleno, horas estimadas de reparación, costo total de reparación (materiales + mano de obra).

---

## Funcionalidades principales
* Regístro y Validación
    * Registro de nuevos reportes con validación por IP o usuario.  
* Priorización
    * Asignación de prioridad en base a evidencia y volumen de reportes.  
* Notificación al Usuario
    * Notificar al usuario cuando su reporte fue enviado exitosamente, y en caso de detectar un reporte previo del mismo usuario, informarle que ya existe un caso abierto asociado.  
* Detección de Duplicados
    * Detectar si ya existe un caso abierto en la misma zona y notificar al usuario antes de permitir un nuevo reporte, para evitar duplicaciones innecesarias.  
* Reportes y Estadísticas
    * Generación de estadísticas y reportes por zona.  
* Asignación Automática
    * Asignación automática de supervisores cuando hay alta actividad en una misma área.  
* Seguimiento de Costos
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
* Obsevación Directa
    * Observación directa de zonas afectadas.  
* Entrevistas
    * Entrevistas a ciudadanos y empleados municipales.  
* Revisión de Sistemas
    * Revisión de reportes previos o sistemas similares.  
* Prototipos
    * Prototipos conceptuales del sistema.  
* Análisis de patrones
    * Análisis de patrones de reclamos según barrio.  

---

## Consideraciones adicionales
En caso de reclamos por daños, el sistema permitirá subir documentación de respaldo, aunque el tratamiento legal dependerá del municipio.<br>
La priorización automática considera tanto la gravedad técnica como la cantidad de reportes.<br>
Las zonas con múltiples baches serán agrupadas para evaluar intervenciones integrales.  

---

## Requerimientos No Funcionales (RNF)

| Categoría | Requisito | Propósito |
| :---: | :---: | :---: |
| **Accesibilidad (A11Y)** | El sistema debe cumplir con el nivel AA de las pautas WCAG 2.1. | Garantizar el acceso a usuarios con discapacidades visuales o cognitivas (ej. daltónicos, disléxicos). |
| **Usabilidad** | La interfaz debe ofrecer al menos dos esquemas de color contrastantes (modo oscuro / alto contraste). | Asistencia para usuarios con visión reducida o sensibilidad a la luz. |
| **Usabilidad** | La tipografía debe ser **clara y escalable**, evitando fuentes con serifa excesivas. | Mejorar la legibilidad para usuarios con dislexia o TDAH. |
| **Rendimiento** | El tiempo de carga de cualquier pantalla (excluyendo la generación de informes) no debe superar los 2 segundos. | |
| **Seguridad** | Todas las comunicaciones de reportes y gestión deben usar cifrado SSL/TLS. | Proteger los datos de ubicación y la información municipal. |

---

# Diagramas

##  Diagrama de Contexto

<img width="2281" height="807" alt="Untitled diagram-2025-11-11-165848" src="https://github.com/user-attachments/assets/6aba9f4a-3017-4f50-9cf8-946edfab6e37" />

##  Diagrama de caso de uso

<img width="1121" height="752" alt="caso de uso bachess drawio" src="https://github.com/user-attachments/assets/be1c0b60-006d-494d-9cc4-db3252c1a69a" />


# Documentación de Casos de Uso  
**Sistema de Registro y Gestión de Baches - Bahía Blanca**

---

## Caso de Uso 1: Reportar Bache

| Campo | Descripción |
|-------|--------------|
| **Identificador** | CU-01 |
| **Nombre** | Reportar Bache |
| **Actor Principal** | Ciudadano |
| **Descripción** | El ciudadano utiliza el sistema para reportar un bache detectado en la vía pública. El sistema permite registrar la ubicación exacta mediante GPS o mapa interactivo, adjuntar evidencia multimedia (fotografía o video) y una breve descripción del daño. El sistema utilizará los metadatos GPS para una verificación inicial de ubicación y frescura, luego de lo cual serán eliminados para proteger la privacidad del ciudadano. Una vez enviado, el reporte se almacena con un identificador único para su posterior seguimiento y verificación. |
| **Precondiciones** | El ciudadano debe tener acceso a internet y una cuenta activa (opcional). El sistema debe estar disponible y operativo. |
| **Flujo Principal** | 1. Selecciona la opción “Reportar bache”.<br>2. El sistema muestra un formulario con campos para ubicación, ubicación en la calzada, nivel de gravedad inicial (1-10), descripción y carga de imagen.<br>3. El ciudadano permite el acceso al GPS o marca la ubicación manualmente.<br>4. El ciudadano adjunta una foto o video opcional y completa la descripción.<br>5. El sistema valida los campos obligatorios (ubicación y descripción).<br>6. El ciudadano confirma el envío del reporte.<br>7. El sistema guarda los datos, genera un identificador único y asigna el estado “Pendiente de verificación”.<br>8. El sistema muestra un mensaje de confirmación y número de seguimiento. |
| **Flujo Alternativo** | 3a. Si el GPS no está disponible, el sistema permite ingresar la dirección manualmente mediante un campo de texto y un mapa que sugiere ubicaciones.<br>3b. Continúa en el paso 4.<hr>5a. **(Validación - Límite Diario)** Si el sistema detecta que el ciudadano (por ID/IP/MAC) ha excedido el límite de 4 reportes diferentes en las últimas 24 horas, muestra una alerta informativa.<br>5b. El sistema no permite la carga del reporte y se finaliza el Caso de Uso.<br><br>5c. **(Validación - Límite Geográfico)** Si el sistema detecta que el ciudadano (por ID/IP/MAC) ha reportado un bache previamente en la misma dirección (dentro de 10.000 metros) en los últimos 7 días, muestra una notificación de caso activo.<br>5d. El sistema no permite el envío, sino que redirige al usuario al seguimiento del reporte existente (Paso 9).<br><br>5e. **(Validación - Límite de Expiración/Tiempo Válido)** Si el sistema determina que el archivo multimedia es demasiado antiguo (más de 7 días), el sistema muestra un mensaje de error sobre la calidad de la prueba y no permite continuar.<br>5f. El sistema no permite la carga del reporte.<br><br>5g. **(Validación - Prueba No Concluyente)** Si el sistema determina que el archivo multimedia ha sido modificado (manipulación de metadatos de archivo o su contenido), muestra una advertencia sobre la calidad de la prueba.<br>5h.	El sistema marca el reporte con Prioridad Baja (Baja Veracidad) y permite continuar en el paso 7, pero con menor peso en la clasificación automática de gravedad.<br><br>5i. **(Validación - Campos faltantes)** Si faltan campos obligatorios, el sistema muestra un mensaje de error sobre los campos faltantes y no permite continuar.<br>5j. El ciudadano corrige los campos y reintenta el envío del reporte (Paso 6).<hr><br>7a. Si hay un error en la conexión, el sistema guarda temporalmente el reporte, incluyendo el identificador único generado, para reintento automático. |
| **Postcondiciones** | El reporte queda almacenado en la base de datos y disponible para revisión por parte del inspector. |
| **Requerimientos Especiales** | El sistema debe validar la ubicación dentro del área urbana de Bahía Blanca, priorizando reportes cuya evidencia contenga metadatos GPS. Los archivos multimedia deben tener una fecha de creación no superior a 7 días respecto a la fecha de subida. Si la evidencia no cumple con la geolocalización o se detecta una modificación posterior a la creación original, el reporte recibirá una prioridad menor hasta que se acumulen al menos cinco reportes válidos con geolocalización, originalidad y frescura coincidente en la misma zona. Las imágenes y videos deben comprimirse automáticamente para optimizar el almacenamiento y debe eliminarse toda la metadata EXIF/GPS de los archivos multimedia, después de la verificación inicial, para proteger la privacidad del ciudadano. |

---

## Caso de Uso 2: Asignar Reparación

| Campo | Descripción |
|-------|--------------|
| **Identificador** | CU-02 |
| **Nombre** | Asignar Reparación |
| **Actor Principal** | Inspector / Área de Obras Públicas |
| **Descripción** | Este caso de uso permite a los inspectores o al personal de Obras Públicas revisar los reportes de baches validados, asignar una cuadrilla de trabajo y establecer un nivel de prioridad, que incluye la gravedad técnica (del reporte) y la prioridad operacional (por zona o tráfico). El objetivo es garantizar una planificación eficiente y ordenada de las reparaciones. |
| **Precondiciones** | Debe existir al menos un reporte verificado y pendiente de asignación. El sistema debe tener cuadrillas disponibles registradas. |
| **Flujo Principal** | 1. El inspector accede al módulo de “Gestión de reportes”.<br>2. El sistema muestra la lista de reportes pendientes de reparación, con información de ubicación, gravedad y fecha del reporte.<br>3. El inspector selecciona un reporte para asignar.<br>4. El sistema muestra los equipos de trabajo disponibles y sus cargas actuales.<br>5. El inspector elige una cuadrilla y asigna **Prioridad Operacional (Alta, Media, Baja)** y **Horas estimadas y Materiales de reparación** (para cálculo del costo).<br>6. El sistema registra la asignación, calcula el costo estimado de la reparación, y actualiza el estado del reporte a “En reparación”.<br>7. Se genera una notificación automática para la cuadrilla asignada, incluyendo el Identificador Único y la ubicación. |
| **Flujo Alternativo** | 2a.	Si el sistema, al mostrar la lista de reportes, detecta que no hay reportes pendientes de asignación (o bien, que todos los reportes han sido descartados en un flujo previo), muestra un mensaje: "No hay baches verificados pendientes de acción.".<br>2b. El inspector regresa al menú principal (o a otra tarea). Se finaliza el Caso de Uso.<br><br>2c. (Falso Positivo) Si el Inspector determina que el reporte es un duplicado, falso positivo, o está fuera de jurisdicción, selecciona la opción "Descartar".<br>2d. El sistema asigna el estado "DESCARTADO" al reporte y lo elimina de la lista de pendientes de asignación. Vuelve a cargar el Paso 2.<hr><br>4a. Si no hay cuadrillas disponibles, el sistema permite dejar el reporte en estado “En espera” y muestra una alerta informativa.<br>4b. El reporte permanece en la lista de asignación con prioridad alta y se finaliza el Caso de Uso.<hr><br>6a. Si ocurre un error de registro al guardar la asignación, el sistema conserva los datos temporales y muestra un mensaje de error.<br>6b. El Inspector reintentar la operación y continua con el paso 7. |
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
| **Flujo Principal** | 1. El administrador selecciona el módulo “Generar informes”.<br>2. El sistema muestra los filtros disponibles: rango de fechas, zona, tipo de bache, estado, prioridad, etc.<br>3. El administrador configura los filtros y solicita el informe.<br>4. El sistema procesa la información y genera un resumen estadístico con tablas y gráficos.<br>5. El informe se muestra en pantalla con opción de exportar a PDF, Excel o CSV.<br>6. El sistema guarda una copia del informe generado, con un identificador único, para control histórico. |
| **Flujo Alternativo** | 3a. Si no hay datos que cumplan los filtros seleccionados, el sistema informa que no existen registros disponibles.<br> 3b. El Administrador correge los filtros y continua con el paso 4<hr><br>4a. Si ocurre un error de procesamiento o de conexión a la base de datos durante la generación del informe, el sistema muestra un mensaje de error técnico.<br>4b. El Administrador reintenta la generación del informe y continua con el Paso 5. |
| **Postcondiciones** | Se genera y almacena un informe con la información solicitada, disponible para consulta futura. |
| **Requerimientos Especiales** | El sistema debe generar los informes en menos de 10 segundos y permitir su exportación a formatos estándar (PDF, XLSX, CSV). Los gráficos deben actualizarse dinámicamente. |
