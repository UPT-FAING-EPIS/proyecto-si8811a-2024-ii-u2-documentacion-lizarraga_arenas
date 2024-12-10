**Proyecto “Aplicativo Movil Juegos Florales”**

## Introducción
### Propósito

El propósito de nuestro proyecto es desarrollar un aplicativo móvil que facilite la inscripción y gestión de equipos participantes en los juegos de actividades florales universitarias, optimizando los procesos actuales y promoviendo una mayor participación estudiantil.

### Alcance

Desarrollar una solución tecnológica que permita a los equipos universitarios registrarse de manera autónoma, acceder a información relevante de los juegos, y recibir notificaciones sobre eventos, todo ello a través de una plataforma móvil accesible y fácil de usar.

### Definición siglas y abreviaturas

- App: Aplicación móvil, un software diseñado específicamente para dispositivos móviles como teléfonos inteligentes y tabletas, que permite a los usuarios interactuar con diversas funcionalidades de manera sencilla y eficiente.
- UI (Interfaz de Usuario): Es la parte visual del sistema que permite a los usuarios interactuar con la aplicación, incluyendo botones, menús, formularios y otros elementos gráficos diseñados para ofrecer una experiencia intuitiva y accesible.
- UX (Experiencia de Usuario): Hace referencia a la percepción y satisfacción del usuario al interactuar con la aplicación, englobando aspectos como facilidad de uso, funcionalidad y estética.
- API (Interfaz de Programación de Aplicaciones): Conjunto de reglas y protocolos que permiten que diferentes aplicaciones o componentes del sistema se comuniquen entre sí, facilitando la integración de servicios externos o funcionalidades adicionales al aplicativo móvil.

### Referencias

- Guías de diseño de interfaces móviles (Google Material Design, Human Interface Guidelines).
- Estudios previos de gestión tecnológica en eventos estudiantiles.
- Documentación técnica de herramientas de desarrollo móvil como Flutter y React Native.

### Visión General

- La visión que tenemos de nuestro sistema web, es que va a resultar innovadora al utilizar la APIS como escala, para la inscripción de equipos en los juegos de actividades florales universitarias. Se presentan el propósito, el alcance, los términos clave y las referencias relevantes, así como una visión detallada de los objetivos y características principales del sistema.

## **Representación Arquitectónica**

1. Escenarios:

1. Requerimientos Funcionales

|**ID**|**Requerimiento**|**Descripción**|
| -: | :- | :-: |
|RF1|Autenticación y Usuarios|<p>- Inicio de sesión mediante cuentas Microsoft</p><p>- Roles diferenciados (administrador y usuario estándar)</p><p>- Cierre de sesión seguro</p>|
|RF2|Gestión de Eventos</p>|<p>- Crear, editar, eliminar y visualizar eventos</p><p>- Asignar fechas y ubicaciones a eventos</p><p>- Gestionar estados de eventos</p>|
|RF3|Gestión de Participantes</p>|<p>- Registro y administración de participantes</p><p>- Asignación de participantes a eventos</p><p>- Control de información personal</p>|
|RF4|Gestión de Equipos</p>|<p>- Crear y administrar equipos</p><p>- Asignar participantes a equipos</p><p>- Vincular equipos con eventos</p>|
|RF5|Gestión de Ubicaciones</p>|<p>- Registro de ubicaciones para eventos.</p><p>- Detalles y disponibilidad de espacios.</p><p>- Asignación de ubicaciones a eventos</p>|



1. Requerimientos No Funcionales - Atributos de Calidad



|**ID**|**Requerimiento**|**Descripción**|
| :-: | :-: | :-: |
|<p></p><p></p><p>RNF1</p>|<p></p><p></p><p>Seguridad</p>|<p>- Autenticación segura con Microsoft</p><p>- Protección de datos personales</p><p>- Control de acceso basado en roles</p>|
|<p></p><p></p><p>RNF2</p>|<p></p><p></p><p>Usabilidad</p>|<p>- Interfaz intuitiva y responsive</p><p>- Tiempos de respuesta rápidos</p><p>- Diseño adaptable a diferentes dispositivos</p>|
|<p></p><p></p><p>RNF3</p>|<p></p><p></p><p>Rendimiento</p>|<p>- Carga rápida de datos</p><p>- Optimización de recursos</p><p>- Manejo eficiente de la memoria</p>|
|<p></p><p></p><p>RNF4</p>|<p></p><p></p><p>Mantenibilidad</p>|<p>- Código modular y documentado</p><p>- Facilidad de actualización</p><p>- Gestión de versiones</p>|



1. Restricciones

- Disponibilidad de datos: El sitio depende de la disponibilidad y precisión de los datos sobre lugares, equipos a competir.

- Acceso a internet: Los usuarios deben tener acceso a una conexión a internet para utilizar todas las funcionalidades del sitio, especialmente la visualización de mapas y la búsqueda en tiempo real.
- Precisión de la información: La calidad de la información proporcionada, como horarios de apertura y tarifas, depende de la actualización y precisión de las fuentes de datos utilizadas.
- Integración con servicios externos: La integración con proveedores de servicios externos, como sistemas de transporte público, puede estar sujeta a restricciones técnicas o de colaboración.



1. ## **Representación de la Arquitectura del Sistema**

1. Vista de Caso de Uso:

3\.1.1. Diagramas de Casos de Uso

![image](https://github.com/user-attachments/assets/edd9c4cb-755b-4a09-ac8e-b2971e446fde)


1. Vista Lógica


1. Diagrama de Subsistemas (paquetes)

1. Diagrama de Secuencia (vista de diseño)

RF1: Autenticación y Usuarios

```mermaid
sequenceDiagram
    participant MyHomePage
    participant AuthService
    participant MyApp
    participant MenuScreen

    MyHomePage->>AuthService: login()
    AuthService->>MyHomePage: Return login status
    MyHomePage->>MyApp: Navigate to MenuScreen
    MyHomePage->>MenuScreen: Display Menu
    MyHomePage->>AuthService: logout()
    AuthService->>MyHomePage: Return logout status
```

RF2: Gestión de Eventos

```mermaid
sequenceDiagram
    participant MenuScreen
    participant EventosScreen
    participant Evento
    participant AuthService

    MenuScreen->>EventosScreen: navigateToEventManagement()
    EventosScreen->>Evento: fetchEvents()
    Evento->>EventosScreen: return list of events
    EventosScreen->>MenuScreen: Display events
    MenuScreen->>EventosScreen: createEvent()
    EventosScreen->>Evento: saveEvent()
    Evento->>EventosScreen: return created event
    MenuScreen->>EventosScreen: editEvent()
    EventosScreen->>Evento: updateEvent()
    Evento->>EventosScreen: return updated event
    MenuScreen->>EventosScreen: deleteEvent()
    EventosScreen->>Evento: deleteEvent()
    Evento->>EventosScreen: return deletion confirmation
```

RF3: Gestión de Participantes

```mermaid
sequenceDiagram
    participant MenuScreen
    participant ParticipantsScreen
    participant Participante

    MenuScreen->>ParticipantsScreen: navigateToParticipantManagement()
    ParticipantsScreen->>Participante: fetchParticipants()
    Participante->>ParticipantsScreen: return list of participants
    ParticipantsScreen->>MenuScreen: Display participants
    MenuScreen->>ParticipantsScreen: addParticipant()
    ParticipantsScreen->>Participante: saveParticipant()
    Participante->>ParticipantsScreen: return created participant
    MenuScreen->>ParticipantsScreen: editParticipant()
    ParticipantsScreen->>Participante: updateParticipant()
    Participante->>ParticipantsScreen: return updated participant
    MenuScreen->>ParticipantsScreen: assignParticipantToEvent()
    ParticipantsScreen->>Participante: assignToEvent()
    Participante->>ParticipantsScreen: return confirmation

```

RF4: Gestión de Equipos

```mermaid
sequenceDiagram
    participant MenuScreen
    participant EquiposScreen
    participant Equipo
    participant Participante

    MenuScreen->>EquiposScreen: navigateToTeamManagement()
    EquiposScreen->>Equipo: fetchEquipos()
    Equipo->>EquiposScreen: return list of teams
    EquiposScreen->>MenuScreen: Display teams
    MenuScreen->>EquiposScreen: createTeam()
    EquiposScreen->>Equipo: saveTeam()
    Equipo->>EquiposScreen: return created team
    MenuScreen->>EquiposScreen: assignParticipantsToTeam()
    EquiposScreen->>Participante: assignToTeam()
    Participante->>EquiposScreen: return assignment confirmation
    MenuScreen->>EquiposScreen: linkTeamToEvent()
    EquiposScreen->>Equipo: linkToEvent()
    Equipo->>EquiposScreen: return linked team to event
```

RF5: Gestión de Ubicaciones

```mermaid
sequenceDiagram
    participant MenuScreen
    participant EquiposScreen
    participant EventosScreen
    participant Location

    MenuScreen->>EventosScreen: navigateToLocationManagement()
    EventosScreen->>Location: fetchLocations()
    Location->>EventosScreen: return list of locations
    EventosScreen->>MenuScreen: Display locations
    MenuScreen->>EventosScreen: assignLocationToEvent()
    EventosScreen->>Location: assignLocation()
    Location->>EventosScreen: return location assignment confirmation
```

1. Diagrama de Colaboración (vista de diseño)

Requerimiento RF-1: Iniciar Sesión
```mermaid
flowchart TD
    actor1[Usuario] -->|Inicia la aplicación| sistema1[Sistema]
    sistema1 -->|Muestra página de inicio con opciones| actor1
    actor1 -->|Hace clic en 'Ingresar con Cuenta Microsoft'| sistema1
    sistema1 -->|Solicita inicio de sesión| microsoftAuth[MicrosoftAuth]
    microsoftAuth -->|Muestra formulario de inicio de sesión| sistema1
    actor1 -->|Ingresa correo y contraseña| microsoftAuth
    microsoftAuth -->|Valida credenciales| sistema1
    sistema1 -->|Muestra menú principal| actor1
```

Requerimiento RF-2: Visualizar Eventos
```mermaid
flowchart TD
    actor1[Usuario] -->|Selecciona 'Ubicaciones'| sistema1
    sistema1 -->|Solicita integración con Google Maps| googleMaps[GoogleMaps]
    googleMaps -->|Muestra mapa| sistema1
    sistema1 -->|Muestra ubicaciones en mapa| actor1
```

Requerimiento RF-4: Visualizar Equipos
```mermaid
flowchart TD
    actor1[Usuario] -->|Selecciona 'Equipos'| sistema1
    sistema1 -->|Muestra lista de equipos| actor1
    sistema1 -->|Muestra participantes y buscador| actor1
```

Requerimiento RF-5: Visualizar Participantes
```mermaid
flowchart TD
    actor1[Usuario] -->|Selecciona 'Eventos'| sistema1
    sistema1 -->|Solicita listado de participantes| actor1
    actor1 -->|Muestra listado con opciones de agregar y editar| sistema1
```

Requerimiento RF-6: Visualizar Coordinadores Docentes
```mermaid
flowchart TD
    actor1[Usuario] -->|Selecciona 'Coordinadores Docentes'| sistema1
    sistema1 -->|Solicita información de coordinadores docentes| actor1
    actor1 -->|Muestra listado de coordinadores docentes| sistema1
```

Requerimiento RF-7: Visualizar Coordinadores Estudiantes

```mermaid
flowchart TD
    actor1[Usuario] -->|Selecciona 'Coordinadores Estudiantes'| sistema1
    sistema1 -->|Solicita información de coordinadores estudiantes| actor1
    actor1 -->|Muestra listado de coordinadores con información| sistema1
```

1. Diagrama de Objetos

1. Diagrama de Clases

```mermaid

   classDiagram
    class MyApp {
        +MyApp()
        +Widget build(BuildContext context)
    }

    class MyHomePage {
        +MyHomePage(String title, GlobalKey navigatorKey)
        +Widget build(BuildContext context)
        +void _login()
        +void _navigateToMenu()
    }

    class AuthService {
        +AuthService(GlobalKey navigatorKey)
        +Future login()
        +Future logout()
    }

    class MenuScreen {
        +MenuScreen(String username)
        +Widget build(BuildContext context)
        +void _logout(BuildContext context)
        +Widget _buildCard(String title, String imagePath, String color, Widget? destination)
    }

    class EquiposScreen {
        +EquiposScreen()
        +Widget build(BuildContext context)
        +Future fetchEquipos()
    }

    class ParticipantsScreen {
        +ParticipantsScreen()
        +Widget build(BuildContext context)
        +Future fetchParticipants()
    }

    class EventosScreen {
        +EventosScreen()
        +Widget build(BuildContext context)
        +Future fetchEvents()
    }

    class EventsListScreen {
        +EventsListScreen()
        +Widget build(BuildContext context)
        +Future fetchEvents()
    }

    class Equipo {
        +String id
        +String nombre
        +String detalle
        +List participants
        +factory Equipo.fromJson(Map json)
    }

    class Participant {
        +String id
        +String nombre
        +String detalle
        +String equipoId
        +factory Participant.fromJson(Map json)
    }

    class Evento {
        +String id
        +String nombre
        +String fechainicio
        +String fechaTermino
        +String facultad
        +factory Evento.fromJson(Map json)
    }

    MyApp --> MyHomePage : Uses
    MyHomePage --> AuthService : Uses
    MyHomePage --> MenuScreen : Navigates to
    AuthService --> EquiposScreen : Navigates to
    AuthService --> ParticipantsScreen : Navigates to
    AuthService --> EventosScreen : Navigates to
    MenuScreen --> EquiposScreen : Navigates to
    MenuScreen --> ParticipantsScreen : Navigates to
    MenuScreen --> EventosScreen : Navigates to
    MenuScreen --> EventsListScreen : Navigates to
    EquiposScreen --> Equipo : Uses
    ParticipantsScreen --> Participant : Uses
    EventosScreen --> Evento : Uses
    EventsListScreen --> Evento : Uses
```

1. Diagrama de Base de Datos

1. Vista de Implementación: (vista de desarrollo)

1. Diagrama de Arquitectura de Software

![image](https://github.com/user-attachments/assets/00f1ef72-ae61-4371-9555-74a416239755)


![image](https://github.com/user-attachments/assets/77b0eedd-5379-44b2-a606-96b3a728fbbc)


1. Diagrama	de	Arquitectura	del	Sistema	(diagrama	de componentes)

![image](https://github.com/user-attachments/assets/51f475da-95e6-42f0-9871-5fa597be15ed)


1. Vista de Procesos:

3\.4.1.	Diagrama	de	Procesos	del	Sistema	(diagrama	de actividades)

1. Visto de Despliegue: (vista física)

3\.5.1 Diagrama de Despliegue

Para mas informacion consultar el siguiente repositorio: https://github.com/UPT-FAING-EPIS/proyecto-si8811a-2024-ii-u1-desarrollo-api-back

![image](https://github.com/user-attachments/assets/171f1b04-28a9-4972-9daa-6e4f546d7582)






1. ## **Atributos de Calidad del Software**

Escenario de Funcionalidad:

| Item | Descripcion|
|------------|-------------------------------------------------------------------------|
| Fuente     | Usuario                                                                 |
| Estímulo   | Necesidad de inscribir equipos, consultar información, visualizar ubicaciones y puntajes |
| Artefacto  | Aplicativo móvil (aplicación o software móvil)                           |
| Entorno    | Entorno digital                                                         |
| Respuesta  | El sistema debe permitir la inscripción de equipos, consulta de actividades, visualización de datos, y seguimiento |
| Medición   | Evaluar si la app permite registrar equipos, mostrar actividades, ubicaciones, y estadísticas correctamente y sin errores |



Escenario de Usabilidad:

| Item | Descripcion|
|------------|-------------------------------------------------------------------------|
| Fuente     | Usuario                                                                 |
| Estímulo   |Necesidad de navegar la app de manera intuitiva|
| Artefacto  | Aplicativo móvil (aplicación o software móvil)                           |
| Entorno    | Entorno digital                                                         |
| Respuesta |El sistema debe ser fácil de navegar, con menús y opciones claras y accesibles.|
| Medición   |Evaluar si los usuarios sin experiencia técnica pueden completar tareas sin dificultad.|


Escenario de Confiabilidad:

| Item | Descripcion|
|------------|-------------------------------------------------------------------------|
| Fuente     | Usuario                                                                 |
| Estímulo   |Necesidad de realizar registros, consultas y actualizaciones sin errores|
| Artefacto  | Aplicativo móvil (aplicación o software móvil)                           |
| Entorno    | Condiciones de evento en tiempo real, con múltiples usuarios activos|
| Respuesta |El sistema debe registrar y consultar datos sin fallos, incluso en momentos de alta carga de usuarios|
| Medición   |Medir la tasa de errores en el registro, consulta y actualización de datos durante el evento|

Escenario de Rendimiento:

Escenario de Mantenibilidad:

