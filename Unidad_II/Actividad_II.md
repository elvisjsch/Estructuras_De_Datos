# 📑 Actividad Evaluativa 2: Caso de Estudio y Simulación de Estructuras Lineales

**Asignatura:** Estructuras de Datos  
**Ponderación:** [Insertar %]  
**Tipo de Entrega:** Informe Técnico + Archivo de Código Fuente  
**Modo:** [Individual / Parejas]  

---

## 🎯 Objetivo de la Actividad
Aplicar los conceptos de estructuras de datos lineales (Arreglos, Listas Enlazadas, Pilas o Colas) en la resolución de un problema del mundo real, justificando la elección de la estructura mediante el análisis de sus ventajas computacionales y simulando su comportamiento a través de código funcional.

---

## 📋 Instrucciones del Reto

Para esta actividad, no se te dará una estructura fija. Deberás seleccionar **UNO** de los siguientes escenarios de backend, analizarlo y desarrollar la solución requerida:

### Escenarios Disponibles (Selecciona solo uno):
* **Escenario A (Gestión de Tráfico Web):** Diseñar el backend para un servidor que procesa peticiones de usuarios hacia una base de datos. Si el servidor se satura, las peticiones deben esperar su turno en orden de llegada.
* **Escenario B (Módulo "Deshacer" - Undo):** Diseñar el editor de texto o módulo de edición de un sistema administrativo donde cada acción o cambio realizado por el usuario pueda revertirse cronológicamente (desde el más reciente al más antiguo).
* **Escenario C (Historial Dinámico de Sesiones):** Diseñar un sistema que almacene el historial de navegación de un usuario en una aplicación de escritorio, permitiendo insertar nuevos registros de forma ilimitada sin reservar un tamaño fijo de memoria de antemano.

---

## 🛠️ Requisitos del Entregable

El proyecto debe constar de dos partes fundamentales integradas en su entrega:

### Parte 1: Documentación del Caso (Informe)
1. **Explicación del Contexto:** Describe el escenario seleccionado con tus propias palabras y detalla cuáles son los datos que entran al sistema y qué operaciones críticas se deben realizar (insertar, eliminar, consultar).
2. **Justificación de la Estructura:** Explica detalladamente **por qué elegiste esa estructura de datos específica sobre las demás**. Debes mencionar por qué no funcionaría bien usar otra (por ejemplo, por qué una Pila no sirve para el Escenario A, o por qué un Arreglo Estático fallaría en el Escenario C).
3. **Análisis de Eficiencia:** Detalla la complejidad temporal en Notación Big O de las operaciones principales de tu estructura elegida (Ej: Inserción $O(1)$, Eliminación $O(1)$, etc.).

### Parte 2: Simulación en Código
* Desarrollar un programa en **[Java / Python / Lenguaje del curso]** que simule el comportamiento del sistema elegido.
* **Restricción Técnica:** No está permitido usar las clases utilitarias del lenguaje (como `java.util.Stack` o `java.util.LinkedList`). **El estudiante debe codificar e implementar la estructura desde cero** usando nodos o arreglos dinámicos según corresponda, demostrando que comprende su funcionamiento interno.
* El código debe incluir un método `main` o una interfaz de consola sencilla que muestre cómo se insertan datos, cómo se procesan/eliminan y cómo queda el estado de la estructura en memoria.

---

## 📐 Rúbrica de Evaluación (Total: 20 Puntos)

| Criterio | Excelente (5 pts) | Aceptable (3.5 pts) | Requiere Mejora (2 pts) | No Cumple (0 pts) |
| :--- | :--- | :--- | :--- | :--- |
| **1. Comprensión del Contexto** | Explica de forma impecable el flujo de datos del escenario elegido, identificando con precisión los requerimientos del sistema. | Explica el contexto pero la descripción del flujo de datos es genérica o pasa por alto alguna operación crítica. | La descripción del problema es confusa, limitándose a copiar el enunciado sin aportar análisis propio. | No define el contexto ni el escenario sobre el cual trabajará. |
| **2. Justificación Técnica** | Justifica sólidamente la elección de la estructura basándose en ventajas computacionales y contrasta por qué las otras estructuras fallarían. | Elige la estructura correcta, pero su justificación es débil o no argumenta por qué descartó las demás opciones. | Elige una estructura ineficiente para el problema o los argumentos de elección carecen de base teórica en estructuras de datos. | No presenta ninguna justificación teórica de la estructura seleccionada. |
| **3. Implementación del Código** | El código está correctamente estructurado, implementa la estructura desde cero sin librerías prohibidas y simula el escenario con éxito. | El código funciona y simula el escenario, pero utiliza colecciones nativas del lenguaje o tiene errores menores en la lógica de punteros/nodos. | El código no compila, está incompleto en sus operaciones base o la simulación no coincide con el escenario elegido. | No entrega código fuente o el código es un plagio evidente que no corresponde al problema. |
| **4. Buenas Prácticas y Estilo** | El código está limpio, documentado con comentarios pertinentes y las variables/clases siguen una nomenclatura profesional (CamelCase o snake_case). | El código funciona bien pero carece por completo de comentarios explicativos o la nomenclatura de las variables es confusa. | El código es desorganizado, difícil de leer, no tiene estructura limpia y carece de documentación técnica. | Entrega un archivo de código ilegible o sin ningún tipo de orden estructurado. |

---
💡 **Consejo del Mentor:** En el desarrollo backend, escribir código que funcione es solo el 50% del trabajo; el otro 50% es saber explicarle al equipo de arquitectura por qué tu solución es la más óptima para la memoria y el procesador del servidor. ¡Mucho éxito construyendo sus soluciones desde cero!
