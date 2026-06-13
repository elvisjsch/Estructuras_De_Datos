# 📑 Actividad Evaluativa: Reto de Optimización Backend (Módulo 1)

**Asignatura:** Estructuras de Datos  
**Metodología:** Aprendizaje Basado en Proyectos (ABP) / Análisis de Casos  
**Ponderación:** [Insertar %]  
**Modo de entrega:** Documento PDF o Repositorio de GitHub (Markdown)  

---

## 🎯 Objetivo de la Actividad
Evaluar la capacidad del estudiante para analizar la eficiencia de un algoritmo, aplicar correctamente la Notación Big O y determinar el impacto del rendimiento en escenarios del mundo real (Mejor, Peor y Caso Promedio) antes de proceder a la codificación.

---

## 🏢 Escenario: El Sistema de Notificaciones de "FastDelivery"

Trabajas como Ingeniero de Software Backend para **FastDelivery**, una aplicación de entrega de comida a domicilio que está experimentando un crecimiento masivo. El sistema cuenta con una lista de usuarios activos ($n$). 

El equipo de marketing ha diseñado una función para buscar usuarios específicos en la base de datos local y enviarles un cupón de descuento. El algoritmo actual realiza una **búsqueda secuencial (lineal)** en la memoria del servidor.

### El Problema:
Con 1,000 usuarios ($n = 1,000$), el sistema funciona instantáneamente. Sin embargo, la empresa se va a expandir a nivel nacional y se espera que la lista crezca a **1,000,000 de usuarios** ($n = 1,000,000$). El servidor backend actual empieza a arrojar alertas de *Timeout* (tiempo de espera agotado) debido al uso excesivo de CPU.

---

## 🛠️ Tareas a Realizar

Los estudiantes deberán entregar un informe técnico que resuelva los siguientes tres puntos:

### Parte 1: Análisis del Algoritmo Actual (30%)
1. Identifica y explica cuál es la **Complejidad Temporal** en Notación Big O del algoritmo de búsqueda lineal actual.
2. Explica detalladamente qué significan los siguientes tres escenarios para **FastDelivery** con la arquitectura actual:
   * **Mejor Caso:** Describe qué tendría que ocurrir con el usuario buscado y cuál sería su Big O.
   * **Peor Caso:** Describe qué ocurre si el usuario no existe o es el último, y cuál sería su Big O.
   * **Caso Promedio:** Explica el comportamiento matemático esperado en un día común de operaciones.

### Parte 2: El Impacto de la Escalabilidad (30%)
Calcula el impacto del crecimiento de los datos rellenando la siguiente tabla predictiva de operaciones (asumiendo que en el peor caso, 1 operación elemental toma 1 microsegundo $\mu s$):

| Tamaño de Usuarios ($n$) | Operaciones en el Peor Caso | Tiempo Estimado (en $\mu s$ o segundos) |
| :--- | :--- | :--- |
| $n = 100$ | | |
| $n = 10,000$ | | |
| $n = 1,000,000$ | | |

*A partir de los resultados, redacta una conclusión técnica de por qué el servidor está fallando ahora que la empresa se expandió.*

### Parte 3: Propuesta de Solución e Impacto Espacial (40%)
Como Ingeniero de Sistemas, debes proponer una alternativa para mejorar la velocidad de búsqueda:
1. Si decides **ordenar la lista previamente** y aplicar un algoritmo de **Búsqueda Binaria**:
   * ¿Cuál sería la nueva complejidad temporal en el peor de los casos? ($O(\log n)$).
   * Justifica matemáticamente por qué esta solución salvaría al servidor del colapso con 1,000,000 de usuarios.
2. **Análisis de Complejidad Espacial:** Si para implementar esta mejora necesitas crear un arreglo auxiliar que duplique los datos en memoria, ¿cuál sería la complejidad espacial ($O$) de tu solución? ¿Qué riesgos comerciales o técnicos implicaría esto para el backend si el dinero para infraestructura es limitado?

---

## 📐 Criterios de Evaluación (Rúbrica)

| Criterio | Excelente (100%) | Lote Aceptable (70%) | Requiere Mejora (40%) |
| :--- | :--- | :--- | :--- |
| **Análisis de Complejidad (Big O)** | Identifica correctamente las complejidades temporales y espaciales usando la notación matemática adecuada ($O$). | Identifica las complejidades pero confunde los términos o confunde el peor caso con el promedio. | No identifica correctamente las complejidades de los algoritmos propuestos. |
| **Comprensión de Casos** | Describe con precisión los escenarios del mundo real (mejor, peor, promedio) aplicados al negocio de FastDelivery. | Describe los escenarios pero de forma muy teórica, sin conectarlos con el problema del negocio. | No distingue la diferencia entre el mejor, peor y caso promedio. |
| **Pensamiento Crítico y Solución** | Propone una solución viable, calcula correctamente el impacto de la escalabilidad y evalúa el costo de la memoria RAM. | Propone una solución pero falla en los cálculos matemáticos del crecimiento de $n$. | No propone soluciones viables o ignora el impacto de la complejidad espacial. |
| **Presentación y Formato** | Entrega un informe técnico impecable, estructurado en Markdown/PDF, con redacción profesional y sin errores. | El informe está completo pero carece de estructura clara o tiene múltiples errores ortográficos. | Entrega un documento desorganizado que no cumple con el formato de informe técnico. |

---
💡 **Consejo del Mentor:** Recuerden que en producción no optimizamos para que el código "se vea bonito", optimizamos para que la infraestructura soporte la carga del negocio. ¡Mucho éxito con el reto!
