# Diseño de Pruebas — Problema "Cultivo bacteriano programado por DNA" (p457)

## 1. Análisis del problema

**Función bajo prueba:** dado un arreglo `DNA[0..9]`, simular 40 platos de cultivo durante 50 días,donde el plato 20 inicia con densidad 1 y el resto en 0.

**Regla de transición:** para cada plato `i`, `K = izquierda + centro + derecha` (vecinos virtuales = 0 en los extremos). El nuevo valor del plato es `DNA[K]`.

**Salida:** por cada uno de los 50 días se imprime una línea de 40 caracteres, mapeando
`0→' '`, `1→'.'`, `2→'x'`, `3→'W'`. Entre las salidas de casos consecutivos va una línea en blanco.

**Detalle de implementación verificado empíricamente:** al simular contra el ejemplo del enunciado, la **primera línea impresa corresponde al estado inicial** (plato 19 = 1, resto 0) y las líneas 2 a 50 corresponden a los 49 días siguientes de evolución. Esto se confirmó reproduciendo carácter por
carácter las 10 líneas de muestra dadas en el enunciado con un simulador de referencia propio (sección 5). Cualquier plan de pruebas debe validar explícitamente este detalle, porque es la fuente más probable de errores "off-by-one" en las implementaciones de los estudiantes.

## 2. Técnicas de diseño aplicadas

- **Partición de equivalencia:** clases de valores de `DNA[K]` (extinción total, crecimiento máximo,
  crecimiento parcial) y clases de formato de entrada (un caso, varios casos).
- **Análisis de valores límite:** `K=0` (mínimo posible) y `K=9` (máximo posible); extremos físicos del
  arreglo de platos (índice 0 y 39); número de días (día 1 vs. día 50, para detectar iteraciones de más
  o de menos); número de casos de prueba `N` (mínimo N=1, N>1).
- **Pruebas estructurales / de caja blanca dirigida:** formato exacto de líneas (40 caracteres, 50
  líneas por caso, separación en blanco entre casos, manejo de líneas en blanco en la entrada).
- **Pruebas no funcionales:** carga/rendimiento con muchos casos.

## 3. Casos de prueba

Cada caso fue ejecutado contra un **simulador de referencia en Python**, verificado previamente contra el ejemplo oficial del enunciado (coincidencia exacta, carácter por carácter, de las 10 líneas de muestra). Por brevedad se muestran las primeras 10 líneas de cada caso (igual que hace el propio
enunciado) más la línea del día 50; el archivo completo de 50 líneas por caso está disponible y puede regenerarse con el script de la sección 5. En las tablas, `b` representa el carácter espacio (como en
el enunciado), para facilitar la lectura.

---

### TC01 — Caso base (ejemplo oficial del enunciado)
- **Técnica:** partición de equivalencia (caso "normal"/representativo) — caso de referencia obligatorio.
- **Objetivo:** validar la implementación contra la salida oficial proporcionada.
- **Entrada:** `N=1`; `DNA = [0,1,2,0,1,3,3,2,3,0]`
- **Resultado esperado (líneas 1-10, día 50 al final):**
```
bbbbbbbbbbbbbbbbbbb.bbbbbbbbbbbbbbbbbbbb
bbbbbbbbbbbbbbbbbb...bbbbbbbbbbbbbbbbbbb
bbbbbbbbbbbbbbbbb.xbx.bbbbbbbbbbbbbbbbbb
bbbbbbbbbbbbbbbb.bb.bb.bbbbbbbbbbbbbbbbb
bbbbbbbbbbbbbbb.........bbbbbbbbbbbbbbbb
bbbbbbbbbbbbbb.xbbbbbbbx.bbbbbbbbbbbbbbb
bbbbbbbbbbbbb.bbxbbbbbxbb.bbbbbbbbbbbbbb
bbbbbbbbbbbb...xxxbbbxxx...bbbbbbbbbbbbb
bbbbbbbbbbb.xb.WW.xbx.WW.bx.bbbbbbbbbbbb
bbbbbbbbbb.bbb.xxWb.bWxx.bbb.bbbbbbbbbbb
... (día 50): bbbbWWxxWWxWxWWxWxWWb.WWxxWbbWbbWbbbbbWW
```
- **Criterio de aceptación:** coincidencia exacta con el listado del enunciado (10 líneas) + coincidencia
  con el simulador de referencia para las 50 líneas.

---

### TC02 — Extinción total inmediata (valor límite `DNA[1]=0`)
- **Técnica:** valor límite + partición de equivalencia (clase "muere de inmediato").
- **Objetivo:** verificar que si `DNA[1]=0`, el único plato vivo (K=1) muere al primer paso y el
  cultivo entero queda extinto y estable el resto de la simulación.
- **Entrada:** `N=1`; `DNA = [0,0,0,0,0,0,0,0,0,0]`
- **Resultado esperado:** línea 1 con un único `.` en la posición 20; **todas las líneas 2 a 50 en blanco**.
- **Por qué importa:** detecta errores en el cálculo de `K` o en la indexación de `DNA`, y confirma que
  el estado "todo cero" es realmente un punto fijo estable.

---

### TC03 — Explosión máxima instantánea (valor límite `DNA[0]=3`)
- **Técnica:** valor límite (extremo superior) + caso extremo mencionado explícitamente en el enunciado.
- **Objetivo:** verificar que si `DNA[0]=3`, **todos** los platos vacíos (K=0, que es casi todo el
  tablero) se saturan a `W` en un solo paso, y que el tablero permanece saturado.
- **Entrada:** `N=1`; `DNA = [3,3,3,3,3,3,3,3,3,3]`
- **Resultado esperado:** línea 1 = estado inicial (un `.`); **líneas 2 a 50 completamente llenas de `W`**.
- **Por qué importa:** fuerza a que se ejercite `DNA[9]` (suma máxima, 3+3+3) en los platos internos,
  cubriendo el extremo superior del dominio de `K`.

---

### TC04 — Propagación mínima aislada (`DNA[1]=1`, resto 0)
- **Técnica:** partición de equivalencia — aísla el efecto de un único valor de la tabla DNA.
- **Objetivo:** confirmar el cálculo correcto de vecinos (izquierda/derecha) sin interferencia de otros
  valores de `DNA`, generando un patrón fractal simple y fácil de verificar a mano.
- **Entrada:** `N=1`; `DNA = [0,1,0,0,0,0,0,0,0,0]`
- **Resultado esperado (líneas 1-10, día 50):**
```
bbbbbbbbbbbbbbbbbbb.bbbbbbbbbbbbbbbbbbbb
bbbbbbbbbbbbbbbbbb...bbbbbbbbbbbbbbbbbbb
bbbbbbbbbbbbbbbbb.bbb.bbbbbbbbbbbbbbbbbb
bbbbbbbbbbbbbbbb...b...bbbbbbbbbbbbbbbbb
bbbbbbbbbbbbbbb.bbbbbbb.bbbbbbbbbbbbbbbb
bbbbbbbbbbbbbb...bbbbb...bbbbbbbbbbbbbbb
bbbbbbbbbbbbb.bbb.bbb.bbb.bbbbbbbbbbbbbb
bbbbbbbbbbbb...b...b...b...bbbbbbbbbbbbb
bbbbbbbbbbb.bbbbbbbbbbbbbbb.bbbbbbbbbbbb
bbbbbbbbbb...bbbbbbbbbbbbb...bbbbbbbbbbb
... (día 50): bb...bbbbbbbbb...bbbbbbbbb...bbbbb...bbb
```

---

### TC05 — El frente alcanza los bordes del arreglo (valor límite estructural)
- **Técnica:** análisis de valores límite sobre los **índices físicos** del arreglo (plato 0 y plato 39).
- **Objetivo:** este es el caso más importante para detectar errores de índice fuera de rango o manejo
  incorrecto del "vecino virtual = 0" en los extremos, porque el frente de población avanza **una
  columna por día** y llega exactamente al borde izquierdo el **día 20**.
- **Entrada:** `N=1`; `DNA = [0,1,1,1,1,1,1,1,1,1]`
- **Resultado esperado:**
  - Días 1–19: el frente crece simétricamente 1 plato por día alrededor del centro.
  - **Día 20:** el frente toca el plato 1 (índice 0) por la izquierda, sin desbordarse ni fallar.
  - **Día 21 en adelante:** el tablero completo queda saturado con `.` y permanece estable hasta el día 50.
- **Por qué importa:** un `IndexError` o un cálculo erróneo de vecinos en los bordes solo se manifiesta
  cuando el frente efectivamente llega a las columnas 0 o 39; muchas implementaciones defectuosas pasan
  el TC01 (donde el frente nunca llega al borde) pero fallan aquí.

---

### TC06 — Estabilización tras un transitorio (control de exactamente 50 iteraciones)
- **Técnica:** valor límite sobre el **número de días simulados** (detecta off-by-one: 49 vs. 50 vs. 51
  iteraciones).
- **Objetivo:** usar un `DNA` cuyo patrón en el día 49 sea **distinto** al del día 50 (no llega a un
  punto fijo), de modo que una implementación que simule un día de más o de menos produzca una salida
  visiblemente distinta a la esperada.
- **Entrada:** `N=1`; `DNA = [0,1,2,0,0,0,0,0,0,0]`
- **Resultado esperado (extracto, verificado con el simulador de referencia):**
```
Día 48: bxxxxxxbxxxbbbbbbbbbbbbbbbbxxxbxxxbxxxbb
Día 49: xbbbbbbbbbbxbbbbbbbbbbbbbbxbbbbbbbbbbbxb
Día 50: xxbbbbbbbbxxxbbbbbbbbbbbbxxxbbbbbbbbbxxx
```
  (día 49 ≠ día 50: si la salida del estudiante coincide con "día 49" o "día 51" en vez de "día 50",
  hay un error de conteo de iteraciones).

---

### TC07 — Múltiples casos de prueba con líneas en blanco (formato de entrada/salida)
- **Técnica:** prueba estructural sobre el formato de E/S descrito en el enunciado (línea en blanco
  entre casos de entrada, línea en blanco entre casos de salida).
- **Objetivo:** verificar el parseo correcto cuando hay más de un caso, con las líneas en blanco de
  separación que exige el enunciado, y que la salida separe los bloques de 50 líneas con exactamente
  una línea en blanco (sin línea en blanco sobrante al final del archivo).
- **Entrada:**
```
3

0 0 0 0 0 0 0 0 0 0

3 3 3 3 3 3 3 3 3 3

0 1 2 0 1 3 3 2 3 0
```
- **Resultado esperado:** tres bloques de 50 líneas (equivalentes a TC02, TC03 y TC01 respectivamente),
  separados entre sí por una única línea en blanco, sin línea en blanco extra al final.

---

### TC08 — Patrón "tablero de ajedrez" en la tabla DNA (cobertura de valores impares/pares de K)
- **Técnica:** partición de equivalencia sobre la tabla `DNA`, alternando extremos (`3,0,3,0,...`) para
  forzar que se ejerciten tanto los índices pares como impares de `K` con valores no triviales.
- **Entrada:** `N=1`; `DNA = [3,0,3,0,3,0,3,0,3,0]`
- **Resultado esperado (líneas 1-10, día 50):**
```
bbbbbbbbbbbbbbbbbbb.bbbbbbbbbbbbbbbbbbbb
WWWWWWWWWWWWWWWWWWbbbWWWWWWWWWWWWWWWWWWW
WbbbbbbbbbbbbbbbbWbWbWbbbbbbbbbbbbbbbbbW
bbWWWWWWWWWWWWWWbbWbWbbWWWWWWWWWWWWWWWbb
WbWbbbbbbbbbbbbWbbbWbbbWbbbbbbbbbbbbbWbW
bWbbWWWWWWWWWWbbbWbbbWbbbWWWWWWWWWWWbbWb
bbbbWbbbbbbbbWbWbbbWbbbWbWbbbbbbbbbWbbbb
WWWbbbWWWWWWbbWbbWbbbWbbWbbWWWWWWWbbbWWW
WbWbWbWbbbbWbbbbbbbWbbbbbbbWbbbbbWbWbWbW
bWbWbWbbWWbbbWWWWWbbbWWWWWbbbWWWbbWbWbWb
... (día 50): WWWWWWbbbWbbWbbWWWbbbWWWWWbbWbbbbbWWWWWW
```
- **Objetivo:** patrón caótico que exige exactitud total en el orden de lectura izquierda→centro→derecha
  y en la actualización simultánea (todos los platos deben calcularse con los valores del día *anterior*,
  no con valores ya actualizados del mismo día — error clásico de simulación "in-place").

---

### TC09 — Validación estricta del formato de salida
- **Técnica:** prueba estructural / de conformidad de formato.
- **Objetivo:** verificar automáticamente (por ejemplo con un script de comparación) que:
  1. cada línea impresa tiene **exactamente 40 caracteres**;
  2. cada caso produce **exactamente 50 líneas**;
  3. solo se usan los 4 caracteres válidos: `' '`, `.`, `x`, `W`;
  4. hay **exactamente una** línea en blanco entre las salidas de casos consecutivos, y ninguna al
     final del archivo ni al principio.
- **Insumo:** se puede reutilizar la salida de cualquiera de los casos anteriores (p. ej. TC01) como
  entrada a este chequeo automático.

---

### TC10 — Prueba de carga / robustez
- **Técnica:** prueba no funcional (rendimiento) — valor límite superior de `N`.
- **Objetivo:** verificar que el programa procesa correctamente un número grande de casos (por ejemplo
  `N=1000`, todos con el mismo `DNA` de TC01) dentro de un tiempo razonable, sin degradación de
  memoria ni errores acumulativos de parseo entre casos.
- **Entrada:** `N=1000` repeticiones del caso TC01, separadas por líneas en blanco según el formato.
- **Resultado esperado:** 1000 bloques idénticos de 50 líneas (cada uno igual al de TC01), separados
  correctamente, ejecutados en tiempo aceptable.

## 4. Matriz de trazabilidad

| Caso | Técnica principal                        | Riesgo que mitiga                                             |
|------|-------------------------------------------|-----------------------------------------------------------------|
| TC01 | Caso representativo / equivalencia        | Corrección funcional básica frente al oráculo oficial           |
| TC02 | Valor límite (DNA[1]=0)                   | Manejo de extinción y estabilidad del punto fijo "todo cero"    |
| TC03 | Valor límite (DNA[0]=3)                   | Saturación total, uso de DNA[9] en platos internos              |
| TC04 | Equivalencia (aislar un valor de DNA)     | Cálculo correcto de vecinos sin ruido de otros valores          |
| TC05 | Valor límite estructural (bordes 0 y 39)  | Errores de índice / vecino virtual mal implementado             |
| TC06 | Valor límite (día 49 vs. 50)              | Errores off-by-one en el número de iteraciones                  |
| TC07 | Estructural (formato de E/S multi-caso)   | Parseo de líneas en blanco / separación de casos                |
| TC08 | Equivalencia (patrón alternante)          | Actualización simultánea correcta (no in-place)                 |
| TC09 | Estructural (formato de salida)           | Longitud de línea, número de líneas, caracteres válidos         |
| TC10 | No funcional (carga)                      | Rendimiento y estabilidad con muchos casos                      |

## 5. Simulador de referencia

El siguiente script en Python fue usado para generar y verificar todas las salidas esperadas de esta tabla. Reproduce exactamente las 10 líneas de muestra del enunciado y puede usarse como **oráculo automático** para comparar contra la salida de cualquier implementación bajo prueba.

```python
def simulate(dna, days=50, dishes=40, start=19):
    density = [0] * dishes
    density[start] = 1
    chars = {0: ' ', 1: '.', 2: 'x', 3: 'W'}
    lines = [''.join(chars[d] for d in density)]  # día 1 impreso = estado inicial
    for _ in range(days - 1):
        newd = [0] * dishes
        for i in range(dishes):
            left = density[i - 1] if i > 0 else 0
            right = density[i + 1] if i < dishes - 1 else 0
            k = left + density[i] + right
            newd[i] = dna[k]
        density = newd
        lines.append(''.join(chars[d] for d in density))
    return lines
```
