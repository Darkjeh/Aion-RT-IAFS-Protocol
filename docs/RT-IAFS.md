# RT-IAFS: Real-Time Iterative Audio Feedback System

## 1. Propósito del Módulo
RT-IAFS es un protocolo de interacción para edición de audio basado en nodos temporales, preservación absoluta y modificación iterativa guiada por lenguaje natural. No es una herramienta tradicional: es una arquitectura modular diseñada para integrarse en sistemas más amplios como MAin y AIFS.

Su objetivo es permitir modificaciones precisas dentro de rangos temporales sin alterar el resto del audio, garantizando continuidad y control total.

---

## 2. Arquitectura General
RT-IAFS se compone de cuatro elementos principales:

### 2.1 Timeline Engine
Motor que representa el audio como una línea temporal continua. Permite:
- Cortes
- Inserciones
- Reemplazos
- Ajustes de volumen
- Efectos simples (fade in/out)

### 2.2 NodoTemporal
Unidad mínima de modificación. Contiene:
- start_time
- end_time
- buffer_original
- buffer_modificado

El nodo garantiza que solo el segmento seleccionado sea alterado.

### 2.3 Hook Temporal
Sistema de selección que define el rango a modificar. El usuario selecciona un intervalo, y el sistema lo convierte en un nodo.

### 2.4 Orquestador
Interpreta instrucciones en lenguaje natural y decide qué operación aplicar al nodo.

---

## 3. Flujo Operativo
1. Cargar audio base.
2. Usuario selecciona un rango temporal.
3. El sistema crea un NodoTemporal.
4. El usuario da una instrucción.
5. El orquestador interpreta la intención.
6. Se aplica la modificación solo dentro del nodo.
7. Se genera un preview.
8. El usuario evalúa y repite.

Este ciclo continúa hasta que el usuario declara finalizada la iteración.

---

## 4. Estados del Sistema
- Idle: esperando selección.
- NodeSelected: nodo temporal definido.
- Processing: aplicando modificación.
- PreviewReady: esperando evaluación del usuario.
- Iteration: repitiendo el ciclo.

---

## 5. Ejemplos de Uso

### Ejemplo 1: Ajuste de volumen
Instrucción: "Bájale 20% al volumen entre 00:12 y 00:15."
- Se crea un nodo.
- El orquestador clasifica la intención como ajuste_volumen.
- Se modifica solo el nodo.

### Ejemplo 2: Suavizar transición
Instrucción: "Haz un fade out suave en los últimos 300 ms del rango
