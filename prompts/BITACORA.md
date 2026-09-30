# Bitacora de tecnicas avanzadas

Laboratorio 07: Tecnicas Avanzadas de Prompting.
Herramienta de IA usada: Gemini

## Ejercicio 2: Zero-shot, one-shot y few-shot

| Tipo | Aciertos (de 5) | Formato de la respuesta | Todas con el mismo formato (Si/No) |
|------|-----------------|-------------------------|------------------------------------|
| Zero-shot | 5/5 | Parrafo explicativo con viñetas | No |
| One-shot | 5/5 | Lista con breves explicaciones | No |
| Few-shot | 5/5 | "texto" -> Etiqueta directa y limpia | Si |

## Ejercicio 3: Chain of Thought

| Pedido | Respuesta de la IA | Muestra los pasos (Si/No) | Correcta (Si/No) |
|--------|--------------------|---------------------------|------------------|
| Directo | 318.60 | No | Si |
| Paso a paso | Muestra descuento (S/ 90.00), IGV (S/ 106.20) y total de 3 unidades (S/ 318.60) | Si | Si |

## Ejercicio 4: Role prompting

| Version | Vocabulario (sencillo/tecnico) | Usa ejemplos o codigo | A quien le sirve mas |
|---------|-------------------------------|-----------------------|----------------------|
| A. Sin rol | Moderado | Ejemplos teoricos generales | Publico general |
| B. Rol docente | Sencillo y cotidiano | Analogia de una caja etiquetada | Estudiantes sin experiencia previa |
| C. Rol senior | Tecnico (Stack, Heap, tipos) | Codigo en Java con declaracion y ambito | Desarrolladores y compañeros de equipo |

## Ejercicio 5: Descomposicion

- *Paso 1:* Listo los 5 requisitos principales (Gestion de Productos, Control de Stock, Registro de Ventas, Alertas y Reportes).
- *Paso 2:* Diseno las clases Producto, Inventario y Venta especificando atributos y tipos de datos.
- *Paso 3:* Escribio el codigo de la clase Producto.java limpio con encapsulamiento, constructor y metodos get y set.
- *Paso 4:* Propuso 3 mejoras: validacion de datos en setters, metodo toString() e ID autoincremental.

Comparado con el pedido de una sola vez, la descomposicion permite revisar y ajustar la arquitectura antes de generar el codigo, obteniendo un resultado mucho mas preciso y ordenado.

## Ejercicio 6: Prompt estructurado y autocritica

```text
<rol>Actua como analista de pruebas de software.</rol>
<contexto>Login web con correo y contraseña. La cuenta se bloquea despues de 3 intentos fallidos.</contexto>
<tarea>Piensa paso a paso que puede fallar y escribe 6 casos de prueba.</tarea>
<formato>Tabla con las columnas: ID, escenario, datos de entrada, resultado esperado.</formato>

[Mensaje de autocritica]:
Revisa tu tabla: faltan casos limite como campos vacios, correo sin @ o contraseña con espacios? Agrega los que falten e indica cuales agregaste.
```

| Que revisar | Cumple (Si / No) |
|-------------|------------------|
| ¿Tiene las 4 columnas pedidas? | Si |
| ¿Incluye el bloqueo despues de 3 intentos? | Si |
| ¿Incluye casos con campos vacios? | Si |
| ¿Indica que casos agrego en la autocritica? | Si |
| ¿Hay algun caso repetido o que no tenga sentido? | No |
