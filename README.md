# gestion-de-baches-bahia
# *Sistema de Registro y Gestión de Baches Bahía Blanca*

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

## 📌 Diagrama de Contexto (Nivel 0) + 📌 DFD Nivel 1

```mermaid
flowchart LR
    %% ==== DIAGRAMA DE CONTEXTO ====
    subgraph Contexto [Diagrama de Contexto]
        C[Ciudadano] -->|Reporte (foto, ubicación, tipo)| S[Sistema de Gestión de Baches]
        S -->|Confirmación, estado del caso| C

        A[Administrador Municipal] -->|Asignación cuadrillas, cambios de estado| S
        S -->|Listas de reportes, estadísticas| A

        I[Inspector / Supervisor] -->|Validación en terreno| S
        S -->|Casos asignados| I

        N[Servicio de Notificaciones] -->|SMS / Email| C
        S -->|Solicitud de notificación| N
    end

    %% ==== DFD NIVEL 1 ====
    subgraph DFD [DFD Nivel 1]
        subgraph P1[1. Recepción de Reportes]
            C -->|Reporte| P1
            P1 --> D4[(Evidencias)]
            P1 --> D1[(Reportes)]
        end

        subgraph P2[2. Verificación y Dedupl.]
            P1 --> P2
            D1 --> P2
            D2[(Usuarios)] --> P2
        end

        subgraph P3[3. Priorización]
            P2 --> P3
            P3 --> D1
        end

        subgraph P4[4. Asignación y Gestión]
            P3 --> P4
            P4 --> D3[(Intervenciones/Presupuesto)]
            A --> P4
            P4 --> A
            P4 --> I
            I --> P4
        end

        subgraph P5[5. Seguimiento y Costos]
            P4 --> P5
            P5 --> D3
            P5 --> A
        end

        P2 -->|Duplicado detectado| N
        P4 -->|Avisos de avance| N
        N -->|SMS/Email| C
    end
