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
**MUX 2:1:** Tiene 2 entradas, por lo tanto tiene una línea de control. <br>

| S | Y |
| :--- | :--- |
| 0 | I0 |
| 1 | I1 |

<div align="center">
<pre><code>Y = S' · I<sub>0</sub> + S · I<sub>1</sub></code></pre>
</div>

---

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
* 1 OR de 4 entradas. <br>
***🔢 Integrados de la familia 74LS*** <br>

| Integrado | Qué contiene |
| :--- | :--- |
| 74LS157 | 4 multiplexores 2:1 |
| 74LS153 | 2 multiplexores 4:1 |
| 74LS151 | 1 multiplexor 8:1 |
| 74LS150 | 1 multiplexor 16:1 |
<br>

<div align="center">
  <img src="../Imagenes/MUX_4Entradas.png" alt="Circuito lógico de un Multiplexor de 4 entradas" width="600">
  <p><em>Figura 2: Implementación de un Multiplexor 4:1 con compuertas lógicas (NOT, AND y OR).</em></p>
</div>

En este circuito mediante las líneas de selección se eligió la entrada (01 = 2) que estará en la salida. Y como se puede ver I1 (la segunda entrada) es igual a 1 y Y = 1.  <br>

---

### Expanción 
Un MUX más grande se arma con MUX más chicos. Un MUX 8:1 son dos MUX de 4:1 que comparten S1 y S0 más un MUX 2:1 controlado por S2 que elige cuál de los dos resultados pasa. 

<div align="center">
  <img src="../Imagenes/Expansion_8entradas.jpg" alt="Expansión de Multiplexor a 8 entradas" width="550">
  <p><em>Figura 3: Expansión de un Multiplexor a 8 entradas (MUX 8:1).</em></p>
</div>

<br>

<div align="center" style="background-color: #f6f8fa; border: 2px solid #0969da; border-radius: 10px; padding: 12px 20px; margin: 20px 0;">
  <h3 style="margin: 0; color: #0969da;">⚡ EJERCICIOS ⚡</h3>
  <sub>Práctica de Multiplexores (MUX)</sub>
</div>

<br>
<div style="background-color: #fff8c5; border-left: 5px solid #d4a72c; padding: 14px; border-radius: 6px; margin-bottom: 16px;">
  <strong style="color: #7d4e00; font-size: 1.05em;">📋 Enunciado:</strong><br>
  Una planta industrial requiere supervisar <strong>8 sensores digitales</strong> (<code>I<sub>0</sub></code> a <code>I<sub>7</sub></code>) enviando su señal a una única línea de monitoreo (<code>Y</code>), controlada por un selector binario y un interruptor maestro de mantenimiento (<code>E</code>). Si los sensores registran <code>I<sub>0</sub>=0, I<sub>1</sub>=1, I<sub>2</sub>=0, I<sub>3</sub>=1, I<sub>4</sub>=1, I<sub>5</sub>=0, I<sub>6</sub>=1, I<sub>7</sub>=0</code>, <strong>¿qué arquitectura de multiplexor (dimensionamiento, ecuación, compuertas, integrado comercial y expansión) se requiere, y cuál será el valor en la salida <code>Y</code> cuando <code>S<sub>2</sub>S<sub>1</sub>S<sub>0</sub> = 110</code> con <code>E = 1</code> y luego al cambiar a <code>E = 0</code>?</strong>
</div>

<div align="center">

| Parámetro | Valor / Dato |
| :--- | :--- |
| **Tipo de circuito** | MUX 8:1 con Enable |
| **Entradas de datos (2<sup>n</sup>)** | <code>2<sup>3</sup> = 8</code> (<code>I<sub>0</sub></code> a <code>I<sub>7</sub></code>) |
| **Líneas de selección (<em>n</em>)** | <code>n = 3</code> (<code>S<sub>2</sub></code>, <code>S<sub>1</sub></code>, <code>S<sub>0</sub></code>) |
| **Habilitación / Salida** | <code>E</code> (1 bit) / <code>Y</code> (1 salida) |
| **Compuertas discretas** | 3 NOT + 8 AND (4 ent.) + 1 OR (8 ent.) + 1 AND (2 ent.) = **13 compuertas** |
| **Integrado 74LS** | **74LS151** (1 MUX 8:1) |
| **Expansión** | 2 MUX 4:1 (**74LS153**) en <code>S<sub>1</sub>, S<sub>0</sub></code> + 1 MUX 2:1 (**74LS157**) en <code>S<sub>2</sub></code> |

</div>

<br>



<div align="center">
<pre><code>Y = E · ( S<sub>2</sub>'·S<sub>1</sub>'·S<sub>0</sub>'·I<sub>0</sub> + S<sub>2</sub>'·S<sub>1</sub>'·S<sub>0</sub>·I<sub>1</sub> + S<sub>2</sub>'·S<sub>1</sub>·S<sub>0</sub>'·I<sub>2</sub> + S<sub>2</sub>'·S<sub>1</sub>·S<sub>0</sub>·I<sub>3</sub> +
          S<sub>2</sub>·S<sub>1</sub>'·S<sub>0</sub>'·I<sub>4</sub> + S<sub>2</sub>·S<sub>1</sub>'·S<sub>0</sub>·I<sub>5</sub> + S<sub>2</sub>·S<sub>1</sub>·S<sub>0</sub>'·I<sub>6</sub> + S<sub>2</sub>·S<sub>1</sub>·S<sub>0</sub>·I<sub>7</sub> )</code></pre>
</div>

<br>

<div align="center">
  <img src="../Imagenes/MUX_8Entradas_Circuito.png" alt="Circuito lógico de un Multiplexor 8:1 con Enable" width="650">
  <p><em>Figura 4: Simulación en Logisim del Multiplexor 8:1 con entrada de habilitación (E).</em></p>
</div>

<div align="center">

| `E` | `S2 S1 S0` | Minitérmino activo (`= 1`) | Canal | Dato (`I`) | Salida (`Y`) |
| :---: | :---: | :---: | :---: | :---: | :---: |
| `1` | `000` | `S2' · S1' · S0'` | `I0` | `0` | `0` |
| `1` | `001` | `S2' · S1' · S0` | `I1` | `1` | `1` |
| `1` | `010` | `S2' · S1 · S0'` | `I2` | `0` | `0` |
| `1` | `011` | `S2' · S1 · S0` | `I3` | `1` | `1` |
| `1` | `100` | `S2 · S1' · S0'` | `I4` | `1` | `1` |
| `1` | `101` | `S2 · S1' · S0` | `I5` | `0` | `0` |
| **`1`** | **`110`** | **`S2 · S1 · S0'`** | **`I6`** | **`1`** | **`1`** |
| `1` | `111` | `S2 · S1 · S0` | `I7` | `0` | `0` |
| **`0`** | **`XXX`** | `0` | — | `X` | **`0`** |

</div>

<div style="background-color: #e6ffed; border-left: 5px solid #198754; padding: 12px; border-radius: 6px; margin-top: 12px;">
  <strong style="color: #146c43;">✅ Respuesta:</strong> Con <code>E = 1</code> y <code>S<sub>2</sub>S<sub>1</sub>S<sub>0</sub> = 110</code>, se selecciona <code>I<sub>6</sub></code> y la salida es <strong><code>Y = 1</code></strong>; al pasar a <code>E = 0</code>, la salida es <strong><code>Y = 0</code></strong>.
</div>


<br>

---

<div align="center">
  <sub>✦ • ✦ • ✦</sub>
</div>

---

<br>

---


## 🔀 Demultiplexor (DEMUX)

<div align="center">
  <img src="../Imagenes/DEMUX_REAL.jpg" alt="Circuito integrado Demultiplexor real" width="450">
  <p><em>Figura 5: Demultiplexor real.</em></p>
</div>

<div style="background-color: #f0f7ff; border-left: 5px solid #0066cc; padding: 14px; border-radius: 6px; margin-bottom: 16px;">
  <strong style="color: #004c99; font-size: 1.05em;">📘 Definición:</strong><br>
  
Un demultiplexor hace lo contrario del MUX: toma una sola entrada de datos (D) y la envía a una de varias salidas (la que indica la salida de selección), esta salida toma el valor lógico de la entrada y las demás quedan en 0. 

---

### 🧩 Partes de un DEMUX

| 🏷️ Parte | 📖 Explicación | 💡 Ejemplo explicativo |
| :--- | :--- | :--- |
| <span style="color: #198754;"><strong>📥 1 entrada de datos (D)</strong></span> | En todo DEMUX siempre habrá una sola entrada de datos, que es la señal que se quiere repartir | Entrada <strong>D</strong> |
| <span style="color: #6f42c1;"><strong>🎛️ n líneas de selección</strong></span> | Son los bits que indican por cuál salida debe salir el dato. Si hay 2<sup>n</sup> salidas, <em>n</em> es la cantidad de bits de selección | <code>8 = 2<sup>3</sup></code> por lo tanto <code>n = 3</code>, es decir, habrá tres líneas de selección (3 bits) |
| <span style="color: #0066cc;"><strong>📤 2<sup>n</sup> salidas</strong></span> | La cantidad de salidas es una potencia de 2. Solo una toma el valor de D y las demás quedan en 0 | <code>2<sup>3</sup> = 8</code> (Y<sub>0</sub>, Y<sub>1</sub>, Y<sub>2</sub>, Y<sub>3</sub>, Y<sub>4</sub>, Y<sub>5</sub>, Y<sub>6</sub>, Y<sub>7</sub>) |
| <span style="color: #d97706;"><strong>🔌 OPCIONAL:</strong></span> <strong>Entrada de habilitación</strong> | Es una entrada adicional que apaga o enciende el circuito | <ul><li><span style="color: #198754;"><strong>Si E=1</strong></span> el DEMUX funciona de manera normal.</li><li><span style="color: #dc3545;"><strong>Si E=0</strong></span> sin importar D ni las líneas de selección, todas las salidas (Y) valen 0.</li></ul> |

<br>

---

***Ejemplo*** <br>
**DEMUX 1:4** <br>
| S1 | S0 | Y0 | Y1 | Y2 | Y3 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 0 | 0 | D | 0 | 0 | 0 |
| 0 | 1 | 0 | D | 0 | 0 |
| 1 | 0 | 0 | 0 | D | 0 |
| 1 | 1 | 0 | 0 | 0 | D |

<br>

<div align="center">
<pre><code>Y<sub>0</sub> = D · S<sub>1</sub>' · S<sub>0</sub>'      Y<sub>1</sub> = D · S<sub>1</sub>' · S<sub>0</sub>      Y<sub>2</sub> = D · S<sub>1</sub> · S<sub>0</sub>'      Y<sub>3</sub> = D · S<sub>1</sub> · S<sub>0</sub></code></pre>
</div>

<br>

---

### 🧮 Ecuación Booleana

Para enviar el dato a una sola salida y dejar las demás en 0 también se usan compuertas **AND**, pero aquí **no lleva OR**, porque cada salida es independiente. Tomando el ejemplo anterior (DEMUX 1:4):

<div align="center">
<pre><code>Y<sub>0</sub> = D · S<sub>1</sub>' · S<sub>0</sub>'
Y<sub>1</sub> = D · S<sub>1</sub>' · S<sub>0</sub>
Y<sub>2</sub> = D · S<sub>1</sub> · S<sub>0</sub>'
Y<sub>3</sub> = D · S<sub>1</sub> · S<sub>0</sub></code></pre>
</div>

<div style="background-color: #f8f9fa; border-left: 5px solid #6f42c1; padding: 14px; border-radius: 6px; margin-bottom: 16px;">
  <strong style="color: #4c2889;">⚙️ ¿Cómo funciona la selección?</strong>
  <ul>
    <li><strong>Minitérminos en S:</strong> Cada ecuación contiene un minitérmino en <code>S</code> (donde <code>S = 1</code> y <code>S' = 0</code>), y cada combinación de <code>S</code> representa un número binario (<code>00</code>, <code>01</code>, <code>10</code> y <code>11</code>) que corresponde a una salida (<code>Y0</code>, <code>Y1</code>, <code>Y2</code> y <code>Y3</code>).</li>
    <li><strong>Condición de paso (AND):</strong> El dato <code>D</code> solo llega a la salida cuando el minitérmino de <code>S</code> vale <code>1</code>, ya que así la multiplicación (<strong>AND</strong>) no cambia el valor de <code>D</code>.</li>
    <li><strong>Salidas bloqueadas:</strong> En las demás salidas el minitérmino de <code>S</code> vale <code>0</code>, y como cualquier cosa multiplicada por <code>0</code> da <code>0</code>, esas salidas quedan apagadas sin importar el valor de <code>D</code>.</li>
  </ul>
</div>

#### 📊 Comportamiento de la compuerta AND como llave de paso

<div align="center">

| Minitérmino de S (`1` = seleccionado) | Dato (`D`) | Salida (`Y`) | Estado |
| :---: | :---: | :---: | :--- |
| `0` | `0` | `0` | 🔴 Bloqueado (apagado) |
| `0` | `1` | `0` | 🔴 Bloqueado (apagado) |
| `1` | `0` | `0` | 🟢 Pasa el dato `D` (`0`) |
| `1` | `1` | `1` | 🟢 Pasa el dato `D` (`1`) |

</div>

#### 🧪 Ejemplo numérico

Con `D = 1` y `S₁ S₀ = 10` (que es 2 en decimal):

| Salida | Cálculo | Resultado |
| :---: | :--- | :---: |
| `Y0` | `1 · 1 · 0 = 0` | `0` |
| `Y1` | `1 · 1 · 1 · ... ` | `0` |
| `Y2` | `1 · 1 · 1 = 1` | `1` ✅ |
| `Y3` | `1 · 1 · 0 = 0` | `0` |

El dato `D` sale únicamente por **Y2**. Si `D = 0`, todas las salidas valen `0`.

---

### 🔧 Formación del circuito

Siguiendo el ejemplo del DEMUX 1:4 se necesitará:

* 2 NOT (para S₁' y S₀').
* 4 AND de tres entradas (una por cada salida).

Total: **6 compuertas**. <br>

***🔢 Integrados de la familia 74LS*** <br>
| Integrado | Qué contiene |
| :--- | :--- |
| 74LS139 | 2 demultiplexores 1:4  |
| 74LS155 | 2 demultiplexores 1:4 |
| 74LS138 | 1 demultiplexor 1:8 |
| 74LS154 | 1 demultiplexor 1:16 |

<br>

<div align="center">
  <img src="../Imagenes/DEMUX_4Salidas.png" alt="Circuito lógico de un Demultiplexor de 4 salidas" width="600">
  <p><em>Figura 6: Implementación de un Demultiplexor 1:4 con compuertas lógicas (NOT y AND).</em></p>
</div>

---

### 🔧 Expansión

Un DEMUX más grande se arma con DEMUX más chicos. Un **DEMUX 1:16** es un **DEMUX 1:2** controlado por **S3**, que decide cuál de los dos DEMUX 1:8 recibe el dato **D**, más dos **DEMUX 1:8** que comparten **S2, S1 y S0**.

<div align="center">
  <img src="../Imagenes/demux_4.webp" alt="Demultiplexor de 4 salidas" width="550">
  <p><em>Figura 7: Demultiplexor 1:4.</em></p>
</div>

> **Nota sobre la figura:** en la imagen original las líneas de selección están rotuladas S1, S2, S3 y S1. En este cuaderno se leen así: **S3** controla el DEMUX 1x2, y **S2, S1 y S0** se comparten con los dos DEMUX 1:8. La entrada **I** de la figura es la entrada **D**.

| S3 | S2 S1 S0 | DEMUX 1:8 que recibe D | Salida que toma el valor de D |
| :---: | :---: | :---: | :---: |
| 0 | 000 a 111 | Inferior | Y0 a Y7 |
| 1 | 000 a 111 | Superior | Y8 a Y15 |

El DEMUX 1:8 que **no** es elegido recibe 0, así que todas sus salidas quedan en 0.

**Ejemplo:** con S3 S2 S1 S0 = 1010 (que es 10 en decimal), el dato sale por **Y10**.

<br>

<div align="center" style="background-color: #f6f8fa; border: 2px solid #0969da; border-radius: 10px; padding: 12px 20px; margin: 20px 0;">
  <h3 style="margin: 0; color: #0969da;">⚡ EJERCICIOS ⚡</h3>
  <sub>Práctica de Demultiplexores (DEMUX)</sub>
</div>

<br>

<div style="background-color: #fff8c5; border-left: 5px solid #d4a72c; padding: 14px; border-radius: 6px; margin-bottom: 16px;">
  <strong style="color: #7d4e00; font-size: 1.05em;">📋 Enunciado:</strong><br>
  Un sistema de distribución automatizado recibe una señal única de control (<code>D</code>) desde un microcontrolador y debe enrutarla hacia <strong>8 actuadores independientes</strong> (<code>Y<sub>0</sub></code> a <code>Y<sub>7</sub></code>), gobernados por un selector binario de 3 bits y un botón maestro de seguridad (<code>E</code>). Si se envía el dato <code>D = 1</code> con el interruptor maestro activo (<code>E = 1</code>), <strong>¿qué arquitectura de demultiplexor (dimensionamiento, ecuaciones booleanas, compuertas, integrado comercial y expansión) se requiere, y cuál será el estado en las 8 salidas cuando <code>S<sub>2</sub>S<sub>1</sub>S<sub>0</sub> = 101</code> y luego al desactivar <code>E = 0</code>?</strong>
</div>

| Parámetro | Valor / Dato |
| :--- | :--- |
| **Tipo de circuito** | DEMUX 1:8 con Enable |
| **Entrada de datos** | `D` (1 línea única de información) |
| **Líneas de selección (<em>n</em>)** | <code>n = 3</code> (<code>S<sub>2</sub></code>, <code>S<sub>1</sub></code>, <code>S<sub>0</sub></code>) |
| **Salidas de datos (2<sup>n</sup>)** | <code>2<sup>3</sup> = 8</code> (<code>Y<sub>0</sub></code> a <code>Y<sub>7</sub></code>) |
| **Habilitación** | `E` (1 bit de control maestro) |
| **Compuertas discretas** | 3 NOT + 8 AND (5 ent.: `D`, `E`, `S2`, `S1`, `S0`) = **11 compuertas** *(sin OR)* |
| **Integrado 74LS** | **74LS138** (Decodificador/DEMUX 1:8 usando Enable como entrada de datos) |
| **Expansión** | 1 DEMUX 1:2 en `S2` + 2 DEMUX 1:4 (**74LS139**) compartiendo `S1, S0` |

<br>

<div align="center">
<pre><code>Y<sub>0</sub> = E · D · S<sub>2</sub>' · S<sub>1</sub>' · S<sub>0</sub>'       Y<sub>4</sub> = E · D · S<sub>2</sub> · S<sub>1</sub>' · S<sub>0</sub>'
Y<sub>1</sub> = E · D · S<sub>2</sub>' · S<sub>1</sub>' · S<sub>0</sub>        Y<sub>5</sub> = E · D · S<sub>2</sub> · S<sub>1</sub>' · S<sub>0</sub>
Y<sub>2</sub> = E · D · S<sub>2</sub>' · S<sub>1</sub> · S<sub>0</sub>'        Y<sub>6</sub> = E · D · S<sub>2</sub> · S<sub>1</sub> · S<sub>0</sub>'
Y<sub>3</sub> = E · D · S<sub>2</sub>' · S<sub>1</sub> · S<sub>0</sub>         Y<sub>7</sub> = E · D · S<sub>2</sub> · S<sub>1</sub> · S<sub>0</sub></code></pre>
</div>

<br>

<div align="center">
  <img src="../Imagenes/DEMUX_8Salidas_Compuertas.png" alt="Circuito lógico de un Demultiplexor 1:8 con Enable" width="650">
  <p><em>Figura 8: Simulación en Logisim del Demultiplexor 1:8 con entrada de habilitación (E).</em></p>
</div>

<div align="center">

| `E` | `D` | `S2 S1 S0` | Canal activo | `Y0` | `Y1` | `Y2` | `Y3` | `Y4` | `Y5` | `Y6` | `Y7` |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| `1` | `1` | `000` | `Y0` | `1` | `0` | `0` | `0` | `0` | `0` | `0` | `0` |
| `1` | `1` | `001` | `Y1` | `0` | `1` | `0` | `0` | `0` | `0` | `0` | `0` |
| `1` | `1` | `010` | `Y2` | `0` | `0` | `1` | `0` | `0` | `0` | `0` | `0` |
| `1` | `1` | `011` | `Y3` | `0` | `0` | `0` | `1` | `0` | `0` | `0` | `0` |
| `1` | `1` | `100` | `Y4` | `0` | `0` | `0` | `0` | `1` | `0` | `0` | `0` |
| **`1`** | **`1`** | **`101`** | **`Y5`** | **`0`** | **`0`** | **`0`** | **`0`** | **`0`** | **`1`** | **`0`** | **`0`** |
| `1` | `1` | `110` | `Y6` | `0` | `0` | `0` | `0` | `0` | `0` | `1` | `0` |
| `1` | `1` | `111` | `Y7` | `0` | `0` | `0` | `0` | `0` | `0` | `0` | `1` |
| **`0`** | **`X`** | **`XXX`** | *Ninguno* | **`0`** | **`0`** | **`0`** | **`0`** | **`0`** | **`0`** | **`0`** | **`0`** |

</div>

<div style="background-color: #e6ffed; border-left: 5px solid #198754; padding: 12px; border-radius: 6px; margin-top: 12px;">
  <strong style="color: #146c43;">✅ Respuesta:</strong> Con <code>E = 1</code>, <code>D = 1</code> y <code>S<sub>2</sub>S<sub>1</sub>S<sub>0</sub> = 101</code>, el dato se enruta únicamente hacia la salida <strong><code>Y<sub>5</sub> = 1</code></strong> mientras las demás quedan en <code>0</code>; al desactivar <code>E = 0</code>, <strong>todas las salidas (<code>Y<sub>0</sub></code> a <code>Y<sub>7</sub></code>) pasan a <code>0</code></strong>.
</div>

<br>

---


