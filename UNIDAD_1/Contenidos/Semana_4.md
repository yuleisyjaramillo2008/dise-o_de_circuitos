<div align="center">

# ⚙️ **CIRCUITOS ARITMÉTICOS: SUMADORES, RESTADORES Y COMPARADORES** ⚙️

</div>

## **🧠 1. Suma Binaria y Tipos de Sumadores**

La suma columna por columna requiere dos tipos de circuitos según la posición del bit:

- 🟢 **Semisumador (Half Adder - HA):** Solo suma 2 bits (`A` y `B`). Se usa únicamente en la **columna 0** porque no recibe acarreo previo.
- 🔵 **Sumador Completo (Full Adder - FA):** Suma 3 bits (`A`, `B` y el acarreo de entrada `Cin`). Se usa en las **columnas 1, 2, 3...**

| Tipo de Sumador | Entradas | Ecuación de Suma (S) | Ecuación de Acarreo (Cout) |
| :---: | :---: | :---: | :---: |
| **Semisumador (HA)** | A, B | S = A ⊕ B | Cout = A · B |
| **Sumador Completo (FA)** | A, B, Cin | S = A ⊕ B ⊕ Cin *(Impar de 1s)* | Cout = AB + A·Cin + B·Cin *(Al menos dos 1s)* |

---

## **🗺️ 2. Tablas de Verdad y Mapas de Karnaugh (Full Adder)**

### **📋 Tabla de Verdad**

| A | B | Cin | N° de 1s | Acarreo (Cout) | Suma (S) |
| :-: | :-: | :-: | :-: | :-: | :-: |
| 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 | **1** |
| 0 | 1 | 0 | 1 | 0 | **1** |
| 0 | 1 | 1 | 2 | **1** | 0 |
| 1 | 0 | 0 | 1 | 0 | **1** |
| 1 | 0 | 1 | 2 | **1** | 0 |
| 1 | 1 | 0 | 2 | **1** | 0 |
| 1 | 1 | 1 | 3 | **1** | **1** |

### **🧩 Análisis Ecuacional de los Mapas K**

- **Mapa K de la Suma (S):** Los `1`s quedan en posición de ajedrez (ninguno tiene vecinos). No admite simplificación adyacente y se expresa directamente como **XOR triple** (`S = A ⊕ B ⊕ Cin`).
- **Mapa K del Acarreo (Cout):** Forma 3 grupos de 2 celdas. Representa la regla de mayoría: `Cout = AB + A·Cin + B·Cin`.

---

## **⛓️ 3. Sumador en Cadena (Ripple Carry Adder) y Retardo**

Para sumar números de N bits se encadenan N sumadores completos conectando la salida `Cout` de cada etapa al `Cin` de la siguiente.

- 🌊 **Efecto Ola (Ripple):** El resultado final se completa de derecha a izquierda conforme el acarreo se propaga etapa por etapa.
- ⏱️ **Estimación del Retardo:** Asumiendo ≈ 10 ns por compuerta y que el acarreo cruza ≈ 2 compuertas por etapa:

<pre><code>Tiempo Total ≈ 2 · N · 10 ns</code></pre>

- **4 bits:** ≈ 80 ns
- **16 bits:** ≈ 320 ns
- **32 bits:** ≈ 640 ns

---

## **🔄 4. Circuito Sumador / Restador Controlado**

Usando la propiedad de **Complemento a Dos** (`A - B = A + (-B)`) y compuertas `XOR` como inversores controlados por una señal `M`:

- 🟢 **Modo Suma (`M = 0`):** `B` pasa intacto y `Cin = 0`.
- 🔴 **Modo Resta (`M = 1`):** `B` se invierte bit a bit (`XOR`) y entra `Cin = 1` al primer sumador (aporta el +1 de C2).

---

## **⚠️ 5. Overflow (Desbordamiento) y Comparador**

### **🚨 Detección de Overflow (V)**
Ocurre cuando el resultado de una operación con signo supera el rango representable (ejemplo en 4 bits con signo: -8 a +7).

- **Regla Práctica:** Se compara el acarreo que entra al bit de signo (`C3`) con el acarreo que sale (`C4`).

<pre><code>V = C3 ⊕ C4</code></pre>

> 💡 *Nota:* `Cout = 1` en el bit MSB **no** significa error en operaciones con signo; la falla real la indica únicamente el flag `V`.

---

### **📊 Comparador de Magnitud (CI 7485)**

Determina las relaciones de orden entre dos números A y B:

- **Igualdad (`A = B`):** Aplica `XNOR` bit a bit y evalúa una compuerta `AND` general.
- **Mayoría (`A > B`):** Evalúa desde el bit más significativo (MSB) hacia el menos significativo (LSB); el primer bit diferente determina cuál es mayor.
