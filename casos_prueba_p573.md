# Casos de Prueba - Problema p573 

## CP-001

**ID:** CP-001

**Descripcion:** Validar el fin de la entrada cuando `H = 0` es el primer y unico valor recibido.

**Precondiciones:** El programa debe estar disponible para recibir datos por entrada estandar.

**Datos de entrada:**

```txt
0 0 0 0
```

**Recorrido de pasos:**

```txt
H = 0 -> se detiene la lectura, no se procesa ningun caso
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar la linea `0 0 0 0`.
3. Verificar que no se genere ninguna linea de salida.

**Resultado esperado:**

```txt
(sin salida)
```

---

## CP-002

**ID:** CP-002

**Descripcion:** Validar el caso limite en que la altura escalada en un dia es exactamente igual a la altura del pozo (no debe considerarse exito, ya que se exige superarla estrictamente).

**Precondiciones:** El programa debe aplicar la condicion "altura > H" y no "altura >= H" para determinar el exito.

**Datos de entrada:**

```txt
5 5 5 1
0 0 0 0
```

**Recorrido de pasos:**

```txt
Dia 1: sube 5' -> altura 5' (5' no es mayor que H=5', no hay exito) -> resbala 5' -> altura 0'
Dia 2: sube 5' - 10%x5' = 4.95' -> altura 4.95' (no supera 5') -> resbala 5' -> altura -0.05' (< 0)
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar la linea `5 5 5 1`.
3. Ingresar la linea `0 0 0 0` para finalizar la entrada.
4. Verificar la salida generada.

**Resultado esperado:**

```txt
failure on day 2
```

---

## CP-003

**ID:** CP-003

**Descripcion:** Validar los valores minimos permitidos por el enunciado (`H, U, D, F = 1`).

**Precondiciones:** Todos los parametros deben estar en el rango `1 <= H, U, D, F <= 100`.

**Datos de entrada:**

```txt
1 1 1 1
0 0 0 0
```

**Recorrido de pasos:**

```txt
Dia 1: sube 1' -> altura 1' (no supera H=1') -> resbala 1' -> altura 0'
Dia 2: sube 1' - 1%x1' = 0.99' -> altura 0.99' (no supera 1') -> resbala 1' -> altura -0.01' (< 0)
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar la linea `1 1 1 1`.
3. Ingresar la linea `0 0 0 0` para finalizar la entrada.
4. Verificar la salida generada.

**Resultado esperado:**

```txt
failure on day 2
```

---

## CP-004

**ID:** CP-004

**Descripcion:** Validar el caso en que la fatiga (`F = 100`) reduce la distancia escalada a 0' a partir del segundo dia, dejando que el caracol descienda 1' por noche hasta fracasar.

**Precondiciones:** El programa debe truncar a 0 la distancia escalada cuando la fatiga la vuelve negativa, y debe seguir aplicando el resbalon nocturno igualmente.

**Datos de entrada:**

```txt
50 10 1 100
0 0 0 0
```

**Recorrido de pasos:**

```txt
Dia 1: sube 10' -> altura 10' -> resbala 1' -> altura 9'
Dia 2 en adelante: sube 0' (la fatiga anula el avance) -> resbala 1' cada noche
Altura: 9, 8, 7, 6, 5, 4, 3, 2, 1, 0 (dia 10) y -1 (dia 11)
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar la linea `50 10 1 100`.
3. Ingresar la linea `0 0 0 0` para finalizar la entrada.
4. Verificar la salida generada.

**Resultado esperado:**

```txt
failure on day 11
```

---

## CP-005

**ID:** CP-005

**Descripcion:** Validar los valores maximos permitidos por el enunciado (`H, U, D, F = 100`).

**Precondiciones:** Todos los parametros deben estar en el rango `1 <= H, U, D, F <= 100`.

**Datos de entrada:**

```txt
100 100 100 100
0 0 0 0
```

**Recorrido de pasos:**

```txt
Dia 1: sube 100' -> altura 100' (no supera H=100') -> resbala 100' -> altura 0'
Dia 2: sube 100' - 100%x100' = 0' -> altura 0' -> resbala 100' -> altura -100' (< 0)
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar la linea `100 100 100 100`.
3. Ingresar la linea `0 0 0 0` para finalizar la entrada.
4. Verificar la salida generada.

**Resultado esperado:**

```txt
failure on day 2
```

---

## CP-006

**ID:** CP-006

**Descripcion:** Validar el caso de ejemplo presentado en el enunciado del problema, donde el caracol logra salir del pozo en el tercer dia.

**Precondiciones:** El programa debe calcular correctamente la reduccion fija por fatiga (`10% del avance del primer dia`) y acumularla dia a dia.

**Datos de entrada:**

```txt
6 3 1 10
0 0 0 0
```

**Recorrido de pasos:**

```txt
Dia 1: sube 3' -> altura 3' -> resbala 1' -> altura 2'
Dia 2: sube 3' - 0.3' = 2.7' -> altura 4.7' -> resbala 1' -> altura 3.7'
Dia 3: sube 3' - 0.6' = 2.4' -> altura 6.1' (> 6') -> exito
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar la linea `6 3 1 10`.
3. Ingresar la linea `0 0 0 0` para finalizar la entrada.
4. Verificar la salida generada.

**Resultado esperado:**

```txt
success on day 3
```

---

## CP-007

**ID:** CP-007

**Descripcion:** Validar el procesamiento de multiples casos de prueba en una sola ejecucion, combinando un caso de exito y uno de fracaso antes del `0 0 0 0` final.

**Precondiciones:** El programa debe procesar cada linea de forma independiente y en el orden en que se reciben, hasta encontrar la linea `0 0 0 0`.

**Datos de entrada:**

```txt
6 3 1 10
1 1 1 1
0 0 0 0
```

**Recorrido de pasos:**

```txt
Caso 1 (6 3 1 10): igual que CP-006 -> exito en el dia 3
Caso 2 (1 1 1 1): igual que CP-003 -> fracaso en el dia 2
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar la linea `6 3 1 10`.
3. Ingresar la linea `1 1 1 1`.
4. Ingresar la linea `0 0 0 0` para finalizar la entrada.
5. Verificar que se generen dos lineas de salida, una por cada caso, en el mismo orden en que fueron ingresados.

**Resultado esperado:**

```txt
success on day 3
failure on day 2
```

---

