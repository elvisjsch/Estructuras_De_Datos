# Módulo 2: Estructuras de Datos Lineales

Este módulo explora las estructuras de datos donde los elementos se organizan de forma secuencial (uno detrás de otro). Entender sus fortalezas y debilidades es clave para elegir la herramienta adecuada para cada problema.

---

## 1. Arreglos (Arrays) y Listas Dinámicas

### Definición
Un **arreglo** es una colección de elementos del mismo tipo almacenados en posiciones de memoria **contiguas**. En lenguajes de alto nivel como Python, esto se implementa como una **Lista Dinámica** (Dynamic Array), que puede crecer o disminuir de tamaño automáticamente.

### Complejidad de Operaciones
| Operación | Complejidad Temporal | Explicación |
| :--- | :---: | :--- |
| **Acceso por índice** | $O(1)$ | La memoria es contigua, el cálculo de la dirección es matemático e inmediato. |
| **Búsqueda de un valor** | $O(n)$ | En el peor caso, hay que recorrer todo el arreglo. |
| **Inserción al final** | $O(1)$ *amortizado* | Generalmente es $O(1)$. Ocasionalmente, si el arreglo está lleno, debe redimensionarse (copiar todo a un nuevo espacio), lo que toma $O(n)$, pero el promedio sigue siendo $O(1)$. |
| **Inserción/Eliminación al inicio o medio** | $O(n)$ | Requiere desplazar todos los elementos siguientes una posición a la derecha o izquierda. |

---

## 2. Listas Enlazadas (Linked Lists)

### Definición
Una **lista enlazada** es una colección de **nodos**, donde cada nodo contiene dos cosas:
1. El **dato** en sí.
2. Una **referencia (puntero)** al siguiente nodo de la secuencia.

A diferencia de los arreglos, **no requieren memoria contigua**. Esto elimina la necesidad de desplazar elementos al insertar o eliminar, pero sacrifica el acceso aleatorio rápido.

### Tipos Principales
* **Simplemente enlazada:** Cada nodo apunta solo al siguiente. El último apunta a `null` (o `None`).
* **Doblemente enlazada:** Cada nodo tiene un puntero al siguiente y otro al anterior. Facilita el recorrido en ambas direcciones.
* **Circular:** El último nodo apunta de nuevo al primero, formando un bucle.

### Complejidad de Operaciones (Lista Simplemente Enlazada)
| Operación | Complejidad Temporal | Explicación |
| :--- | :---: | :--- |
| **Inserción al inicio** | $O(1)$ | Solo se actualizan dos punteros (el nuevo nodo y la cabeza de la lista). |
| **Inserción al final** | $O(n)$ o $O(1)$ | $O(n)$ si hay que recorrerla. $O(1)$ si se mantiene una referencia al último nodo (`tail`). |
| **Búsqueda** | $O(n)$ | No hay acceso por índice; hay que recorrer nodo por nodo desde el inicio. |
| **Eliminación** | $O(n)$ | Requiere buscar el nodo ($O(n)$) y luego actualizar el puntero del nodo anterior ($O(1)$). |

---

## 3. Pilas (Stacks)

### Definición
Una pila es una estructura de datos lineal que sigue el principio **LIFO** (*Last In, First Out* / Último en entrar, primero en salir). Imagina una pila de platos: solo puedes añadir o quitar el plato que está hasta arriba.

### Operaciones Básicas (Todas $O(1)$)
* `push(item)`: Añade un elemento a la cima de la pila.
* `pop()`: Elimina y devuelve el elemento de la cima.
* `peek()` o `top()`: Devuelve el elemento de la cima sin eliminarlo.
* `is_empty()`: Verifica si la pila está vacía.

### Aplicaciones Comunes
* Funcionalidad de "Deshacer" (Undo) en editores de texto.
* Gestión de llamadas a funciones y recursión (Call Stack).
* Evaluación de expresiones matemáticas (notación polaca inversa).
* Algoritmos de recorrido en profundidad (DFS - Depth First Search).

---

## 4. Colas (Queues)

### Definición
Una cola es una estructura de datos lineal que sigue el principio **FIFO** (*First In, First Out* / Primero en entrar, primero en salir). Imagina una fila de personas en un banco: el primero en llegar es el primero en ser atendido.

### Operaciones Básicas (Todas $O(1)$ con la implementación correcta)
* `enqueue(item)`: Añade un elemento al final de la cola.
* `dequeue()`: Elimina y devuelve el elemento del frente de la cola.
* `front()`: Devuelve el elemento del frente sin eliminarlo.
* `is_empty()`: Verifica si la cola está vacía.

### Aplicaciones Comunes
* Manejo de solicitudes en servidores web (colas de impresión, colas de mensajes como RabbitMQ/Kafka).
* Planificación de procesos en sistemas operativos.
* Algoritmos de recorrido en anchura (BFS - Breadth First Search) en grafos y árboles.

> ⚠️ **Nota crucial en Python**: Usar `list.pop(0)` para una cola es **$O(n)$** porque todos los elementos deben desplazarse. La forma correcta y eficiente ($O(1)$) de implementar una cola en Python es usando `collections.deque` (double-ended queue).

---

## Código Práctico en Python

A continuación, se presentan implementaciones limpias y comentadas de estas estructuras.

### 1. Lista Enlazada Simplemente Enlazada
```python
class Nodo:
    def __init__(self, dato):
        self.dato = dato
        self.siguiente = None  # Puntero al siguiente nodo

class ListaEnlazada:
    def __init__(self):
        self.cabeza = None
        self.tamaño = 0

    def insertar_al_inicio(self, dato):
        """Complejidad: O(1)"""
        nuevo_nodo = Nodo(dato)
        nuevo_nodo.siguiente = self.cabeza
        self.cabeza = nuevo_nodo
        self.tamaño += 1

    def insertar_al_final(self, dato):
        """Complejidad: O(n) si no hay referencia al final, O(1) si la hay."""
        nuevo_nodo = Nodo(dato)
        if self.cabeza is None:
            self.cabeza = nuevo_nodo
        else:
            actual = self.cabeza
            while actual.siguiente:  # Recorre hasta el último nodo
                actual = actual.siguiente
            actual.siguiente = nuevo_nodo
        self.tamaño += 1

    def eliminar(self, dato):
        """Complejidad: O(n) en el peor caso."""
        if self.cabeza is None:
            return

        # Si el elemento a eliminar es la cabeza
        if self.cabeza.dato == dato:
            self.cabeza = self.cabeza.siguiente
            self.tamaño -= 1
            return

        # Buscar el nodo anterior al que se quiere eliminar
        actual = self.cabeza
        while actual.siguiente and actual.siguiente.dato != dato:
            actual = actual.siguiente

        # Si se encontró el nodo
        if actual.siguiente:
            actual.siguiente = actual.siguiente.siguiente  # "Salta" el nodo eliminado
            self.tamaño -= 1

    def mostrar(self):
        elementos = []
        actual = self.cabeza
        while actual:
            elementos.append(str(actual.dato))
            actual = actual.siguiente
        print(" -> ".join(elementos) + " -> None")

# --- Prueba ---
lista = ListaEnlazada()
lista.insertar_al_final(10)
lista.insertar_al_inicio(5)
lista.insertar_al_final(20)
lista.mostrar()       # Salida: 5 -> 10 -> 20 -> None
lista.eliminar(10)
lista.mostrar()       # Salida: 5 -> 20 -> None
```

### 2. Pila (Stack)
```python
class Pila:
    def __init__(self):
        self.elementos = []  # Usamos una lista de Python como base

    def apilar(self, item):
        """O(1) amortizado"""
        self.elementos.append(item)

    def desapilar(self):
        """O(1) amortizado"""
        if self.esta_vacia():
            raise IndexError("No se puede desapilar de una pila vacía")
        return self.elementos.pop()  # pop() sin argumentos elimina el último

    def ver_cima(self):
        """O(1)"""
        if self.esta_vacia():
            return None
        return self.elementos[-1]

    def esta_vacia(self):
        return len(self.elementos) == 0

# --- Prueba ---
pila = Pila()
pila.apilar("Plato 1")
pila.apilar("Plato 2")
print(pila.ver_cima())      # Salida: Plato 2
print(pila.desapilar())     # Salida: Plato 2 (LIFO)
print(pila.desapilar())     # Salida: Plato 1
```

### 3. Cola (Queue) - Implementación Óptima
```python
from collections import deque

class Cola:
    def __init__(self):
        # deque está implementado en C como una lista doblemente enlazada,
        # garantizando O(1) para append y popleft.
        self.elementos = deque()

    def encolar(self, item):
        """O(1)"""
        self.elementos.append(item)

    def desencolar(self):
        """O(1)"""
        if self.esta_vacia():
            raise IndexError("No se puede desencolar de una cola vacía")
        return self.elementos.popleft()  # Elimina por la izquierda (el más antiguo)

    def ver_frente(self):
        """O(1)"""
        if self.esta_vacia():
            return None
        return self.elementos[0]

    def esta_vacia(self):
        return len(self.elementos) == 0

# --- Prueba ---
cola = Cola()
cola.encolar("Cliente A")
cola.encolar("Cliente B")
cola.encolar("Cliente C")
print(cola.ver_frente())      # Salida: Cliente A
print(cola.desencolar())      # Salida: Cliente A (FIFO)
print(cola.desencolar())      # Salida: Cliente B
```

---

## Resumen Comparativo para la Toma de Decisiones

| Estructura | Mejor para... | Evitar cuando... |
| :--- | :--- | :--- |
| **Arreglo / Lista Dinámica** | Acceso frecuente por índice, iteración secuencial, datos de tamaño conocido. | Necesitas insertar/eliminar frecuentemente al inicio o en el medio. |
| **Lista Enlazada** | Inserciones/eliminaciones frecuentes al inicio, tamaño de datos muy dinámico e impredecible. | Necesitas acceso aleatorio (por índice) o recorrer la estructura hacia atrás (a menos que sea doblemente enlazada). |
| **Pila (Stack)** | Revertir acciones, recursión, análisis sintáctico (parsing), DFS. | Necesitas acceder a elementos que no estén en la cima. |
| **Cola (Queue)** | Manejo de tareas en orden de llegada, buffers, BFS. | Necesitas priorizar elementos (para eso existe la *Cola de Prioridad* / Heap, que veremos en el Módulo 3). |

> 💡 **Consejo para desarrolladores**: En Python, la `list` nativa es increíblemente optimizada para actuar como Pila (`append` y `pop`). Sin embargo, **nunca** uses `list.pop(0)` o `list.insert(0, item)` para simular una Cola en código de producción, ya que degrada el rendimiento a $O(n)$. Usa siempre `collections.deque`.

---
