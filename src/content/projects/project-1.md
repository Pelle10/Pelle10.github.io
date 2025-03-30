---
title: 'Ejercicios Domiciliarios UT1'
description: Ejercicios del UT1_PD1 al UT1_PD10
publishDate: 'Mar 30 2025'
isFeatured: true
seo:
  image:
    src: 'project-1.jpg'
    alt: Project preview
---

![Project preview](/project-1.jpg)


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


## Technology Stack

- Frontend: React Native for cross-platform mobile app development.
- Backend: Firebase for real-time data synchronization and user authentication.
- Database: Firestore for scalable and flexible data storage.
- AI Integration: Dialogflow for natural language processing and conversation with EcoEducator.

## Outcome

EcoBuddy has successfully created a community of environmentally conscious individuals who actively participate in sustainable living practices. The app not only educates and motivates users but also provides tangible rewards for their commitment to a greener lifestyle, fostering a positive impact on the environment.
