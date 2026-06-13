# Módulo 1: Introducción y Análisis de Algoritmos

Este documento proporciona una guía clara y estructurada sobre los conceptos fundamentales del análisis de algoritmos y las estructuras de datos, esenciales para el desarrollo de software eficiente y escalable.

---

## 1. ¿Qué son las estructuras de datos y por qué importan?

### Definición
Una **estructura de datos** es una forma particular de organizar, gestionar y almacenar datos en la memoria de una computadora para que puedan ser accedidos y modificados de manera eficiente. Ejemplos comunes incluyen arreglos (arrays), listas enlazadas, pilas (stacks), colas (queues), árboles (trees), grafos (graphs) y tablas hash.

### ¿Por qué importan?
1. **Eficiencia**: La elección correcta de una estructura de datos puede reducir drásticamente el tiempo de ejecución (complejidad temporal) y el uso de memoria (complejidad espacial) de un programa.
2. **Escalabilidad**: Un algoritmo que funciona bien con 100 elementos puede colapsar con 1.000.000 si la estructura de datos subyacente no es la adecuada. Las buenas estructuras de datos permiten que el software crezca sin degradar su rendimiento.
3. **Abstracción y Reutilización**: Permiten a los desarrolladores trabajar con conceptos de alto nivel (como "insertar", "buscar" o "eliminar") sin preocuparse por los detalles de bajo nivel de la gestión de memoria en cada operación.
4. **Base de los Algoritmos**: Los algoritmos y las estructuras de datos son inseparables. Un algoritmo es el *procedimiento* (la receta), y la estructura de datos son los *ingredientes* organizados. Como dijo el pionero de la informática Niklaus Wirth: *"Algoritmos + Estructuras de Datos = Programas"*.

---

## 2. Notación Big O: Complejidad Temporal y Espacial

La **Notación Big O** ($O$) es una notación matemática utilizada en ciencias de la computación para describir el comportamiento límite (asintótico) de una función. En la práctica, nos dice cómo escala el rendimiento de un algoritmo a medida que el tamaño de la entrada ($n$) crece hacia el infinito, ignorando constantes y términos de menor orden.

### Complejidad Temporal
Mide la cantidad de operaciones (o tiempo) que un algoritmo necesita para ejecutarse en función del tamaño de la entrada $n$. No mide segundos reales, sino el *número de pasos* relativos.

| Notación Big O | Nombre | Descripción | Ejemplo Común |
| :--- | :--- | :--- | :--- |
| $O(1)$ | Constante | El tiempo de ejecución no cambia, sin importar el tamaño de $n$. | Acceder a un elemento en un arreglo por su índice. |
| $O(\log n)$ | Logarítmica | El tiempo crece lentamente. Cada paso reduce el problema a la mitad. | Búsqueda binaria en un arreglo ordenado. |
| $O(n)$ | Lineal | El tiempo crece proporcionalmente al tamaño de la entrada. | Búsqueda lineal en un arreglo no ordenado. |
| $O(n \log n)$ | Log-lineal | Típico de algoritmos de ordenamiento eficientes. | Merge Sort, Quick Sort (caso promedio), Heap Sort. |
| $O(n^2)$ | Cuadrática | El tiempo crece al cuadrado. Común en bucles anidados. | Bubble Sort, Selection Sort, comparar todos los pares. |
| $O(2^n)$ | Exponencial | El tiempo se duplica con cada elemento añadido. Extremadamente ineficiente para $n$ grande. | Resolución de la Torre de Hanoi, fuerza bruta en subconjuntos. |

### Complejidad Espacial
Mide la cantidad de **memoria adicional** (RAM) que un algoritmo necesita para ejecutarse, en función del tamaño de la entrada $n$. 
* **Nota**: No cuenta la memoria que ocupa la entrada en sí, sino la memoria *extra* asignada durante la ejecución (variables auxiliares, estructuras de datos temporales, profundidad de la pila de llamadas en recursión).
* *Ejemplo*: Un algoritmo que ordena un arreglo "in-place" (como Heap Sort) tiene una complejidad espacial de $O(1)$ o $O(\log n)$ (por la recursión), mientras que Merge Sort requiere $O(n)$ de espacio adicional para los arreglos temporales.

---

## 3. Análisis de mejor caso, peor caso y caso promedio

Para entender completamente el rendimiento de un algoritmo, no basta con un solo número. Debemos evaluar cómo se comporta bajo diferentes escenarios de entrada.

### 1. Mejor Caso (Best Case)
* **Definición**: El escenario más favorable posible para el algoritmo. Representa el límite inferior de su rendimiento.
* **Notación**: A menudo asociado con la notación **Omega ($\Omega$)**.
* **Utilidad**: Sirve para saber si existe alguna condición bajo la cual el algoritmo es extremadamente rápido, aunque no es la métrica más confiable para garantizar el rendimiento.

### 2. Peor Caso (Worst Case)
* **Definición**: El escenario más desfavorable posible. Representa el límite superior del tiempo o espacio que el algoritmo consumirá.
* **Notación**: Asociado con la notación **Big O ($O$)**.
* **Utilidad**: Es la métrica **más importante** en sistemas críticos (ej. médicos, aeroespaciales, financieros), ya que proporciona una *garantía* de que el algoritmo nunca tardará más de ese tiempo, sin importar la entrada.

### 3. Caso Promedio (Average Case)
* **Definición**: El rendimiento esperado del algoritmo sobre todas las posibles entradas de tamaño $n$, asumiendo una distribución de probabilidad específica (generalmente uniforme).
* **Notación**: A menudo asociado con la notación **Theta ($\Theta$)** cuando el mejor y peor caso convergen, o se expresa como valor esperado $E[T(n)]$.
* **Utilidad**: Refleja el comportamiento "típico" o "realista" del algoritmo en la práctica.

---

### Ejemplo Práctico: Búsqueda Lineal en un Arreglo

Imagina un algoritmo que busca un número $X$ en un arreglo no ordenado de $n$ elementos, revisando uno por uno desde el inicio.

| Escenario | Descripción | Complejidad Temporal |
| :--- | :--- | :--- |
| **Mejor Caso** | El elemento $X$ es el **primer** elemento del arreglo. El algoritmo lo encuentra en 1 paso. | $O(1)$ |
| **Peor Caso** | El elemento $X$ es el **último** elemento del arreglo, o **no existe** en el arreglo. El algoritmo debe revisar los $n$ elementos. | $O(n)$ |
| **Caso Promedio** | Asumiendo que $X$ tiene la misma probabilidad de estar en cualquier posición o de no estar, en promedio se revisarán $n/2$ elementos. Al descartar constantes en Big O, esto sigue siendo lineal. | $O(n)$ |

---

## Resumen
* Las **estructuras de datos** son la base para organizar la información de manera que los algoritmos puedan procesarla eficientemente.
* La **Notación Big O** nos permite clasificar y comparar algoritmos ignorando detalles de hardware, enfocándonos en cómo escalan con datos grandes ($n \to \infty$).
* Evaluar el **mejor, peor y promedio caso** nos da una visión completa: el peor caso nos da garantías de seguridad, el mejor caso nos muestra el potencial óptimo, y el caso promedio nos dice qué esperar en el día a día.

> 💡 **Consejo para desarrolladores**: Siempre prioriza optimizar el *peor caso* y el *caso promedio* al diseñar sistemas. El mejor caso es interesante teóricamente, pero rara vez define la robustez de una aplicación en producción.
