---
title: "Los 4 pilares de la Programación Orientada a Objetos, explicados con ejemplos"
date: 2026-09-08T10:00:00-06:00
draft: false
description: "Encapsulamiento, herencia, polimorfismo y abstracción explicados con ejemplos sencillos en Java, tal como los vimos en clase de Programación Orientada a Objetos."
categorias: ["Programación Orientada a Objetos"]
tags: ["java", "poo", "oop"]
cover: "images/covers/poo-java.svg"
toc: true
---

Uno de los temas que más se repite en la carrera es POO, así que aquí va un resumen propio de los cuatro pilares, con ejemplos cortos en Java para no olvidarlos.

## 1. Encapsulamiento

Consiste en ocultar los datos internos de una clase y solo exponer lo necesario a través de métodos públicos (getters/setters).

```java
public class CuentaBancaria {
    private double saldo; // privado: nadie fuera de la clase lo toca directo

    public double getSaldo() {
        return saldo;
    }

    public void depositar(double monto) {
        if (monto > 0) {
            saldo += monto;
        }
    }
}
```

La idea es que nadie pueda poner `saldo = -500` directamente desde fuera; todo pasa por métodos que controlan las reglas de negocio.

## 2. Herencia

Permite que una clase reutilice atributos y comportamiento de otra clase "padre".

```java
class Vehiculo {
    protected String marca;

    public void arrancar() {
        System.out.println(marca + " está arrancando...");
    }
}

class Auto extends Vehiculo {
    private int numPuertas;
}
```

`Auto` hereda `marca` y `arrancar()` sin tener que reescribirlos.

## 3. Polimorfismo

Es la capacidad de que un mismo método se comporte distinto según la clase que lo implemente (sobreescritura / *override*).

```java
class Animal {
    public void hacerSonido() {
        System.out.println("El animal hace un sonido");
    }
}

class Perro extends Animal {
    @Override
    public void hacerSonido() {
        System.out.println("Guau guau");
    }
}

class Gato extends Animal {
    @Override
    public void hacerSonido() {
        System.out.println("Miau");
    }
}
```

```java
Animal[] animales = { new Perro(), new Gato() };
for (Animal a : animales) {
    a.hacerSonido(); // cada uno responde diferente
}
```

## 4. Abstracción

Se trata de modelar solo lo relevante de un objeto para el problema que se está resolviendo, ignorando los detalles innecesarios. En Java se apoya mucho en clases abstractas e interfaces:

```java
abstract class Figura {
    abstract double calcularArea();
}

class Circulo extends Figura {
    private double radio;

    Circulo(double radio) {
        this.radio = radio;
    }

    @Override
    double calcularArea() {
        return Math.PI * radio * radio;
    }
}
```

No necesitamos saber cómo calcula cada figura su área desde afuera, solo que **toda figura puede calcular un área**.

## Por qué importa esto en la práctica

Estos cuatro pilares no son solo teoría de examen: son la base de por qué los diagramas de clases (UML) se ven como se ven, y por qué en las actividades de clase nos piden separar responsabilidades entre clases en vez de meter toda la lógica en una sola.
