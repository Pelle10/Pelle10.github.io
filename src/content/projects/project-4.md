---
title: 'Ejercicios UT5_PD1'
description: Ejercicios del UT5_PD1
publishDate: 'May 11 2025'
isFeatured: true
seo:
  image:
    src: '/project-3.jpg'
---

# EJERCICIO 1

1)
´´´kotlin
FUNCION Insertar(unaEtiqueta, etiquetaPadre)
    SI raiz ES nulo Y etiquetaPadre ES vacía
        raiz ← CrearNodo(unaEtiqueta)
        RETORNAR verdadero
    FIN SI

    nodoPadre ← Buscar(etiquetaPadre)
    SI nodoPadre ES nulo
        RETORNAR falso
    FIN SI

    nuevoNodo ← CrearNodo(unaEtiqueta)

    SI nodoPadre.primerHijo ES nulo
        nodoPadre.primerHijo ← nuevoNodo
    SINO
        hermano ← nodoPadre.primerHijo
        MIENTRAS hermano.hermanoDerecho NO ES nulo
            hermano ← hermano.hermanoDerecho
        FIN MIENTRAS
        hermano.hermanoDerecho ← nuevoNodo
    FIN SI

    RETORNAR verdadero
FIN FUNCION
´´´

2)
´´´kotlin
- Prueba para Insertar: Vamos a comprobar si podemos agregar correctamente una nueva unidad al organigrama. Si el árbol está vacío, la primera unidad debería convertirse en la raíz. Si ya hay otras unidades, la nueva debe colocarse en el lugar correcto, como hija o hermana de otra ya existente.
- Prueba para Buscar: Queremos asegurarnos de que el programa encuentra una unidad cuando la buscamos. Si la unidad existe, debe devolverla. Si intentamos buscar algo que no está en el organigrama, el resultado debería ser "no encontrado".
- Prueba para listarIndentado: Vamos a revisar si el organigrama se muestra bien, con cada unidad en su nivel correcto y bien organizada. Así podremos ver claramente qué unidades dependen de cuáles.
´´´

3)
´´´kotlin
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

class TArbolGenericoTest {
    @Test
    void testOperacionesBasicas() {
        TArbolGenerico arbol = new TArbolGenerico();
        assertTrue(arbol.insertar("RECTORÍA", ""));
        assertTrue(arbol.insertar("VICERRECTORÍA ACADÉMICA", "RECTORÍA"));
        assertTrue(arbol.insertar("FACULTAD DE INGENIERÍA", "VICERRECTORÍA ACADÉMICA"));

        assertNotNull(arbol.buscar("FACULTAD DE INGENIERÍA"));
        assertNull(arbol.buscar("UNIDAD INEXISTENTE"));

        arbol.listarIndentado(); // Deberia de imprimir correctamente
    }
}
´´´

4)

´´´kotlin
class TNodoArbolGenerico {
    String etiqueta;
    TNodoArbolGenerico primerHijo, hermanoDerecho;

    public TNodoArbolGenerico(String etiqueta) {
        this.etiqueta = etiqueta;
    }
}

class TArbolGenerico {
    private TNodoArbolGenerico raiz;

    public boolean insertar(String unaEtiqueta, String etiquetaPadre) {
        if (etiquetaPadre.isEmpty()) {
            if (raiz == null) {
                raiz = new TNodoArbolGenerico(unaEtiqueta);
                return true;
            }
            return false;
        }

        TNodoArbolGenerico nodoPadre = buscar(etiquetaPadre);
        if (nodoPadre == null) return false;

        TNodoArbolGenerico nuevoNodo = new TNodoArbolGenerico(unaEtiqueta);

        if (nodoPadre.primerHijo == null) {
            nodoPadre.primerHijo = nuevoNodo;
        } else {
            TNodoArbolGenerico hermano = nodoPadre.primerHijo;
            while (hermano.hermanoDerecho != null) {
                hermano = hermano.hermanoDerecho;
            }
            hermano.hermanoDerecho = nuevoNodo;
        }
        return true;
    }

    public TNodoArbolGenerico buscar(String unaEtiqueta) {
        return buscarRecursivo(raiz, unaEtiqueta);
    }

    private TNodoArbolGenerico buscarRecursivo(TNodoArbolGenerico nodo, String unaEtiqueta) {
        if (nodo == null || nodo.etiqueta.equals(unaEtiqueta)) return nodo;
        TNodoArbolGenerico encontrado = buscarRecursivo(nodo.primerHijo, unaEtiqueta);
        return (encontrado != null) ? encontrado : buscarRecursivo(nodo.hermanoDerecho, unaEtiqueta);
    }

    public void listarIndentado() {
        listarRecursivo(raiz, 0);
    }

    private void listarRecursivo(TNodoArbolGenerico nodo, int nivel) {
        if (nodo == null) return;
        System.out.println("  ".repeat(nivel) + nodo.etiqueta);
        listarRecursivo(nodo.primerHijo, nivel + 1);
        listarRecursivo(nodo.hermanoDerecho, nivel);
    }
}
´´´

5)
´´´kotlin
TArbolGenerico arbol = new TArbolGenerico();
arbol.insertar("RECTORÍA", "");
arbol.insertar("VICERRECTORÍA ACADÉMICA", "RECTORÍA");
arbol.insertar("VICERRECTORÍA ADMINISTRATIVA", "RECTORÍA");
arbol.insertar("FACULTAD DE INGENIERÍA", "VICERRECTORÍA ACADÉMICA");
arbol.insertar("FACULTAD DE CIENCIAS EMPRESARIALES", "VICERRECTORÍA ACADÉMICA");
arbol.insertar("DEPARTAMENTO DE RECURSOS HUMANOS", "VICERRECTORÍA ADMINISTRATIVA");
´´´

6)
´´´kotlin
System.out.println(arbol.buscar("FACULTAD DE INGENIERÍA") != null ? "Encontrado" : "No encontrado");
System.out.println(arbol.buscar("UNIDAD INVENTADA") != null ? "Encontrado" : "No encontrado");
´´´

7)
´´´kotlin
arbol.listarIndentado();
´´´