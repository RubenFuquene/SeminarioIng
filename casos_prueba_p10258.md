# Casos de Prueba - Problema p10258

## CP-001

**ID:** CP-001

**Descripcion:** Validar el comportamiento cuando solo un equipo tiene aciertos

**Precondiciones:** El programa debe reconocer al equipo con entrega correcta pero no al equipo sin entrega correcta.

**Datos de entrada:**

```txt
1

1 2 10 I
3 1 11 I
1 2 19 R
1 2 21 C
1 1 25 C
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar entrada desordenada.
4. Verificar la salida generada.

**Resultado esperado:**

```txt
1 2 66
3 0 0
```

---

## CP-002

**ID:** CP-002

**Descripcion:** Validar el comportamiento cuando ningún equipo entrega correctamente.

**Precondiciones:** El programa debe reconocer equipos sin entregas correctas.

**Datos de entrada:**

```txt
1

1 1 10 I
3 1 11 I
```

**Procesamiento:**

```txt
No hay entregas correctas
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar casos sin entregas correctas.
4. Revisar la salida.

**Resultado esperado:**

```txt
1 0 0
3 0 0
```

---

## CP-003

**ID:** CP-003

**Descripcion:** Validar el comportamiento cuando dos equpos empatan.

**Precondiciones:** El programa debe ordenar equipos que empatan en cantidad de aciertos.

**Datos de entrada:**

```txt
1

1 2 17 C
3 1 15 C
```

**Procesamiento:**

```txt
equipo 1 aciertos: 1
equipo 3 aciertos: 1
```

**Pasos:**

1. Ejecutar el programa.
2. Ingresar puntajes de equipos empatados
4. Revisar la salida.

**Resultado esperado:**

```txt
3 1 15
1 1 17
```

---

## CP-004

**ID:** CP-004

**Descripcion:** Validar el comportamiento cuando dos equpos empatan y tienen el mismo tiempo.

**Precondiciones:** El programa debe ordenar equipos que empatan en cantidad de aciertos y tiempo consumido.

**Datos de entrada:**

```txt
1

1 3 12 C
3 2 12 C
```

**Pasos:**

1. Ejecutar el programa.
3. Ingresar puntajes de equipos empatados y con el mismo tiempo.
4. Verificar la cantidad minima de pasos.

**Resultado esperado:**

```txt
1 1 12
3 1 12

**Pasos:**

1. Ejecutar el programa.
3. Ingresar puntajes de equipos empatados y con el mismo tiempo.
4. Verificar la cantidad minima de pasos.

**Resultado esperado:**

```txt
1 1 12
3 1 12
```
```