# Casos de Prueba - Problema p100

## CP-001

**ID:** CP-001

**Descripcion:**  Validar el comportamiento cuando la entrada no está ordenada.

**Precondiciones:** El programa debe reconocer al equipo con entrega correcta pero no al equipo sin entrega correcta.

**Datos de entrada:**

```txt
0 1
```
**Procesamiento:**
```txt
i MIN(1e,
j - MAX(1e,
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar dos números en Orden de mayor a menor,
3. Verificar la salida generada.

**Resultado esperado:**

```txt
1 10 20
```

---

## CP-002

**ID:** CP-002

**Descripcion:** Validar una distancia grande.

**Precondiciones:** El programa debe ser capaz de procesar entradas grandes.

**Datos de entrada:**

```txt
900 1000
```
**Pasos:**

1. Ejecutar el programa.
2. Ingresar los valores gee leee .
3. Verificar la cantidad minima de pasos.

**Resultado esperado:**

```txt
900 1000 174
```

---

## CP-003

**ID:** CP-003

**Descripcion:** Validar una distancia que corresponde a O.

**Precondiciones:** El programa debe calcular correctamente casos donde la distancia es e .

**Datos de entrada:**

```txt
50 50
```

**Procesamiento:**

```txt
n=0
i=50
j=50
i==j
n++
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar los valores 50 5e .
3. Verificar la salida.

**Resultado esperado:**

```txt
50 50 1
```

---

## CP-004

**ID:** CP-004

**Descripcion:** Validar entradas erroneas

**Precondiciones:** El programa debe excluir correctamente valores no admitidos.

**Datos de entrada:**

```txt
10000 99
8 -1
```
**Procesamiento:**
```txt
i>9999
No valido

j<0
No valido
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar los valores Iaaea .
3. Ingresar los valores 8 -1 .
4. Verificar la salida.

**Resultado esperado:**

```txt
Error, entrada fuera del intervalo admitido.
Error, entrada fuera del intervalo admitido.
```