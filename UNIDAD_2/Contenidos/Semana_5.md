# SELECCIÓN Y CODIFICACIÓN DE DATOS 
## Multiplexor
### Definición: 
Un multiplexor o selector de datos es aquel que tiene **varias entradas** pero solo **una salida**, es decir, solo deja pasar una de las entradas mediante una selección o control generado por bits (líneas de selección).
### Partes de un MUX 
| Parte | Explicación | Ejemplo |
| :-: | :-: | :-: |
| 2ⁿ entradas de datos | Los datos de entrada solo pueden ser potencias de 2 | 2³ = 8 (I0, I1, I2, I3, I4, I5, I6, I7) |
| n líneas de selección | De la formula 2ⁿ que es igual a las entradas n es la cantidad de bits que controlan la selección | 8 = 2³ por lo tanto n = 3 es decir habrá tres líneas de selección (3 bits) | 
| 1 salida (Y) | En todo MUX siempre habrá una sola salida | Salida Y | 
| **OPCIONAL:** Entrada de habilitación | Es una entrada adicional que apaga o enciende el circuito | <ul><li>Si E=1 el MUX funciona de manera normal.</li><li>Si E=0 sin importar las entradas o las líneas de selección la salida (Y) es igual a 0.</li></ul> | 
***EJEMPLOS:***
**MUX 2:1**


