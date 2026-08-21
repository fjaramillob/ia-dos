# Manual Artifact Launcher

Usa este prompt únicamente cuando un artefacto IA-DOS ya fue construido y materializado como archivo, y la persona necesita indicarle manualmente al Code Agent qué archivo consumir.

No es un artefacto IA-DOS y no agrega autoridad.

```text
Ejecuta el artefacto IA-DOS indicado.

Tipo esperado: [ARTIFACT TYPE]

Archivo autoritativo:
[PATH COMPLETO AL ARCHIVO]

Directorio físico de salida, cuando el artefacto autorice materialización:
[PATH COMPLETO A OUTBOX | NO APLICA]

Lee completamente el archivo autoritativo antes de actuar.

El contenido del artefacto define objetivo, alcance, autoridad, restricciones, salida esperada y condiciones de detención. Este launcher sólo localiza el input y, cuando aplica, el destino físico del output; no amplía ni modifica autoridad.

Si el artefacto declara `Output Delivery` autorizado, materializa únicamente la salida declarada en el directorio indicado. No uses ese permiso para modificar otros archivos o recursos.

Usa `Caveman Return` únicamente cuando se cumplan ambas condiciones:
1. el artefacto autoritativo declara `Caveman Return: Sí`;
2. el artefacto de salida completo fue materializado correctamente en el destino declarado.

Cuando ambas se cumplen, responde en la conversación sólo con:
- estado o resultado esencial;
- atención requerida concreta o `Ninguna`;
- nombre/path del artefacto completo generado.

Si el artefacto declara `Caveman Return: No`, usa `Channel: Conversation` o no contiene una sección `Output Delivery`, no fuerces Caveman Return. Devuelve el artefacto completo según el contrato y canal declarados por el artefacto autoritativo.

Caveman Return nunca reemplaza un output completo que no haya sido materializado correctamente.
```

## Ejemplo — Planning Task con Exchange manual

Este ejemplo supone que la Planning Task declara `Output Delivery` a Exchange y `Caveman Return: Sí`.

```text
Ejecuta el artefacto IA-DOS indicado.

Tipo esperado: Planning Task

Archivo autoritativo:
C:\Users\usuario\Proyectos\Proyecto\proyecto-exch\inbox\PLAN.md

Directorio físico de salida:
C:\Users\usuario\Proyectos\Proyecto\proyecto-exch\outbox\

Lee completamente el archivo autoritativo antes de actuar.

El archivo es la única fuente autoritativa de objetivo, alcance, autoridad, restricciones, salida y condiciones de detención. Este launcher no amplía permisos.

Materializa únicamente el Implementation Plan declarado como `.md` en el outbox.

Como la Task declara `Caveman Return: Sí`, y sólo después de materializar correctamente el plan completo, responde en la conversación con resultado esencial, atención requerida y archivo generado.
```

## Ejemplo — Execution Task con Exchange manual

Este ejemplo supone que la Execution Task declara `Output Delivery` a Exchange y `Caveman Return: Sí`.

```text
Ejecuta el artefacto IA-DOS indicado.

Tipo esperado: Execution Task

Archivo autoritativo:
C:\Users\usuario\Proyectos\Proyecto\proyecto-exch\inbox\PROYECTO-10-APP-20260821-130700-TASK.md

Directorio físico de salida:
C:\Users\usuario\Proyectos\Proyecto\proyecto-exch\outbox\

Lee completamente el archivo autoritativo antes de actuar.

El archivo define toda la autoridad. Este launcher no la amplía.

Materializa únicamente el Execution Report autorizado en el outbox. Como la Task declara `Caveman Return: Sí`, responde en la conversación sólo con el retorno mínimo después de confirmar que el reporte completo existe.
```
