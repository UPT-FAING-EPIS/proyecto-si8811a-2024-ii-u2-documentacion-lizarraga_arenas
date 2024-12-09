# Proyecto Juegos Florales - Plataforma Web

## Introducción
Los Juegos Florales son una tradición universitaria que fomenta la participación activa de los estudiantes en actividades culturales y artísticas. Sin embargo, la ausencia de una plataforma digital centralizada ha generado dificultades en la gestión y difusión de información. Este informe detalla el desarrollo de una plataforma web para resolver estas problemáticas, alineándose con los objetivos de la Universidad Privada de Tacna (UPT).

---

## Generalidades de la Empresa

### Nombre de la Empresa
**Universidad Privada de Tacna (UPT)**  
Una institución de educación superior comprometida con la formación integral de sus estudiantes, promoviendo valores éticos, académicos y culturales.

### Visión
Ser una institución líder en educación superior reconocida por su excelencia académica, innovación tecnológica y compromiso con el desarrollo cultural y social.

### Misión
Formar profesionales de alta calidad, fomentando la investigación, la cultura y la responsabilidad social mediante programas educativos innovadores.

---

## Visionamiento de la Empresa

### Descripción del Problema
Actualmente, la gestión y difusión de los Juegos Florales se realiza de forma manual y dispersa, causando problemas como:
- **Accesibilidad limitada**: Dificultades para encontrar información actualizada.
- **Falta de transparencia**: Desconfianza en los procesos de selección.
- **Visibilidad reducida**: Talento estudiantil no reconocido adecuadamente.

### Objetivos de Negocios
1. **Mejorar la eficiencia operativa** mediante la automatización de procesos.
2. **Incrementar la participación estudiantil** facilitando el acceso a la información.
3. **Fortalecer la imagen institucional** como líder en innovación tecnológica.
4. **Aumentar la transparencia y confianza** proporcionando información clara y actualizada.

### Objetivos de Diseño
- Crear una interfaz amigable y accesible.
- Implementar funcionalidades avanzadas de búsqueda y filtrado.
- Garantizar escalabilidad y sostenibilidad tecnológica.
- Cumplir con estándares de accesibilidad como WCAG.

---

## Alcance del Proyecto

1. **Diseño e implementación de la plataforma web**:
   - **Frontend**: React y Tailwind CSS.
   - **Backend**: Almacenamiento en Amazon S3.
2. **Funcionalidades principales**:
   - Registro e inscripción en actividades.
   - Publicación de cronogramas y resultados.
   - Exportación de datos.
3. **Capacitación y soporte**:
   - Entrenamiento para administradores.
   - Protocolos de mantenimiento.
4. **Documentación**:
   - Documento de visión.
   - Especificación de requisitos de software (SRS).
   - Documento de arquitectura de software (SAD).

---

## Viabilidad del Sistema

### Factibilidad Técnica
- Personal capacitado en React y Amazon S3.
- Recursos tecnológicos disponibles en la UPT.

### Factibilidad Económica
- Costos dentro de las capacidades de la universidad.
- Reducción de gastos en procesos manuales.

### Factibilidad Operativa
- Optimización de la gestión del evento.
- Capacitación del personal para una transición fluida.

### Factibilidad Social
- Impacto positivo en la comunidad estudiantil.
- Mayor participación en los Juegos Florales.

### Factibilidad Legal
- Protección de datos personales y derechos de autor.
- Cumplimiento con reglamentos internos de la universidad.

### Factibilidad Ambiental
- Digitalización que reduce la huella ecológica.

## Análisis de Procesos

### Diagrama del Proceso Actual – Diagrama de actividades

![image](https://github.com/user-attachments/assets/086fae9a-4bb5-4661-87eb-3bbb1d8c9452)

### Diagrama del Proceso Propuesto – Diagrama de actividades Inicial

![image](https://github.com/user-attachments/assets/21769ebf-5066-498c-8379-300b5fd69f60)

## Especificación de Requerimientos de Software

### Requerimientos Funcionales

| ID   | Nombre                   | Descripción                                                                 | Prioridad | Actor       |
|------|--------------------------|-----------------------------------------------------------------------------|-----------|-------------|
| RF1  | Registro de Usuarios     | Permitir a los estudiantes registrarse con sus datos personales.           | Alta      | Estudiantes |
| RF2  | Inscripción en Actividades | Facilitar la inscripción en actividades por categorías.                    | Alta      | Estudiantes |
| RF3  | Configuración de Eventos | Los organizadores pueden gestionar eventos y categorías.                   | Alta      | Organizadores |
| RF4  | Publicación del Cronograma | Mostrar un cronograma dinámico filtrable por categoría y fecha.            | Media     | Sistema     |
| RF5  | Evaluación de Actividades | Permitir a los jueces evaluar actividades y enviar observaciones.           | Alta      | Jueces      |
| RF6  | Registro de Puntajes     | Integrar un módulo para registrar puntajes y comentarios.                  | Alta      | Organizadores |
| RF7  | Consulta de Resultados   | Permitir la consulta de resultados en tiempo real con gráficos y resúmenes. | Alta      | Estudiantes |

### Requerimientos No Funcionales

| ID    | Nombre          | Descripción                                                  | Prioridad | Actor       |
|-------|-----------------|--------------------------------------------------------------|-----------|-------------|
| RNF1  | Usabilidad      | La plataforma debe ser intuitiva y accesible.               | Alta      | Sistema     |
| RNF2  | Escalabilidad   | El sistema debe soportar múltiples usuarios simultáneamente. | Alta      | Sistema     |
| RNF3  | Seguridad       | Protección de datos personales y normativas de seguridad.   | Alta      | Sistema     |
| RNF4  | Tiempo de Respuesta | Operaciones principales deben realizarse en menos de 10 segundos. | Alta      | Sistema     |
| RNF5  | Disponibilidad  | Disponibilidad del 99.5% del tiempo.                        | Media     | Sistema     |

---

## Fase de Desarrollo

### Perfiles de Usuario
- **Estudiante**: Se inscribe en actividades y consulta resultados.
- **Organizador**: Gestiona eventos y supervisa actividades.
- **Juez**: Evalúa participantes y envía observaciones.
- **Sistema**: Procesa y publica información.

### Casos de Uso

![image](https://github.com/user-attachments/assets/07dc6ddc-6855-46da-9773-5171792712a1)

#### Caso de Uso: Registrar Eventos
- **Actor Principal**: Organizador.
- **Flujo Normal**:
  1. El organizador accede a la sección de eventos.
  2. Completa el formulario del evento.
  3. El sistema valida y registra el evento.

```mermaid
sequenceDiagram
  actor Organizador
  participant Sistema

  Organizador->>Sistema: Accede a la sección "Eventos"
  Organizador->>Sistema: Selecciona "Agregar Evento"
  Organizador->>Sistema: Completa el formulario (nombre, descripción, categoría, fecha)
  Sistema->>Sistema: Valida la información
  alt Validación exitosa
    Sistema->>Sistema: Guarda evento en la base de datos
    Sistema->>Organizador: Muestra mensaje de confirmación
  else Validación fallida
    Sistema->>Organizador: Muestra error de validación
  end
```

#### Caso de Uso: Consultar Resultados
- **Actor Principal**: Estudiante.
- **Flujo Normal**:
  1. El estudiante selecciona la categoría deseada.
  2. Visualiza los resultados en una tabla.
  3. Puede descargar un reporte en PDF.

```mermaid
sequenceDiagram
  actor Estudiante
  participant Sistema

  Estudiante->>Sistema: Accede a la sección "Resultados"
  Estudiante->>Sistema: Selecciona categoría o evento
  Sistema->>Sistema: Consulta la base de datos
  Sistema->>Estudiante: Muestra resultados en tabla
  Estudiante->>Sistema: Solicita reporte en PDF
  Sistema->>Estudiante: Descarga el reporte en PDF
```

#### Caso de Uso: Evaluar Actividades
- **Actor Principal**: Juez.
- **Flujo Normal**:
  1. El juez selecciona la actividad a evaluar.
  2. Ingresa puntajes y comentarios.
  3. El sistema guarda las evaluaciones.

```mermaid
sequenceDiagram
  actor Juez
  participant Sistema

  Juez->>Sistema: Accede a la sección "Evaluaciones"
  Juez->>Sistema: Selecciona actividad a evaluar
  Sistema->>Juez: Muestra lista de participantes
  Juez->>Sistema: Asigna puntajes y comentarios
  Sistema->>Sistema: Valida puntajes ingresados
  Juez->>Sistema: Confirma evaluación
  Sistema->>Sistema: Guarda resultados en la base de datos
```

#### Caso de Uso 4: Procesar Resultados
- **Actor Principal**: Sistema (automatizado).
- **Flujo Normal**:
   1. El sistema verifica que todas las evaluaciones para un evento estén completas.
   2. Calcula el puntaje promedio o total para cada participante según las reglas definidas.
   3. Almacena los puntajes procesados en la base de datos.
   4. Publica automáticamente los resultados en la sección "Resultados" de la plataforma.
   5. Notifica a los organizadores que los resultados están disponibles.

```mermaid
sequenceDiagram
  actor Sistema
  participant BaseDeDatos
  participant Organizador

  Sistema->>BaseDeDatos: Verifica si todas las evaluaciones están completas
  Sistema->>Sistema: Calcula puntajes promedios/totales
  Sistema->>BaseDeDatos: Almacena puntajes procesados
  Sistema->>Sistema: Publica resultados en la plataforma
  Sistema->>Organizador: Notifica que los resultados están disponibles
```

#### Caso de Uso 5: Supervisar Actividades
- **Actor Principal**: Organizador.
- **Flujo Normal**:
	1. El organizador accede a la sección "Supervisión de Actividades".
	2. Selecciona una actividad en progreso.
	3. Visualiza el estado de las evaluaciones realizadas por los jueces.
	4. Si es necesario, puede enviar recordatorios a los jueces para completar las evaluaciones.
	5. El organizador finaliza la supervisión.

```mermaid
sequenceDiagram
  actor Organizador
  participant Sistema

  Organizador->>Sistema: Accede a "Supervisión de Actividades"
  Organizador->>Sistema: Selecciona actividad en progreso
  Sistema->>Organizador: Muestra estado de evaluaciones
  Organizador->>Sistema: Envia recordatorios a jueces (si necesario)
  Organizador->>Sistema: Finaliza supervisión
```

### Diagrama de Clases

```mermaid

classDiagram
    class CountdownTimer {
        +calculateTimeLeft()
        +render()
        -timeLeft: Object
    }
    
    class EventCard {
        +render()
    }
    
    class Footer {
        +render()
    }
    
    class Header {
        +render()
    }
    
    class Home {
        +render()
    }
    
    class Navbar {
        +render()
    }
    
    class Event {
        +nombre: String
        +fechaInicio: String
        +fechaTermino: String
        +facultad: String
    }
    
    class AuthSlice {
        +onChecking()
        +onLogin(payload)
        +onLogout(payload)
    }
    
    class EventSlice {
        +onAddNewEvent(payload)
        +onDeleteEvent()
        +onLoadEvents(payload)
        +onSetActiveEvent(payload)
    }
    
    class Store {
        +configureStore()
    }
    
    class useAuthStore {
        +loginWithGoogle()
        +checkAuthToken()
        +startLogout()
    }
    
    class useEventStore {
        +startLoadingEvents()
    }
    
    class categoriasApi {
        +getCategorias()
    }
    
    class equipoApi {
        +getEquipos()
    }
    
    class eventoApi {
        +getEvents()
    }
    
    class lugaresApi {
        +getLugares()
    }
    
    class participanteApi {
        +getParticipantes()
    }

    Header --> Navbar
    Home --> Header
    Home --> Footer
    Home --> CountdownTimer
    Home --> EventCard
    Home --> Event
    
    EventCard --> Event
    
    AuthSlice --> Store
    EventSlice --> Store
    
    useAuthStore --> AuthSlice
    useEventStore --> EventSlice

    categoriasApi --> Home
    equipoApi --> Home
    eventoApi --> Home
    lugaresApi --> Home
    participanteApi --> Home
```

## Conclusiones
La plataforma representa un avance significativo en la gestión de los Juegos Florales, mejorando la transparencia, participación y eficiencia. Su diseño moderno asegura un desempeño óptimo, mientras que su escalabilidad permite adaptarse a futuras necesidades.
