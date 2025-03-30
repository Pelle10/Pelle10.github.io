---
title: 'Ejercicios UT1_PD4'
description: Ejercicios del UT1_PD4.
publishDate: 'Mar 30 2025'
isFeatured: true
seo:
  image:
    src: '/project-2.jpg'
    alt: Project preview
---

## Ejercicio 1

**Letra del ejercicio**
**EN PAPEL**

Dado el siguiente código fuente:
```kotlin
public class IdentifyMyParts {
  public static int x = 7;
  public int y = 3;
}
```
a) ¿Cuáles son las variables de clase?
b) ¿Cuáles son las variables de instancia?

**Solucion**

-a) x
-b) y

¿Cuál es la salida que produce el siguiente código?
```kotlin
  IdentifyMyParts a = new IdentifyMyParts();
  IdentifyMyParts b = new IdentifyMyParts();
  a.y = 5;
  b.y = 6;
  a.x = 1;
  b.x = 2;
  System.out.println("a.y = " + a.y);
  System.out.println("b.y = " + b.y);
  System.out.println("a.x = " + a.x);
  System.out.println("b.x = " + b.x);
  System.out.println("IdentifyMyParts.x = " + IdentifyMyParts.x);
```
**Solucion**

```kotlin
a.y = 5
b.y = 6
a.x = 2
b.x = 2
IdentifyMyParts.x = 2
```
a.x , b.x y IdentifyMyParts.x, es igual a 2 porque x es una variable Static.


## Ejercicio 2

**Letra del ejercicio**

1) Indica qué es lo que está mal en el siguiente programa:
```kotlin
public class SomethingIsWrong {
  public static void main(String[] args) {
    Rectangle myRect;
    myRect.width = 40;
    myRect.height = 50;
    System.out.println("myRect's area is " + myRect.area());
  }
}
```
2) Repara el error, ejecuta el programa y verifica que la salida es correcta.

**Solucion**

1) Lo primero MyRect no esta inicializada, porque se declara como Rectangle myRect pero
no se le asigna una instancia de Rectangle.

Lo siguiente falta al definicion de Rectangle, el codigo asume que Rectangle existe.

2) 

```kotlin
class Rectangle {
    int width;
    int height;

    int area() {
        return width * height;
    }
}
public class SomethingIsWrong {
    public static void main(String[] args) {
        Rectangle myRect = new Rectangle();  // Se crea una instancia
        myRect.width = 40;
        myRect.height = 50;
        System.out.println("myRect's area is " + myRect.area());
    }
}
```

## Ejercicio 3

**Letra del ejercicio**

1) El siguiente código crea un array y una string. ¿Cuántas referencias a estos objetos
existen luego de que el código se ha ejecutado? ¿Es alguno de los objetos candidato a
ser eliminado por el garbage collector?

```kotlin
String[] students = new String[10];
String studentName = "Peter Parker";
students[0] = studentName;
studentName = null;
...
```
2) Cómo hace un programa para destruir un objeto que ha creado?

3) Dada la siguiente clase, llamada “ContenedorDeNumeros”, escribe un programa que
cree una instancia de la clase, inicialice sus dos variables miembro yluego muestre el
valor de cada una de ellas.
```kotlin
public class NumberHolder {
  public int anInt;
  public float aFloat;
}
```
**Solucion**

1) Luego de ser ejecutado 1, porque "Peter Parker" llega a tener 2 referencias, (studentName y  students[0]) y luego studentName = null, lo deja con 1 referencia.

No hay objetos candidatos a ser eliminados porque "Peter Parker" sigue referenciado en 
students[0]

2) Manualmente en Java no se puede, pero se puede hacer cuando un objeto no tiene referencias activas.
Ejemplo:
```kotlin
MyClass obj = new MyClass(); // Se crea un objeto
obj = null; // Ahora no hay referencias al objeto, puede ser recolectado por el GC
```

3) 
```kotlin
public class NumberHolder {
    public int anInt;
    public float aFloat;
}

public class ContenedorDeNumeros {
    public static void main(String[] args) {
        NumberHolder numero = new NumberHolder();
        numero.anInt = 42;
        numero.aFloat = 3.14f;

        System.out.println("Valor de anInt: " + numero.anInt);
        System.out.println("Valor de aFloat: " + numero.aFloat);
    }
}
```
```kotlin
Valor de anInt: 42
Valor de aFloat: 3.14
```
