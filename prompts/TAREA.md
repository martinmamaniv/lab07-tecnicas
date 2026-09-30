# Tarea: Mi prompt avanzado

## Tarea elegida

Diseño de arquitectura e implementacion de un controlador REST API para la gestion de productos en Spring Boot (Java).

## Version 1: prompt basico

```text
Crea una API REST de productos en Java.
```
- *​Técnica agregada:* Ninguna (prompt directo sin estructura).
- *Por qué:* Para evaluar el resultado predeterminado de la IA sin ninguna restricción ni contexto específico.
- *Resultado:* La IA genera un solo archivo de controlador básico con métodos incompletos, sin DTOs, sin manejo de errores y con endpoints no estandarizados.
## Version 2

```text
<rol>Actúa como desarrollador Backend Senior especializado en Spring Boot.</rol>
<tarea>Diseña un controlador REST API completo para gestionar el CRUD de productos.</tarea>
<formato>Código Java limpio con anotaciones de Spring Boot y comentarios breves.</formato>
```
- *​Técnica agregada:* Role prompting y Prompt estructurado.
- *Por qué:* Para delimitar la especialidad técnica del modelo y estructurar las instrucciones con etiquetas delimitadoras.
- *Resultado:* Entrega la clase ProductoController usando anotaciones de Spring (@RestController, @GetMapping, etc.), pero los métodos no manejan validaciones de entrada ni respuestas HTTP estandarizadas con DTOs.

## Version 3: prompt final

```text
<rol>Actúa como desarrollador Backend Senior experto en Spring Boot y buenas prácticas REST API.</rol>

<contexto>
Estamos construyendo el microservicio de catálogo de productos para una tienda de comercio electrónico en Java 17.
</contexto>

<tarea>
Diseña la capa web (Controller) para el recurso /api/v1/productos. Piensa paso a paso en el diseño antes de programar:
1. Define los endpoints HTTP con sus métodos y códigos de estado.
2. Crea el DTO de entrada con validaciones.
3. Implementa el controlador con inyección de dependencias.
</tarea>

<ejemplos>
Entrada: POST /api/v1/productos con body { "nombre": "Teclado", "precio": 45.50 }
Salida esperada: 201 Created con body { "id": 1, "nombre": "Teclado", "precio": 45.50 }

Entrada: GET /api/v1/productos/999 (id inexistente)
Salida esperada: 404 Not Found
</ejemplos>

<formato>
Presenta primero la tabla de endpoints definida y luego las clases Java correspondientes.
</formato>

<autocrítica>
Al finalizar, revisa si el controlador incluye validación de campos obligatorios con @Valid y si maneja excepciones globales para IDs no encontrados.
</autocrítica>
```
- *​Técnica agregada:* Chain of Thought, Few-shot y Autocrítica.
- *Por qué:* Para obligar a la IA a planificar los contratos de la API antes de codificar, asegurar el uso de códigos de estado HTTP correctos mediante ejemplos y verificar la seguridad y validación del payload enviado.
- *Resultado:* La IA genera una tabla clara de endpoints, crea la clase ProductoRequestDTO con validaciones de Hibernate (@NotNull, @Positive), el controlador ProductoController inyectando el servicio, y aplica la autocrítica agregando un @ExceptionHandler para respuestas 404.

## Tecnicas usadas en el prompt final

| Técnica | Parte del Prompt Final donde se aplica |
|---------|----------------------------------------|
| Role Prompting | <rol>Actúa como desarrollador Backend Senior experto en Spring Boot...</rol> |
| Prompt Estructurado | Uso de etiquetas delimitadoras <rol>, <contexto>, <tarea>, <ejemplos>, <formato>, <autocrítica> |
| Chain of Thought | Piensa paso a paso en el diseño antes de programar... dentro de <tarea> |
| Few-Shot | Bloque <ejemplos> definiendo contratos de peticiones HTTP y códigos de respuesta |
| Autocrítica | Bloque <autocrítica> solicitando revisión de validaciones con @Valid y manejo de excepciones |

## Evaluacion del resultado

| Criterio de Evaluación | Cumple (Sí / No) |
|------------------------|------------------|
| ¿Cumple con el rol asignado de desarrollador backend senior? | Sí |
| ¿Aplica convenciones REST y códigos de estado HTTP correctos? | Sí |
| ¿Muestra el desglose de endpoints antes de entregar el código? | Sí |
| ¿Aplica la autocrítica incluyendo validaciones y manejo de errores? | Sí |

## Por que elegi estas tecnicas
Elegí *Role Prompting* y *Prompt Estructurado* para que la IA responda como un programador senior y organice el contenido claramente. La técnica *Few-Shot* sirvió para mostrar el formato exacto de las respuestas HTTP que quería recibir. Con *Chain of Thought* logré que primero ordene los endpoints antes de programar, y la *Autocrítica* ayudó a revisar que no faltara ninguna validación importante en el código.