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

---

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
#### Caso de Uso: Registrar Eventos
- **Actor Principal**: Organizador.
- **Flujo Normal**:
  1. El organizador accede a la sección de eventos.
  2. Completa el formulario del evento.
  3. El sistema valida y registra el evento.

#### Caso de Uso: Consultar Resultados
- **Actor Principal**: Estudiante.
- **Flujo Normal**:
  1. El estudiante selecciona la categoría deseada.
  2. Visualiza los resultados en una tabla.
  3. Puede descargar un reporte en PDF.

#### Caso de Uso: Evaluar Actividades
- **Actor Principal**: Juez.
- **Flujo Normal**:
  1. El juez selecciona la actividad a evaluar.
  2. Ingresa puntajes y comentarios.
  3. El sistema guarda las evaluaciones.

---

## Conclusiones
La plataforma representa un avance significativo en la gestión de los Juegos Florales, mejorando la transparencia, participación y eficiencia. Su diseño moderno asegura un desempeño óptimo, mientras que su escalabilidad permite adaptarse a futuras necesidades.
