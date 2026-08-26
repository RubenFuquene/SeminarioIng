# Casos de Prueba - Problema p846

## CP-001

**ID:** CP-001

**Descripcion:** Validar el comportamiento cuando la distancia entre `x` y `y` es cero.

**Precondiciones:** El programa debe estar disponible para recibir datos por entrada estandar.

**Datos de entrada:**

```txt
1
0 0
```

**Recorrido de pasos:**

```txt
0 = 0
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar el numero de casos de prueba.
3. Ingresar los valores `x = 0` y `y = 0`.
4. Verificar la salida generada.

**Resultado esperado:**

```txt
0
```

---

## CP-002

**ID:** CP-002

**Descripcion:** Validar el minimo recorrido posible con distancia `1`.

**Precondiciones:** El programa debe aceptar valores donde `0 <= x <= y < 2^31`.

**Datos de entrada:**

```txt
1
0 1
```

**Recorrido de pasos:**

```txt
1 = 1
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar un caso de prueba.
3. Ingresar los valores `0 1`.
4. Revisar el numero minimo de pasos calculado.

**Resultado esperado:**

```txt
1
```

---

## CP-003

**ID:** CP-003

**Descripcion:** Validar una distancia pequena que requiere dos pasos de longitud `1`.

**Precondiciones:** El programa debe calcular correctamente distancias pequenas.

**Datos de entrada:**

```txt
1
0 2
```

**Recorrido de pasos:**

```txt
1 + 1 = 2
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar un caso de prueba.
3. Ingresar los valores `0 2`.
4. Comparar la salida con el resultado esperado.

**Resultado esperado:**

```txt
2
```

---

## CP-004

**ID:** CP-004

**Descripcion:** Validar una distancia pequena impar.

**Precondiciones:** El programa debe respetar que el primer y ultimo paso sean de longitud `1`.

**Datos de entrada:**

```txt
1
0 3
```

**Recorrido de pasos:**

```txt
1 + 1 + 1 = 3
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar un caso de prueba.
3. Ingresar los valores `0 3`.
4. Verificar la cantidad minima de pasos.

**Resultado esperado:**

```txt
3
```

---

## CP-005

**ID:** CP-005

**Descripcion:** Validar una distancia que corresponde a un cuadrado perfecto.

**Precondiciones:** El programa debe calcular correctamente casos donde la distancia es `4`.

**Datos de entrada:**

```txt
1
0 4
```

**Recorrido de pasos:**

```txt
1 + 2 + 1 = 4
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar un caso de prueba.
3. Ingresar los valores `0 4`.
4. Verificar la salida.

**Resultado esperado:**

```txt
3
```

---

## CP-006

**ID:** CP-006

**Descripcion:** Validar una distancia justo despues de un cuadrado perfecto.

**Precondiciones:** El programa debe manejar correctamente los cambios de rango entre cantidades de pasos.

**Datos de entrada:**

```txt
1
0 5
```

**Recorrido de pasos:**

```txt
1 + 2 + 1 + 1 = 5
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar un caso de prueba.
3. Ingresar los valores `0 5`.
4. Revisar el resultado.

**Resultado esperado:**

```txt
4
```

---

## CP-007

**ID:** CP-007

**Descripcion:** Validar una distancia intermedia dentro del mismo rango de pasos.

**Precondiciones:** El programa debe calcular correctamente distancias mayores a `5`.

**Datos de entrada:**

```txt
1
0 6
```

**Recorrido de pasos:**

```txt
1 + 2 + 2 + 1 = 6
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar un caso de prueba.
3. Ingresar los valores `0 6`.
4. Verificar la salida.

**Resultado esperado:**

```txt
4
```

---

## CP-008

**ID:** CP-008

**Descripcion:** Validar el primer caso de ejemplo del enunciado.

**Precondiciones:** El programa debe producir la misma salida que el ejemplo oficial.

**Datos de entrada:**

```txt
1
45 48
```

**Recorrido de pasos:**

```txt
1 + 1 + 1 = 3
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar un caso de prueba.
3. Ingresar los valores `45 48`.
4. Comparar la salida con el ejemplo esperado.

**Resultado esperado:**

```txt
3
```

---

## CP-009

**ID:** CP-009

**Descripcion:** Validar el segundo caso de ejemplo del enunciado.

**Precondiciones:** El programa debe producir la misma salida que el ejemplo oficial.

**Datos de entrada:**

```txt
1
45 49
```

**Recorrido de pasos:**

```txt
1 + 2 + 1 = 4
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar un caso de prueba.
3. Ingresar los valores `45 49`.
4. Comparar la salida con el resultado esperado.

**Resultado esperado:**

```txt
3
```

---

## CP-010

**ID:** CP-010

**Descripcion:** Validar el tercer caso de ejemplo del enunciado.

**Precondiciones:** El programa debe producir la misma salida que el ejemplo oficial.

**Datos de entrada:**

```txt
1
45 50
```

**Recorrido de pasos:**

```txt
1 + 2 + 1 + 1 = 5
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar un caso de prueba.
3. Ingresar los valores `45 50`.
4. Verificar la salida.

**Resultado esperado:**

```txt
4
```

---

## CP-011

**ID:** CP-011

**Descripcion:** Validar una distancia de `9`, correspondiente a un cuadrado perfecto.

**Precondiciones:** El programa debe manejar correctamente distancias calculadas a partir de `y - x`.

**Datos de entrada:**

```txt
1
10 19
```

**Recorrido de pasos:**

```txt
1 + 2 + 3 + 2 + 1 = 9
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar un caso de prueba.
3. Ingresar los valores `10 19`.
4. Verificar el numero minimo de pasos.

**Resultado esperado:**

```txt
5
```

---

## CP-012

**ID:** CP-012

**Descripcion:** Validar una distancia justo despues de `9`.

**Precondiciones:** El programa debe identificar correctamente cuando aumenta el numero minimo de pasos.

**Datos de entrada:**

```txt
1
10 20
```

**Recorrido de pasos:**

```txt
1 + 2 + 2 + 2 + 2 + 1 = 10
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar un caso de prueba.
3. Ingresar los valores `10 20`.
4. Revisar la salida.

**Resultado esperado:**

```txt
6
```

---

## CP-013

**ID:** CP-013

**Descripcion:** Validar una distancia consecutiva que mantiene el mismo numero minimo de pasos.

**Precondiciones:** El programa debe manejar rangos donde varias distancias comparten la misma cantidad minima de pasos.

**Datos de entrada:**

```txt
1
10 21
```

**Recorrido de pasos:**

```txt
1 + 2 + 3 + 2 + 2 + 1 = 11
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar un caso de prueba.
3. Ingresar los valores `10 21`.
4. Verificar el resultado.

**Resultado esperado:**

```txt
6
```

---

## CP-014

**ID:** CP-014

**Descripcion:** Validar una distancia de `16`, correspondiente a un cuadrado perfecto.

**Precondiciones:** El programa debe calcular correctamente distancias medianas.

**Datos de entrada:**

```txt
1
100 116
```

**Recorrido de pasos:**

```txt
1 + 2 + 3 + 4 + 3 + 2 + 1 = 16
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar un caso de prueba.
3. Ingresar los valores `100 116`.
4. Verificar la salida.

**Resultado esperado:**

```txt
7
```

---

## CP-015

**ID:** CP-015

**Descripcion:** Validar una distancia justo despues de un cuadrado perfecto mayor.

**Precondiciones:** El programa debe incrementar correctamente los pasos cuando la distancia supera un cuadrado perfecto.

**Datos de entrada:**

```txt
1
100 117
```

**Recorrido de pasos:**

```txt
1 + 2 + 3 + 4 + 3 + 2 + 1 + 1 = 17
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar un caso de prueba.
3. Ingresar los valores `100 117`.
4. Revisar el resultado.

**Resultado esperado:**

```txt
8
```

---

## CP-016

**ID:** CP-016

**Descripcion:** Validar una distancia que requiere un paso adicional dentro de un rango superior.

**Precondiciones:** El programa debe manejar correctamente distancias medianas no cuadradas.

**Datos de entrada:**

```txt
1
100 120
```

**Recorrido de pasos:**

```txt
1 + 2 + 3 + 4 + 4 + 3 + 2 + 1 = 20
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar un caso de prueba.
3. Ingresar los valores `100 120`.
4. Verificar la salida.

**Resultado esperado:**

```txt
8
```

---

## CP-017

**ID:** CP-017

**Descripcion:** Validar una distancia de `24`, cercana al cuadrado perfecto `25`.

**Precondiciones:** El programa debe calcular correctamente valores cercanos a cambios de rango.

**Datos de entrada:**

```txt
1
1000 1024
```

**Recorrido de pasos:**

```txt
1 + 2 + 3 + 4 + 4 + 4 + 3 + 2 + 1 = 24
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar un caso de prueba.
3. Ingresar los valores `1000 1024`.
4. Revisar el numero minimo de pasos.

**Resultado esperado:**

```txt
9
```

---

## CP-018

**ID:** CP-018

**Descripcion:** Validar una distancia de `25`, correspondiente a un cuadrado perfecto.

**Precondiciones:** El programa debe calcular correctamente cuadrados perfectos mayores.

**Datos de entrada:**

```txt
1
1000 1025
```

**Recorrido de pasos:**

```txt
1 + 2 + 3 + 4 + 5 + 4 + 3 + 2 + 1 = 25
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar un caso de prueba.
3. Ingresar los valores `1000 1025`.
4. Verificar la salida.

**Resultado esperado:**

```txt
9
```

---

## CP-019

**ID:** CP-019

**Descripcion:** Validar el limite superior con distancia minima.

**Precondiciones:** El programa debe aceptar valores cercanos al maximo permitido `2^31 - 1`.

**Datos de entrada:**

```txt
1
2147483646 2147483647
```

**Recorrido de pasos:**

```txt
1 = 1
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar un caso de prueba.
3. Ingresar los valores `2147483646 2147483647`.
4. Verificar que no ocurra error por valores grandes.

**Resultado esperado:**

```txt
1
```

---

## CP-020

**ID:** CP-020

**Descripcion:** Validar el caso de mayor distancia posible dentro de las restricciones.

**Precondiciones:** El programa debe manejar valores grandes sin desbordamiento ni tiempos excesivos.

**Datos de entrada:**

```txt
1
0 2147483647
```

**Recorrido de pasos:**

```txt
No se detalla el recorrido completo porque requiere 92681 pasos.
Distancia: 2147483647
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar un caso de prueba.
3. Ingresar los valores `0 2147483647`.
4. Verificar que el programa calcule la respuesta correctamente.

**Resultado esperado:**

```txt
92681
```
