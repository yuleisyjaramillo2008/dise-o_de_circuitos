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

**Explicación de la ECUACIÓN BOOLEANA**


