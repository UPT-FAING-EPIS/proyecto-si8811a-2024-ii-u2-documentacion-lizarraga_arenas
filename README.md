# Proyecto Sistema Web para los Juegos Florales UPT

## 1. Introducción

### Propósito (Diagrama 4+1)
El propósito de la plataforma web es ofrecer una solución moderna, eficiente y responsiva para la gestión de los Juegos Florales. Basado en el modelo 4+1, este diseño incluye:
- **Vista Lógica**: Una interfaz dinámica desarrollada con React y Tailwind CSS.
- **Vista de Implementación**: Almacenamiento y escalabilidad mediante Amazon S3.
- **Vista de Procesos**: Integridad y disponibilidad de datos en tiempo real.
- **Vista Física**: Despliegue en la nube con recursos escalables.
- **Vista de Casos de Uso**: Gestión de datos eficiente para actividades de registro y consulta.

### Alcance
Incluye el diseño e implementación de:
- Interfaz moderna con React y Tailwind CSS.
- Backend robusto en Amazon S3, asegurando alta disponibilidad y seguridad.

### Definición, Siglas y Abreviaturas
| Sigla | Nombre                        | Definición                                                                                 |
|-------|-------------------------------|-------------------------------------------------------------------------------------------|
| CU    | Caso de Uso                   | Conjunto de eventos entre un actor y el sistema para completar un proceso.                |
| RF    | Requerimiento Funcional       | Interacciones entre el sistema y su entorno, como usuarios o procesos automáticos.        |
| RNF   | Requerimiento No Funcional    | Criterios que evalúan la operación del sistema más allá de sus comportamientos específicos.|

### Organización del Documento
1. **Introducción**: Propósito, alcance y conceptos clave del proyecto.
2. **Objetivos y Restricciones Arquitectónicas**: Detalle de requisitos funcionales y no funcionales.
3. **Representación de la Arquitectura del Sistema**: Diagramas de vistas del sistema.
4. **Atributos de Calidad del Software**: Escenarios de funcionalidad, usabilidad, rendimiento, entre otros.

---

## 2. Objetivos y Restricciones Arquitectónicas

### Requerimientos Funcionales
| ID   | Nombre                      | Descripción                                                                             | Prioridad |
|------|-----------------------------|-----------------------------------------------------------------------------------------|-----------|
| RF1  | Registro de Usuarios        | Permitir que los estudiantes se registren en la plataforma con sus datos personales.   | Alta      |
| RF2  | Inscripción en Actividades  | Inscribir a estudiantes en actividades de los Juegos Florales.                         | Alta      |
| RF3  | Configuración de Eventos    | Organizar eventos y categorías en la plataforma.                                       | Alta      |
| RF4  | Publicación del Cronograma  | Mostrar cronogramas de actividades en la plataforma.                                   | Media     |
| RF5  | Evaluación de Actividades   | Los jueces evalúan actividades y envían observaciones.                                 | Alta      |
| RF6  | Registro de Puntajes        | Permitir a los organizadores registrar puntajes y comentarios.                         | Alta      |
| RF7  | Consulta de Resultados      | Consultar resultados en tiempo real.                                                  | Alta      |

### Requerimientos No Funcionales – Atributos de Calidad
| ID   | Nombre             | Descripción                                                                   | Prioridad |
|------|--------------------|-------------------------------------------------------------------------------|-----------|
| RNF1 | Usabilidad         | La plataforma debe ser intuitiva y accesible.                                | Alta      |
| RNF2 | Escalabilidad      | Soporte para múltiples usuarios simultáneamente.                             | Alta      |
| RNF3 | Seguridad          | Protección de datos personales y cumplimiento de normativas.                 | Alta      |
| RNF4 | Tiempo de Respuesta| Las operaciones principales deben realizarse en menos de 10 segundos.        | Alta      |
| RNF5 | Disponibilidad     | Disponibilidad mínima del 99.5%.                                             | Media     |

---

## 3. Representación de la Arquitectura del Sistema

### Vista de Caso de Uso

![image](https://github.com/user-attachments/assets/03e93043-113e-441c-9e8e-25ab744315b7)


### Vista Lógica
- **Diagrama de Subsistemas (Paquetes)**: Representa los módulos principales del sistema.

![image](https://github.com/user-attachments/assets/ae187422-a72c-4fce-ae1c-1c9ebaee890e)


- **Diagrama de Secuencia (Vista de Diseño)**: Muestra el flujo de interacciones entre componentes del sistema.

![image](https://github.com/user-attachments/assets/6b206c96-25a4-4bec-a22e-d28c8093a088)


- **Diagrama de Colaboración (Vista de Diseño)**: Describe cómo interactúan los objetos para completar una tarea.

```mermaid
flowchart LR
    UI[":InterfazUsuario"]
    Auth[":Autenticacion"]
    EG[":GestorEventos"]
    TG[":GestorEquipos"]
    PG[":GestorParticipantes"]
    DB[":BaseDatos"]

    UI <--> |"1: autenticarUsuario()"| Auth
    Auth <--> |"2: validarCredenciales()"| DB
    
    UI <--> |"3: gestionarEvento()"| EG
    EG <--> |"4: CRUD eventos"| DB
    
    UI <--> |"5: gestionarEquipo()"| TG
    TG <--> |"6: CRUD equipos"| DB
    
    UI <--> |"7: gestionarParticipante()"| PG
    PG <--> |"8: CRUD participantes"| DB
    
    EG <--> |"9: asociar()"| TG
    TG <--> |"10: asignar()"| PG

    classDef interface fill:#f9f9f9,stroke:#333,stroke-width:2px;
    classDef controller fill:#dbeaff,stroke:#0066cc;
    classDef database fill:#ffe6cc,stroke:#ff9933;
    
    class UI interface;
    class Auth,EG,TG,PG controller;
    class DB database;
```

- **Diagrama de Objetos**: Representa instancias específicas de clases en un momento dado.

```mermaid
classDiagram
    class admin_Usuario {
        +id: 1
        +nombre: Juan Admin
        +email: admin@evento.com
        +rol: ADMINISTRADOR
    }

    class torneoPadel_Evento {
        +id: 1
        +nombre: Torneo Padel 2024
        +descripcion: Torneo amateur
        +fecha: 2024-05-15
        +ubicacion: Club Deportivo
        +estado: ACTIVO
    }

    class equipo1_Equipo {
        +id: 1
        +nombre: Los Campeones
        +categoria: Amateur
    }

    class equipo2_Equipo {
        +id: 2
        +nombre: Padel Stars
        +categoria: Amateur
    }

    class participante1_Participante {
        +id: 1
        +nombre: Ana López
        +email: ana@mail.com
        +telefono: 123456789
    }

    class participante2_Participante {
        +id: 2
        +nombre: Carlos Ruiz
        +email: carlos@mail.com
        +telefono: 987654321
    }

    class inscripcion1_Inscripcion {
        +id: 1
        +fechaInscripcion: 2024-04-01
        +estado: CONFIRMADA
    }

    admin_Usuario --> torneoPadel_Evento : gestiona
    torneoPadel_Evento --> equipo1_Equipo : contiene
    torneoPadel_Evento --> equipo2_Equipo : contiene
    equipo1_Equipo --> participante1_Participante : tiene
    equipo2_Equipo --> participante2_Participante : tiene
    participante1_Participante --> inscripcion1_Inscripcion : realiza
```

- **Diagrama de Clases**: Describe las entidades y relaciones clave.

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

- **Diagrama de Base de Datos (Relacional o No Relacional)**: Representa el modelo de datos utilizado por el sistema.

```mermaid
erDiagram
    USUARIOS {
        int id PK
        string nombre
        string email
        string password
        string rol
        datetime created_at
        datetime updated_at
    }

    EVENTOS {
        int id PK
        string nombre
        string descripcion
        datetime fecha
        string ubicacion
        string estado
        int admin_id FK
        datetime created_at
    }

    EQUIPOS {
        int id PK
        string nombre
        string categoria
        int evento_id FK
        datetime created_at
    }

    PARTICIPANTES {
        int id PK
        int usuario_id FK
        string telefono
        string estado
        datetime created_at
    }

    EQUIPO_PARTICIPANTE {
        int equipo_id PK,FK
        int participante_id PK,FK
        datetime fecha_union
    }

    INSCRIPCIONES {
        int id PK
        int evento_id FK
        int participante_id FK
        datetime fecha_inscripcion
        string estado
        string tipo_pago
    }

    USUARIOS ||--o{ EVENTOS : "administra"
    EVENTOS ||--o{ EQUIPOS : "tiene"
    EQUIPOS ||--o{ EQUIPO_PARTICIPANTE : "contiene"
    PARTICIPANTES ||--o{ EQUIPO_PARTICIPANTE : "pertenece"
    EVENTOS ||--o{ INSCRIPCIONES : "tiene"
    PARTICIPANTES ||--o{ INSCRIPCIONES : "realiza"
    USUARIOS ||--|| PARTICIPANTES : "es"
```

### Vista de Implementación (Vista de Desarrollo)
- **Diagrama de Arquitectura de Software (Paquetes)**: Detalla los módulos y su interacción.

![image](https://github.com/user-attachments/assets/bf54624e-453a-44e7-bac3-92d35962670b)

- **Diagrama de Componentes**: Relación entre frontend y backend.

![image](https://github.com/user-attachments/assets/7ae71b1c-3a8f-4958-8453-a56af30ee305)


### Vista de Procesos
- **Diagrama de Procesos del Sistema (Diagrama de Actividad)**: Muestra el flujo de procesos clave como inscripción, evaluación y consulta de resultados.

![image](https://github.com/user-attachments/assets/af6ebcdb-2c7c-4faa-b095-8f4fe8c3768a)


### Vista de Despliegue (Vista Física)
- **Diagrama de Despliegue**: Representa cómo los componentes están alojados en la infraestructura en la nube.

![image](https://github.com/user-attachments/assets/1f0e1ec5-4b3f-4ef7-a6cf-3ae70d895435)


---

## 4. Atributos de Calidad del Software

| Escenario           | Descripción                                                                                     |
|---------------------|-------------------------------------------------------------------------------------------------|
| **Funcionalidad**   | Los usuarios deben interactuar con el sistema sin errores en tareas críticas como registro y consulta. |
| **Usabilidad**      | La interfaz debe ser intuitiva y permitir que un usuario sin experiencia la utilice en menos de 5 minutos.|
| **Confiabilidad**   | El sistema debe garantizar la integridad y disponibilidad constante de los datos.               |
| **Rendimiento**     | Manejo de múltiples usuarios sin afectar tiempos de respuesta.                                  |
| **Escalabilidad**   | Aceptar incrementos en la cantidad de usuarios sin degradar el rendimiento.                     |
| **Seguridad**       | Implementar encriptación de datos y protección contra accesos no autorizados.                   |

---
