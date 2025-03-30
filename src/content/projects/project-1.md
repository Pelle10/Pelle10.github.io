---
title: 'Ejercicios Domiciliarios UT1_PD1'
description: Ejercicios del UT1_PD1
publishDate: 'Mar 30 2025'
isFeatured: true
seo:
  image:
    src: 'project-1.jpg'
    alt: Project preview
---

## PD1_Ejercicio 1

**Letra del ejercicio**

Dado el siguiente programa:
```kotlin
    "public static void zoop () {
    baffle ();
    System.out.print ("Vos zacata ");
    baffle ();
    }
    public static void main (String[] args) {
    System.out.print ("No, yo ");
    zoop ();
    System.out.print ("Yo ");
    baffle ();
    }
    public static void baffle () {
    System.out.print ("pac");
    ping ();
    }
    public static void ping () {
    System.out.println (".");
    }"
```
¿Cuál es la salida? Sé preciso acerca de dónde hay espacios y dónde hay nuevas líneas.
Indicar cuál es la respuesta más correcta: (\n denota nueva línea)

**Resultado**

```kotlin
"No, yo pac.\n Vos zacata pac.\n Yo pac."
```


## PD1_Ejercicio 2

**Letra del ejercicio**

Dado el siguiente código fuente:
```kotlin
public class Zumbido {

public static void desconcertar (String dirigible) {
  System.out.println (dirigible);
  sipo ("ping", -5);
}
public static void sipo (String membrillo, int flag) {
  if (flag < 0) {
  System.out.println (membrillo + " sup");
  } else {
    System.out.println ("ik");
    desconcertar (membrillo);
    System.out.println ("muaa-ja-ja-ja");
  }
}
public static void main (String[] args) {
  sipo ("traqueteo", 13);
  }
}
```
a) ¿Cuál es la primera sentencia que se ejecuta?
b) Escribir número 2 al lado de la segunda sentencia, un 3 al lado de la que se ejecuta en
tercer lugar, y así siguiendo hasta el final del programa. Si una sentencia se ejecuta más
de una vez, puede que termine con más de un número al lado

**Resultado**

```kotlin
a)La primera sentencia que se ejecuta es el Main

b) 2- Sipo("traqueteo, 13"), 3-desconcertar("traqueteo"), 4- sipo("ping",-5), 5-sipo("traqueteo, 13")//Vuelve
```

## PD1_Ejercicio3

**Letra del ejercicio**

Muchos cálculos pueden ser expresados de manera concisa usando la operación “multsuma”,
que toma tres operandos y computa a*b + c. Algunos procesadores incluso proveen una
implementación de hardware para esta operación para números de punto flotante.
Crear un nuevo programa llamado Multsuma.java. Escribir un método llamado multsuma que
toma tres doubles como parámetros y que imprime el resultado de multisumarlo.
Escribir un método main que testee multsuma invocándolo con unos pocos parámetros
simples, como por ejemplo 1.0, 2.0, 3.0, y después imprima por consola el resultado, que en
ese caso debería ser 5.0.

```kotlin
package UT1.TA3;

public class Multsuma {
    public static double multsuma(double a, double b, double c) {
        return (a * b) + c;
    }
    
    public static void main(String[] args) {
        double resultado1 = multsuma(1.0, 2.0, 3.0);
        System.out.println("Resultado de multsuma(1.0, 2.0, 3.0): " + resultado1); 
        
        double resultado2 = multsuma(4.5, 2.0, -1.0);
        System.out.println("Resultado de multsuma(4.5, 2.0, -1.0): " + resultado2); 
        
        double resultado3 = multsuma(0.0, 10.0, 5.0);
        System.out.println("Resultado de multsuma(0.0, 10.0, 5.0): " + resultado3);
    }
}
```

## PD1_Ejercicio4

**Letra del ejercicio**

Ingrese el siguiente código fuente en su proyecto (una clase “Alumno” y varios métodos
independientes, que no son de la clase “Alumno”) :

```kotlin
public class Alumno {
  private String nombre;
  public Alumno () {
    nombre = null;
  }

  public String getNombreAdmiracion() {
    return nombre.concat("!");
  }
  public static void main (String[] args) {
    Alumno alumno = new Alumno();
  System.out.println(alumno.getNombreAdmiracion());
  }
}
  public static int recorrer (String cadena) {
    int res = 0;
    for (int i = 1; i <= cadena.length(); i++) {
      if (cadena.charAt(i) != ' ') {
        res++;
    }
      }
      return res;
  }
  public static int getValor() {
    int vector[] = { 6, 16, 26,36,46,56,66,76 };
    int idx = 8;
    return vector[idx];
  }
  public static char getPrimerCaracter(String palabra) {
    String string[] = new String[5];
    return (string[1].charAt(1));
  }
  public static String paraAString(int a) {
    Object x1 = new Integer(a);
    return (String) (x1) ;
  }
```

a) Indicar el error al ejecutar la clase Alumno y corregirlo. ¿cómo lo detectaste?

b) Indicar el error al ejecutar el método “recorrer” y corregirlo. ¿cómo lo detectaste?

c) Indicar el error al ejecutar el método “getValor” y corregirlo. ¿cómo lo detectaste?

d) Indicar el error al ejecutar el método “getPrimerCaracter” y corregirlo. ¿cómo lo detectaste?

e) Indicar el error al ejecutar el método “paraAString” y corregirlo. ¿cómo lo detectaste?

```kotlin
a)Al ejecutar getNombreAdmiracion() se lanza una NullPointerException porque nombre es null y se intenta hacer concat() sobre null.

Lo detecté sabiendo que concatenar (!) a un String null causará una excepción. Además, el constructor inicia nombre como null.

Coreccion seria inicializar nombre = ""

b) Hay un ArrayIndexOutOfBoundsException porque el bucle comienza en i = 1 y llega hasta i = cadena.length(), pero los índices de String van de 0 a length() - 1.

Lo detecté investigando para saber que los Strings en Java son 0-indexados, y charAt(length()) está fuera de rango.

Coreccion seria for (i = 0; i < cadena.length(); i++)

c)Hay un ArrayIndexOutOfBoundsException porque el array tiene 8 elementos (índices 0-7), pero se intenta acceder al índice 8.

Lo detecté viendo que el array tiene longitud 8, por lo que el último índice válido es 7.

Correcion seria cambiar idx = 7

d)Hay un NullPointerException porque string[1] es null (el array se inicializa pero no sus elementos).

Lo detecté porque los arrays de objetos se inicializan con null, y no se puede invocar métodos sobre null.

Correccion inicializar un array con valores

e)Hay un ClassCastException porque no se puede castear directamente un Integer a String.

Lo busque y encontré que en Java, no se puede hacer cast directo entre tipos no relacionados.

Correccion usar toString()
```

## PD1_Ejercicio5

**Letra del ejercicio**

Escriba una clase Contador y utilice un bucle while para mostrar el valor de una variable
contador que se incrementa de a uno.
Siga los siguientes pasos para crear su clase:
1. Cree una clase llamada contador con tres atributos llamados: MAX_CONT, incremento
y contador. Asigne el valor 50 a MAX_CONT y el valor 1 a contador e incremento.
Asegúrese de declarar MAX_CONT como una variable "final".
2. Cree un método público mostrarContador en la clase, que no reciba parámetros y
retorne void. Por ejemplo:
public void displayCount()
3. Cree un bucle while en el método con las siguientes características:
a. Expresión booleana: Repita si el valor de contador es menor o igual que el
valor de MAX_CONT.
b. Bloque de código:
i. Imprima el valor de la variable contador.
ii. Incremente el valor de la variable contador con el valor de incremento.
Por ejemplo: contador = contador + incremento;
4. ejecute el archivo Contador.java y observe los valores emitidos.
5. Reescriba el algoritmo de manera de usar una sentencia do-while. Verifique que hace
lo mismo.
6. Reescriba el algoritmo de manera de usar una sentencia for. Verifique que hace lo
mismo.

```kotlin
public class Contador {
    private final int MAX_CONT = 50;
    private int incremento = 1;
    private int contador = 1;

    // Método con while
    public void mostrarContadorWhile() {
        System.out.println("Usando while:");
        contador = 1; 
        while (contador <= MAX_CONT) {
            System.out.println(contador);
            contador += incremento;
        }
    }

    // Método con do-while
    public void mostrarContadorDoWhile() {
        System.out.println("Usando do-while:");
        contador = 1; 
        do {
            System.out.println(contador);
            contador += incremento;
        } while (contador <= MAX_CONT);
    }

    // Método con for
    public void mostrarContadorFor() {
        System.out.println("Usando for:");
        for (int i = 1; i <= MAX_CONT; i += incremento) {
            System.out.println(i);
        }
    }

    public static void main(String[] args) {
        Contador c = new Contador();
        c.mostrarContadorWhile();
        c.mostrarContadorDoWhile();
        c.mostrarContadorFor();
    }
}
```