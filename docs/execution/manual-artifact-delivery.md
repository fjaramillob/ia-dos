# Entrega manual de artefactos

Este documento define una convención opcional para operar IA-DOS cuando un proyecto usa Exchange de forma manual y el Code Agent necesita una instrucción breve para localizar el artefacto de entrada y materializar su salida.

No crea nuevos `Artifact Type`, no modifica Exchange y no agrega autoridad.

## Problema que resuelve

En un flujo manual puede existir un artefacto correcto en `inbox/`, pero el Code Agent todavía necesita saber qué archivo debe consumir.

```text
Conversation Agent
→ construye artefacto autoritativo
→ Exchange / inbox
→ ¿qué archivo debe leer el Code Agent?
```

La solución es un **Manual Artifact Launcher** efímero.

## Manual Artifact Launcher

```text
Manual Artifact Launcher
= prompt efímero y no autoritativo
  que localiza un artefacto ya construido
  y, cuando corresponde, su directorio físico de salida.
```

No es un artefacto IA-DOS.

```text
Launcher ≠ Task
Launcher ≠ Handoff
Launcher ≠ Exchange
Launcher ≠ autorización
Launcher ≠ memoria durable
```

El launcher puede declarar únicamente:

- tipo esperado del artefacto;
- ruta física del archivo autoritativo;
- directorio físico de salida cuando exista;
- instrucción de leer el archivo completo;
- recordatorio de que el artefacto, no el launcher, define objetivo, alcance, autoridad, restricciones, salida y condiciones de detención;
- repetición del modo de retorno **ya declarado por la Task**, cuando ayude a evitar ambigüedad.

El launcher no puede elegir, cambiar ni ampliar el modo de retorno. Tampoco puede ampliar permisos ni corregir silenciosamente el contenido del artefacto.

## Separar contrato y ubicación física

Preferencia:

```text
Planning Task / Execution Task
→ define contrato y entrega autorizada

Manual Artifact Launcher
→ resuelve ubicación física local

Exchange
→ sólo almacena archivos
```

Evita incrustar una ruta absoluta de una máquina dentro del artefacto cuando esa ruta sólo corresponde al transporte local.

Esto permite mover el mismo artefacto entre máquinas o mecanismos de sincronización sin alterar su contrato.

## Output Delivery

Cuando la tarea autoriza materializar el artefacto de salida como archivo, debe declararlo explícitamente.

Ejemplo semántico:

```text
Output Delivery:
Channel: Exchange
Location: outbox
Filename: [NOMBRE.md]
Caveman Return: Sí | No
```

`Location: outbox` describe el destino lógico elegido por el proyecto. El launcher puede resolverlo a una ruta física concreta.

### Planning sigue siendo solo lectura

Una `Planning Task` continúa siendo de solo lectura respecto de las fuentes y del producto aunque autorice crear su `Implementation Plan` como archivo de salida.

```text
Planning read-only
= no modifica código, schema, datos, Git, Wiki,
  configuración ni recursos inspeccionados

Output materialization
= puede escribir únicamente el artefacto
  de salida declarado y en el destino autorizado
```

Materializar el propio output no concede permiso para modificar ningún otro recurso.

La misma distinción puede aplicarse a `Environment Preflight` y otros retornos de solo lectura.

## Caveman Return

La conversación del Code Agent puede utilizar un **Caveman Return** únicamente cuando se cumplen conjuntamente estas condiciones:

1. la Task autoritativa declara `Caveman Return: Sí`;
2. el output completo fue materializado correctamente en el destino declarado.

```text
Caveman Return
= representación conversacional mínima
  del artefacto de salida ya materializado
```

No es un nuevo Artifact Type y no reemplaza al `.md` completo.

```text
Caveman Return ≠ Implementation Plan
Caveman Return ≠ Environment Readiness Report
Caveman Return ≠ Execution Report
Caveman Return ≠ memoria durable
Caveman Return ≠ autorización
```

Debe ser breve y contener sólo:

1. estado o resultado esencial;
2. atención requerida concreta o `Ninguna`;
3. nombre o ubicación del artefacto completo.

Si la Task declara `Caveman Return: No`, usa `Channel: Conversation` o no declara `Output Delivery`, no compactes la salida por esta convención: devuelve el artefacto completo según el contrato y canal autoritativos.

Ejemplo de Planning:

```text
PLAN LISTO

Resultado: `closed_at` puede soportar el archivado propuesto.
Atención: falta definir autoridad para las acciones destructivas.
Archivo: PROYECTO-...-IMPLEMENTATION-PLAN.md
```

Ejemplo de Execution:

```text
EJECUCIÓN COMPLETADA

Atención: Ninguna.
Reporte: PROYECTO-...-REPORT.md
```

Ejemplo bloqueado:

```text
BLOQUEADO

Atención: falta la condición concreta indicada en el reporte.
Reporte: PROYECTO-...-REPORT.md
```

No copies en el Caveman Return el detalle que ya existe en el artefacto completo.

## Identidad y filenames

La identidad no pertenece a Exchange ni al launcher.

Para una `Execution Task` real, el Conversation Agent asigna el `Task ID` antes de materializarla.

Cuando el proyecto no tiene otro esquema, IA-DOS recomienda:

```text
{PROJECT}-{ORIGIN}-{CELL}-{YYYYMMDD}-{HHMMSS}
```

Ejemplo:

```text
PROYECTO-10-APP-20260821-130700
```

Una candidata producida por Planning mantiene:

```text
Task ID: PENDIENTE — ASIGNAR AL ADOPTAR
```

El timestamp se asigna cuando el Conversation Agent adopta la candidata y construye la Execution Task real.

Para materialización de archivos pueden usarse nombres derivados del artefacto, por ejemplo:

```text
{TASK-ID}-TASK.md
{TASK-ID}-REPORT.md
```

Los IDs de Planning conservan su contrato propio; el esquema temporal anterior no se convierte por esta convención en una obligación universal para `Planning Task ID`.

## Flujo manual recomendado

```text
Conversation Agent
→ construye TASK.md
→ Exchange / inbox

Persona
→ pega Manual Artifact Launcher

Code Agent
→ lee TASK.md completo
→ trabaja dentro de autoridad
→ materializa output completo cuando la Task lo autoriza
→ usa Caveman Return sólo si la Task declara Sí y el output completo existe

Conversation Agent / Cycle Owner
→ consume el output completo
→ revisa y decide dentro de su autoridad
```

Nada ocurre automáticamente por existir un archivo en `inbox/` o `outbox/`.

## Regla final

```text
Artifact = contrato y evidencia completos
Launcher = localización manual
Exchange = almacenamiento pasivo
Output Delivery = permiso acotado de materialización
Caveman Return = presentación conversacional mínima sólo por opt-in de la Task
```

Ninguna de estas convenciones cambia la autoridad definida por el artefacto.