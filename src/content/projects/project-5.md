---
title: 'Ejercicios UT5_PD2'
description: Ejercicios del UT5_PD2
publishDate: 'May 11 2025'
isFeatured: true
seo:
  image:
    src: '/project-3.jpg'
---
# EJERCICIO 1

2)

a)
- Recorrer el texto palabra por palabra.
- Insertar cada palabra en el Trie, creando nuevos nodos si es necesario.
- Si la palabra ya existe, agregar la página a la lista de páginas en el nodo final

b)
´´´kotlin

 Precondiciones:
- Tener el texto con palabras y sus páginas.
- El Trie debe estar vacío antes de empezar.
 Postcondiciones:
- El Trie almacenará todas las palabras con sus páginas asociadas.
- Cada búsqueda devolverá las páginas correctas.

´´´

c)Pseudocodigo
´´´kotlin

FUNCION InsertarPalabra(trie, palabra, paginas)
    nodo ← trie.raiz
    PARA CADA letra EN palabra
        SI nodo NO tiene hijo con esa letra
            nodo.nuevoHijo(letra)
        FIN SI
        nodo ← nodo.hijo(letra)
    FIN PARA
    
    nodo.esPalabraFinal ← verdadero
    nodo.paginas.agregar(paginas)
FIN FUNCION

´´´

3)
´´´kotlin

# Comparaciones para buscar "Programa"
 
 Se comparan 8 caracteres (P-R-O-G-R-A-M-A).
 
# Comparaciones para buscar "Proselitismo"
 
 Se comparan 3 caracteres (P-R-O), pero el trie no tiene más letras después de "O", entonces se detiene.
 
# Comparaciones para insertar "Cazadores"
 
 Se comparan 8 caracteres (C-A-Z-A-D-O-R-E-S), insertando nuevos nodos cuando sea necesario.
 
# Altura del trie
 
 La altura es igual a la longitud de la palabra más larga, que en este caso es "Programación" con 12 caracteres.

# Tamaño del trie

 Número total de nodos únicos, que depende de cuántas palabras comparten letras. Aproximadamente 50 nodos considerando repeticiones de letras.

´´´

# EJERCICIO 2

´´´kotlin

FUNCION BuscarPalabra(trie, palabra)
    nodo ← trie.raiz
    PARA CADA letra EN palabra
        SI nodo NO tiene hijo con esa letra
            RETORNAR "La palabra no se encuentra en el libro"
        FIN SI
        nodo ← nodo.hijo(letra)
    FIN PARA

    SI nodo.esPalabraFinal
        RETORNAR nodo.paginas
    FIN SI

    RETORNAR "La palabra no se encuentra en el libro"
FIN FUNCION

´´´