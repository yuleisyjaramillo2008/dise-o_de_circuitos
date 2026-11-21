<div align="center">
  <h1>⚡ SELECCIÓN Y CODIFICACIÓN DE DATOS ⚡</h1>
  <p><i>Unidad 1 • Semana 5 • Diseño de Circuitos Digitales</i></p>
</div>

---

## 🔀 Multiplexor (MUX)
<div align="center">
  <img src="../Imagenes/multiplexor_real.jpg" alt="Circuito integrado Multiplexor real" width="450">
  <p><em>Figura 1: Multiplexor real.</em></p>
</div>

<div style="background-color: #f0f7ff; border-left: 5px solid #0066cc; padding: 14px; border-radius: 6px; margin-bottom: 16px;">
  <strong style="color: #004c99; font-size: 1.05em;">📘 Definición:</strong><br>
  Un multiplexor o selector de datos es aquel que tiene <strong>varias entradas</strong> pero solo <strong>una salida</strong>, es decir, solo deja pasar una de las entradas mediante una selección o control generado por bits (líneas de selección).
</div>

---

### 🧩 Partes de un MUX

| 🏷️ Parte | 📖 Explicación | 💡 Ejemplo explicativo |
| :--- | :--- | :--- |
| <span style="color: #0066cc;"><strong>📥 2<sup>n</sup> entradas de datos</strong></span> | Los datos de entrada solo pueden ser potencias de 2 | <code>2<sup>3</sup> = 8</code> (I<sub>0</sub>, I<sub>1</sub>, I<sub>2</sub>, I<sub>3</sub>, I<sub>4</sub>, I<sub>5</sub>, I<sub>6</sub>, I<sub>7</sub>) |
| <span style="color: #6f42c1;"><strong>🎛️ n líneas de selección</strong></span> | De la fórmula 2<sup>n</sup> que es igual a las entradas, <em>n</em> es la cantidad de bits que controlan la selección | <code>8 = 2<sup>3</sup></code> por lo tanto <code>n = 3</code>, es decir, habrá tres líneas de selección (3 bits) |
| <span style="color: #198754;"><strong>📤 1 salida (Y)</strong></span> | En todo MUX siempre habrá una sola salida | Salida <strong>Y</strong> |
| <span style="color: #d97706;"><strong>🔌 OPCIONAL:</strong></span> <strong>Entrada de habilitación</strong> | Es una entrada adicional que apaga o enciende el circuito | <ul><li><span style="color: #198754;"><strong>Si E=1</strong></span> el MUX funciona de manera normal.</li><li><span style="color: #dc3545;"><strong>Si E=0</strong></span> sin importar las entradas o las líneas de selección la salida (Y) es igual a 0.</li></ul> |

---

***EJEMPLOS:***
<br>
**MUX 4:1:**
Tiene 4 entradas, es decir, 2² por lo tanto n=2 y habrá 2 líneas de selección. 
| S1 | S0 | Y |
| :--- | :--- | :--- |
| 0 | 0 | I0 |
| 0 | 1 | I1 |
| 1 | 0 | I2 |
| 1 | 1 | I3 |

<br>

<div align="center">
<pre><code>Y = S<sub>1</sub>' · S<sub>0</sub>' · I<sub>0</sub> + S<sub>1</sub>' · S<sub>0</sub> · I<sub>1</sub> + S<sub>1</sub> · S<sub>0</sub>' · I<sub>2</sub> + S<sub>1</sub> · S<sub>0</sub> · I<sub>3</sub></code></pre>
</div>

---

### 🧮 Ecuación Booleana

Para seleccionar una entrada y bloquear las demás se usan las compuertas lógicas **AND** y **OR**. Tomando el ejemplo anterior:

<div align="center">
<pre><code>Y = S<sub>1</sub>' · S<sub>0</sub>' · I<sub>0</sub> + S<sub>1</sub>' · S<sub>0</sub> · I<sub>1</sub> + S<sub>1</sub> · S<sub>0</sub>' · I<sub>2</sub> + S<sub>1</sub> · S<sub>0</sub> · I<sub>3</sub></code></pre>
</div>

<div style="background-color: #f8f9fa; border-left: 5px solid #6f42c1; padding: 14px; border-radius: 6px; margin-bottom: 16px;">
  <strong style="color: #4c2889;">⚙️ ¿Cómo funciona la selección?</strong>
  <ul>
    <li><strong>Minitérminos en S:</strong> Esta ecuación representa un minitérmino en <code>S</code> (donde <code>S = 1</code> y <code>S' = 0</code>), y cada combinación de <code>S</code> representa un número binario (<code>00</code>, <code>01</code>, <code>10</code> y <code>11</code>).</li>
    <li><strong>Condición de paso (AND):</strong> Solo deja pasar la entrada cuando la multiplicación (<strong>AND</strong>) entre las líneas de selección es <code>1</code>, ya que así no afecta al valor de la entrada.</li>
    <li><strong>Dependencia de la salida:</strong> Estas combinaciones de <code>S</code> se multiplican (<strong>AND</strong>) con una entrada (<code>I</code>) porque, siempre y cuando las líneas de selección sean iguales a <code>1</code>, el resultado dependerá o será igual a la entrada (<code>I</code>).</li>
  </ul>
</div>

#### 📊 Comportamiento de la compuerta AND como llave de paso

<div align="center">

| Selección (`S₁ · S₀`) | Entrada (`I`) | Salida (`Y`) | Estado |
| :---: | :---: | :---: | :--- |
| `0` | `0` | `0` | 🔴 Bloqueado (apagado) |
| `0` | `1` | `0` | 🔴 Bloqueado (apagado) |
| `1` | `0` | `0` | 🟢 Pasa el dato `I` (`0`) |
| `1` | `1` | `1` | 🟢 Pasa el dato `I` (`1`) |

</div>

---

### Formación de los circuitos 
Siguiendo el ejemplo de del MUX 4:1 se necesitara: <br>
* 2 NOT (para S₀` y S₁`´).
* 4 AND  de tres entradas.
* 1 OR de 4 entradas. 
<div align="center">
  <img src="../Imagenes/MUX_4Entradas.png" alt="Circuito lógico de un Multiplexor de 4 entradas" width="600">
  <p><em>Figura 2: Implementación de un Multiplexor 4:1 con compuertas lógicas (NOT, AND y OR).</em></p>
</div>

En este circuito mediante las líneas de selección se eligió la entrada (01 = 2) que estará en la salida. Y como se puede ver I1 (la segunda entrada) es igual a 1 y Y = 1. 

### Expanción 
Un MUX más grande se arma con MUX más chicos. Un MUX 8:1 son dos MUX de 4:1 que comparten S1 y S0 más un MUX 2:1 controlado por S2 que elige cuál de los dos resultados pasa. 

<br>

---

<div align="center">
  <sub>✦ • ✦ • ✦</sub>
</div>

---

<br>

---

## 🔀 Demultiplexor (DEMUX)




