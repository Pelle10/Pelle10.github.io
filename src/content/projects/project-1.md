---
title: 'Ejercicios Domiciliarios UT1'
description: 
publishDate: 'Mar 30 2025'
seo:
  image:
    src: '/project-1.jpg'
    alt: Project preview
---

![Project preview](/project-1.jpg)


## Ejercicio 1

**Letra del ejercicio**

*Dado el siguiente programa:
    public static void zoop () {
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
    }
¿Cuál es la salida? Sé preciso acerca de dónde hay espacios y dónde hay nuevas líneas.
Indicar cuál es la respuesta más correcta: (\n denota nueva línea)*

**Solucion**

'''kotlin
fun main(){
  println("No, yo pac.\n Vos zacata pac.\n Yo pac.")
}
'''


## Features

1. **EcoScore and Challenges:**

- Users are assigned an EcoScore based on their sustainable activities and choices.
- Daily and weekly challenges encourage users to adopt new habits and compete with friends or the community to earn EcoPoints.

2. **Personalized Eco-Goals:**

- Users can set and track personalized eco-goals, such as reducing plastic usage, conserving water, or choosing eco-friendly transportation.
- The app provides tips and suggestions to help users achieve their goals.

3. **Green Rewards Marketplace:**

- EcoPoints earned through challenges and sustainable actions can be redeemed in a virtual Green Rewards Marketplace.
- The marketplace offers discounts on eco-friendly products, services, and even contributions to environmental causes.

4. **Community Hub:**

- A community feature allows users to connect, share their eco-friendly achievements, and inspire others.
- Users can join local eco-groups, organize clean-up events, and collaborate on sustainability projects.

5. **EcoEducator AI Assistant:**

- An AI-powered assistant, EcoEducator, provides personalized eco-tips, facts, and information based on users' preferences and habits.
- Users can chat with EcoEducator for instant advice on sustainable living.

## Technology Stack

- Frontend: React Native for cross-platform mobile app development.
- Backend: Firebase for real-time data synchronization and user authentication.
- Database: Firestore for scalable and flexible data storage.
- AI Integration: Dialogflow for natural language processing and conversation with EcoEducator.

## Outcome

EcoBuddy has successfully created a community of environmentally conscious individuals who actively participate in sustainable living practices. The app not only educates and motivates users but also provides tangible rewards for their commitment to a greener lifestyle, fostering a positive impact on the environment.
