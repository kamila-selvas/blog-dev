---
title: "Listas enlazadas: la base de las estructuras de datos dinámicas"
date: 2026-09-15T10:00:00-06:00
draft: false
description: "Qué son las listas enlazadas, por qué existen y cómo se implementan en Java, con ejemplos comentados a partir de lo visto en clase de Estructura de Datos."
categorias: ["Estructura de Datos"]
tags: ["java", "estructuras-de-datos", "listas-enlazadas", "poo"]
cover: "images/covers/listas-enlazadas.svg"
toc: true
---

En la materia de **Estructura de Datos** empezamos a ver por qué los arreglos no siempre son la mejor opción para guardar información, y ahí es donde entran las **listas enlazadas**. Aquí dejo mis notas de esta semana, con ejemplos en Java.

## ¿Por qué no usar solo arreglos?

Un arreglo tiene tamaño fijo: una vez declarado, no puedes hacerlo más grande sin crear uno nuevo y copiar los datos. Además, insertar un elemento al inicio implica recorrer y mover todo lo demás. Las listas enlazadas resuelven esto porque **crecen dinámicamente** y no necesitan memoria contigua.

## ¿Qué es un nodo?

Cada elemento de la lista es un **nodo**, y cada nodo guarda dos cosas: un dato y una referencia (o "liga") al siguiente nodo.

```java
class Nodo {
    int dato;
    Nodo siguiente;

    Nodo(int dato) {
        this.dato = dato;
        this.siguiente = null;
    }
}
```

## Implementando la lista

La lista solo necesita guardar una referencia a su primer nodo, la llamada **cabeza** (`head`).

```java
class ListaEnlazada {
    private Nodo cabeza;

    // Insertar al final de la lista
    public void agregar(int dato) {
        Nodo nuevo = new Nodo(dato);
        if (cabeza == null) {
            cabeza = nuevo;
            return;
        }
        Nodo actual = cabeza;
        while (actual.siguiente != null) {
            actual = actual.siguiente;
        }
        actual.siguiente = nuevo;
    }

    // Imprimir todos los elementos
    public void imprimir() {
        Nodo actual = cabeza;
        while (actual != null) {
            System.out.print(actual.dato + " -> ");
            actual = actual.siguiente;
        }
        System.out.println("null");
    }
}
```

## Complejidad: lo que hay que recordar para el examen

| Operación             | Arreglo | Lista enlazada |
|------------------------|:-------:|:---------------:|
| Acceso por índice       | O(1)    | O(n)             |
| Inserción al inicio     | O(n)    | O(1)             |
| Inserción al final      | O(1)*   | O(n)             |
| Búsqueda                | O(n)    | O(n)             |

> \* En un arreglo dinámico (como `ArrayList`), la inserción al final es O(1) amortizado.

## Conclusión

Las listas enlazadas no siempre son "mejores" que los arreglos, son una herramienta distinta: convienen cuando vas a insertar y eliminar mucho, y no tanto cuando necesitas acceso aleatorio rápido por índice. La siguiente clase toca listas doblemente enlazadas, así que voy a actualizar este post cuando las veamos.
