---
title: 'Ejercicios UT5_PD3'
description: Ejercicios del UT5_PD3
publishDate: 'May 11 2025'
isFeatured: true
seo:
  image:
    src: '/project-3.jpg'
---

# EJERCICIO 1

Paso 1)
´´´kotlin
import java.util.*;

class TrieNode {
    Map<Character, TrieNode> hijos = new HashMap<>();
    boolean esPalabraFinal = false;
    Set<Integer> paginas = new TreeSet<>(); // Almacena páginas ordenadas
}
´´´

Paso2)
´´´kotlin
FUNCION IndizarLibro(trie, archivoLibro)
    pagina ← 1
    lineas ← 0
    
    PARA CADA linea EN archivoLibro
        palabras ← LimpiarYSeparar(linea)
        PARA CADA palabra EN palabras
            trie.InsertarPalabra(palabra, pagina)
        FIN PARA
        
        lineas ← lineas + 1
        SI lineas == 50
            pagina ← pagina + 1
            lineas ← 0
        FIN SI
    FIN PARA
FIN FUNCION
´´´

´´´kotlin
import java.io.*;

class Trie {
    private TrieNode raiz = new TrieNode();

    public void indizarLibro(String archivoLibro) throws IOException {
        BufferedReader lector = new BufferedReader(new FileReader(archivoLibro));
        String linea;
        int pagina = 1, lineas = 0;

        while ((linea = lector.readLine()) != null) {
            String[] palabras = limpiarYSeparar(linea);
            for (String palabra : palabras) {
                insertar(palabra, pagina);
            }

            lineas++;
            if (lineas == 50) {
                pagina++;
                lineas = 0;
            }
        }
        lector.close();
    }

    private String[] limpiarYSeparar(String linea) {
        return linea.toLowerCase().replaceAll("[^a-z]", " ").split("\\s+");
    }
}
´´´

Paso 3)

´´´kotlin
FUNCION ImprimirIndice(trie)
    palabras ← ObtenerPalabrasOrdenadas(trie)
    PARA CADA palabra EN palabras
        IMPRIMIR palabra + " → " + paginas de la palabra
    FIN PARA
FIN FUNCION
´´´

´´´kotlin
public void imprimirIndice() {
    imprimirRecursivo(raiz, new StringBuilder());
}

private void imprimirRecursivo(TrieNode nodo, StringBuilder palabra) {
    if (nodo.esPalabraFinal) {
        System.out.println(palabra.toString() + " → " + nodo.paginas);
    }

    for (Map.Entry<Character, TrieNode> entrada : nodo.hijos.entrySet()) {
        palabra.append(entrada.getKey());
        imprimirRecursivo(entrada.getValue(), palabra);
        palabra.deleteCharAt(palabra.length() - 1);
    }
}
´´´

Paso 4)

´´´kotlin
Trie trie = new Trie();
trie.indizarLibro("libro_prueba.txt");
trie.imprimirIndice();
´´´

Paso 5)

´´´kotlin
Trie trie = new Trie();
trie.indizarLibro("libro.txt");
trie.imprimirIndice();
´´´

(codigo completo)
´´´kotlin
import java.io.*;
import java.util.*;

class TrieNode {
    Map<Character, TrieNode> hijos = new HashMap<>();
    boolean esPalabraFinal = false;
    Set<Integer> paginas = new TreeSet<>(); // Páginas ordenadas

    public TrieNode() {}
}

class Trie {
    private TrieNode raiz = new TrieNode();

    public void insertar(String palabra, int pagina) {
        TrieNode nodo = raiz;
        for (char letra : palabra.toCharArray()) {
            nodo.hijos.putIfAbsent(letra, new TrieNode());
            nodo = nodo.hijos.get(letra);
        }
        nodo.esPalabraFinal = true;
        nodo.paginas.add(pagina);
    }

    public Set<Integer> buscar(String palabra) {
        TrieNode nodo = raiz;
        for (char letra : palabra.toCharArray()) {
            if (!nodo.hijos.containsKey(letra)) {
                return Set.of(); // Retorna vacío si no se encuentra la palabra
            }
            nodo = nodo.hijos.get(letra);
        }
        return nodo.esPalabraFinal ? nodo.paginas : Set.of();
    }

    public void indizarLibro(String archivoLibro) throws IOException {
        BufferedReader lector = new BufferedReader(new FileReader(archivoLibro));
        String linea;
        int pagina = 1, lineas = 0;

        while ((linea = lector.readLine()) != null) {
            String[] palabras = limpiarYSeparar(linea);
            for (String palabra : palabras) {
                insertar(palabra, pagina);
            }

            lineas++;
            if (lineas == 50) { // Cada 50 líneas incrementamos la página
                pagina++;
                lineas = 0;
            }
        }
        lector.close();
    }

    private String[] limpiarYSeparar(String linea) {
        return linea.toLowerCase().replaceAll("[^a-z]", " ").split("\\s+");
    }

    public void imprimirIndice() {
        imprimirRecursivo(raiz, new StringBuilder());
    }

    private void imprimirRecursivo(TrieNode nodo, StringBuilder palabra) {
        if (nodo.esPalabraFinal) {
            System.out.println(palabra.toString() + " → " + nodo.paginas);
        }

        for (Map.Entry<Character, TrieNode> entrada : nodo.hijos.entrySet()) {
            palabra.append(entrada.getKey());
            imprimirRecursivo(entrada.getValue(), palabra);
            palabra.deleteCharAt(palabra.length() - 1);
        }
    }
}

public class IndiceLibro {
    public static void main(String[] args) {
        try {
            Trie trie = new Trie();

            trie.indizarLibro("libro_prueba.txt");

            trie.imprimirIndice();

            System.out.println("Búsqueda de 'programa': " + trie.buscar("programa"));
            System.out.println("Búsqueda de 'gato': " + trie.buscar("gato"));

        } catch (IOException e) {
            System.err.println("Error al leer el archivo: " + e.getMessage());
        }
    }
}
´´´

# EJERCICIO 2

´´´kotlin
public String buscar(String palabra) {
    palabra = palabra.toLowerCase().replaceAll("[^a-z]", " "); // Limpiar palabra
    TrieNode nodo = raiz;
    int comparaciones = 0;

    for (char letra : palabra.toCharArray()) {
        comparaciones++;
        if (!nodo.hijos.containsKey(letra)) {
            return "La palabra '" + palabra + "' NO se encuentra en el índice. Comparaciones realizadas: " + comparaciones;
        }
        nodo = nodo.hijos.get(letra);
    }

    if (nodo.esPalabraFinal) {
        return "Palabra: " + palabra + " | Páginas: " + nodo.paginas + " | Comparaciones realizadas: " + comparaciones;
    } else {
        return "La palabra '" + palabra + "' NO se encuentra en el índice. Comparaciones realizadas: " + comparaciones;
    }
}
´´´