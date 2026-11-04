<div align="center">

# ⚙️ `SISTEMAS NUMÉRICOS, CÓDIGOS Y COMPUERTAS LÓGICAS` ⚙️

</div>

## 📡 1. Tipos de Señales

> 🌊 **Señal Analógica**  
> Es continua y adopta infinitos valores. <br>
> ![Señal Analógica](../../señal_analógica.webp)

> 💻 **Señal Digital**  
> Solo adopta dos valores (`0` y `1`). <br>
> ![Señal Digital](../../señal_digital.webp)

---

## 🧩2. Circuitos combinacionales
Circuito que aplica la lógica combinacional para realizar una función específica.
### 🧠Lógica Combinacional  
> Su salida en cualquier instante depende **únicamente de sus entradas en ese mismo momento**.

* ❌ **Sin memoria:** No almacena ni recuerda datos de operaciones pasadas.  
* 🔄 **Cambio directo:** Si las entradas cambian, la salida cambia inmediatamente.

---

## ⚙️3. TRANSISTOR
Es un semiconductor que funciona como interruptor eléctrico o como amplificador de señales.
> Varios transistores interconectados forman una compuerta lógica. 

<table>
  <tr>
    <td width="50%" align="center" valign="top">
      <img src="../../transistor.jpg" alt="Transistor" width="100%">
    </td>
    <td width="50%" valign="top">
      <h3>Base</h3>
      <p>Controla el paso de la corriente, tiene una pequeña corriente (corriente de control) que controla el paso de corriente desde el Emisor al Colector mediante un diodo.</p>
      <h3>Emisor</h3>
      <p>Se encarga de emitir o "inyectar" los electrones al transitor.</p>
      <h3>Colector</h3>
      <p>Esta diseñada para "colectar" o recolectar los portadores de carga que vienen desde el emisor.</p>
    </td>
  </tr>
</table>

---

## ⚡ 4. Rangos de Voltaje en Señales Digitales
<p align="center">
  <img src="../../rango.png" alt="Rangos de Voltaje Digital" width="500">
</p>

#### 🚧 Zona Indefinida
- Franja de confusión para el receptor entre 0,8 V y 2,0 V.
- El componente no reconoce si recibe un 0 o un 1 y no sabe cómo actuar.
- Ocurre por ruido eléctrico, interferencias, pérdida de voltaje en cables largos o pines desconectados.

#### 🔄 Zona Solo de Paso
- Rango intermedio de salida ubicado entre 0,5 V y 2,7 V.
- Se llega a ella porque el cambio de 0 V a 5 V no es instantáneo y requiere un tiempo físico de conmutación.
- La señal únicamente atraviesa este rango a gran velocidad.

### 🛡️ Margen de Ruido

Es la protección que evita que la señal caiga en la **zona indefinida** cuando hay interferencias.

* **Margen Alto (0,7 V):** Lo que puede bajar un 1 en el camino y seguir leyéndose como 1.
* **Margen Bajo (0,3 V):** Lo que puede subir un 0 por interferencia y seguir leyéndose como 0.

Al superar estos límites, la señal cae en la **zona indefinida** y el sistema falla por confusión.

Ejemplo de falla: si sale un 0 de 0,5 V y un motor cercano le suma 0,4 V de ruido, la señal sube a 0,9 V y la compuerta ya no sabe qué hacer.

---

## 🔢 5. Posiciones Binarias
* Cada posición vale el doble de la anterior (1, 2, 4, 8...); solo sumas los valores donde hay un **1**.
* **Bit:** Un solo dígito (0 o 1). **Byte:** Conjunto de 8 bits.

---

## 🔢 6. De Decimal a Binario: Dividir entre 2

Para convertir un número decimal a binario se divide sucesivamente entre 2 y se guardan los restos.

#### Pasos:
1. Dividir el número entre 2.
2. Anotar el **resto** (0 o 1) y guardar el **cociente**.
3. Repetir la división con el nuevo cociente hasta llegar a 0.
4. Leer los restos de **abajo hacia arriba** para obtener el número binario.

---

#### Ejemplo (Número 25):

| División | Cociente | Resto |
| :---: | :---: | :---: |
| 25 ÷ 2 | 12 | **1** |
| 12 ÷ 2 | 6 | **0** |
| 6 ÷ 2 | 3 | **0** |
| 3 ÷ 2 | 1 | **1** |
| 1 ÷ 2 | 0 | **1** |

**Resultado:** 25₁₀ = **11001₂**

* **Comprobación:** 16 + 8 + 1 = 25

---

## 🔣 7. Hexadecimal y Octal: Abreviaturas del Binario

### 1. Hexadecimal (Base 16)
- **Significado:** Sistema de numeración de base 16 que utiliza los números del 0 al 9 y las letras de la A a la F.
- **Uso de la tabla:** Del 10 en adelante se emplean letras para evitar escribir dos dígitos en una sola posición.
- **Agrupación y regla de ceros:** Agrupa el código binario en bloques de **4 bits** de derecha a izquierda. Si al último grupo le faltan bits, se completan con ceros a la izquierda.

| Decimal | Hexadecimal |
| :---: | :---: |
| 10 | **A** |
| 11 | **B** |
| 12 | **C** |
| 13 | **D** |
| 14 | **E** |
| 15 | **F** |

- **Ejemplo (Número 157 = 10011101₂):**
  1. Separa de 4 en 4 bits desde la derecha: `1001` | `1101`.
  2. Convierte cada bloque: `1001` = 9 y `1101` = 13.
  3. Reemplaza el 13 por la letra **D**.
  - **Resultado Hexadecimal:** **9D₁₆**

### 2. Octal (Base 8)
- **Significado:** Sistema de numeración posicional de base 8 que utiliza únicamente los dígitos del 0 al 7.
- **Por qué se utiliza:** Métodos sencillos para representar binarios largos sin necesidad de usar letras, ya que ningún bloque supera el valor de 7.
- **Agrupación y regla de ceros:** Agrupa el código binario en bloques de **3 bits** de derecha a izquierda. Si el primer grupo no completa los 3 bits, se le agregan ceros a la izquierda.
- **Ejemplo (Número 157 = 10011101₂):**
  1. Separa de 3 en 3 bits desde la derecha: `010` | `011` | `101` *(se agrega un 0 a la izquierda para completar)*.
  2. Convierte cada bloque a decimal: `010` = 2, `011` = 3 y `101` = 5.
  - **Resultado Octal:** **235₈**

---

## 8. 
