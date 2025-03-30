---
title: 'Ejercicios UT1_PD5'
description: Ejercicios del UT1_PD5
publishDate: 'Mar 30 2025'
isFeatured: true
seo:
  image:
    src: '/project-3.jpg'
---

# Ejercicio 1

## Letra del ejercicio

La declaración “enum” define una clase (llamada tipo enumerado). El cuerpo de esta clase
puede incluir métodos y otros campos. En particular, el compilador automáticamente agrega
algunos métodos especiales cuando crea un enum. Por ejemplo, tiene un método de valores
estáticos que retorna un array que contiene todos los valores del enum en el orden en que
fueron declarados.
1) Escribe un ejemplo de uso de tal método, y asegúrate de comprender cómo funciona!!
2) Teniendo presente el programa que tu Equipo escribió para contar vocales y
consonantes en una cierta frase, ¿cómo podrías escribirlo nuevamente utilizando tipos
enumerados?

**Solucion**
1) 
```kotlin
public class EnumEjemplo {
    public enum Dia {
        LUNES, MARTES, MIERCOLES, JUEVES, VIERNES, SABADO, DOMINGO
    }

    public static void main(String[] args) {
        for (Dia d : Dia.values()) {
            System.out.println(d);
        }
    }
}
```
2) 
```kotlin
public class ContadorLetras {

    public static void main(String[] args) {
        String frase = "Hola Mundo!";
        int vocales = 0, consonantes = 0;

        for (int i = 0; i < frase.length(); i++) {
            char c = Character.toLowerCase(frase.charAt(i));

            if ("aeiou".indexOf(c) != -1) { // Es una vocal
                vocales++;
            } else if (Character.isLetter(c)) { // Es una consonante
                consonantes++;
            }
        }

        System.out.println("Vocales: " + vocales);
        System.out.println("Consonantes: " + consonantes);
    }
}
```

# Ejercicio 2

## Letra del ejercicio

dado el siguiente código fuente:
```kotlin
public class ValueOfDemo {
  public static void main(String[] args) {

      // this program requires two
      // arguments on the command line
      if (args.length == 3) {
        // convert strings to numbers
        float a = (Float.value (args[0])).floatValue();
        float b = (Float.valueOf(args[1])).float ();

        // do some arithmetic
        System.out.println("a + b = " +
        (a + b));
        System.out.println("a - b = " +
        (a - b));
        System.out.println("a * b = " +
        (a * b));
        System.out.println("a / b = " +
        (a / b));
        System.out.println("a % b = " +
        (a % b));
    } else {
      System.out.println("This program " +
        "requires two command-line arguments.");
    }
  }
}
```
1) Verificar que funciona correctamente e indicar cuál es la salida cuando se invoca con
parámetros 13.4 y 66.1
2) ¿cómo debería modificarse el código si los parámetros de línea de comando fueran
solamente enteros positivos?

**Solucion**
1) 
```kotlin
//salidas
a + b = 79.5
a - b = -52.699997
a * b = 885.7399
a / b = 0.20272315
a % b = 13.4
```

2) En vez de utilizar float usar integer, y utilizar division entera.

# Ejercicio 3

## Letra del ejercicio

Dado el siguiente código:
```kotlin
public class ToStringDemo {
  public static void main(String[] args) {
    double d = 888.51;
    String s = Double.toString(d);

    int dot = s.indexOf('.');
    System.out.println(dot + " digits " +
      "before decimal point.");
    System.out.println( (s.length() - dot - 1) +
      " digits after decimal point.");
  }
}
```
1) Indicar cuál es la salida obtenida al ejecutarlo.
2) Indicar por qué se imprime cada uno de los datos y la razón de su forma

**Solucion**

1) Salida:
```kotlin
3 digits before decimal point.
2 digits after decimal point.
```
2) Toma el número 888.51 y lo convierte en letras: "888.51",
Cuenta las letras hasta encontrar el punto:

Posición 0: '8'

Posición 1: '8'

Posición 2: '8'

Posición 3: '.' (aquí está el punto).
Guarda el número 3 porque el punto está en la tercera posición.

Cuenta los digitos antes del punto (3).

Cuenta los digitos despues del punto, la cadena tiene 6 letras, resta la posicion
del punto y el punto mismo y da que hay 2 digitos despues.

# Ejercicio 4

## Letra del ejercicio

¿Cuál es la capacidad inicial del siguiente stringbuilder?
```kotlin
StringBuilder sb = new StringBuilder("Able was I ere I saw Elba.");
```
**Solucion**

Longitud del string: "Able was I ere I saw Elba." tiene 24 caracteres (incluyendo espacios y punto).

Capacidad inicial = 16 + 24 = 40.

Entonces la siguiente sera 40

# Ejercicio 5

## Letra del ejercicio

Considere la siguiente string:
```kotlin
String hannah = "Did Hannah see bees? Hannah did.";
```
a) ¿qué valor muestra la expresión “hannah.length”?
b) ¿qué valor es retornado por la invocación del método “hannah.charAt(12)”?
c) Escribe una expresión que referencie la letra “b” en la string referida por “hannah".

**Solucion**

a) 32

b) "e"

c) hannah.charAt(15)

# Ejercicio 6

## letra del ejercicio

¿Cuán larga es las string devuelta por la siguiente expresión? ¿cuál es la string?
```kotlin
"Was it a car or a cat I saw?".substring(9, 12)
```

**Solucion**

La string devuelta es car y tiene largo 3.