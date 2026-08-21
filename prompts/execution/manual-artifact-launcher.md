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

Si el artefacto declara Output Delivery autorizado, materializa únicamente la salida declarada en el directorio indicado. No uses ese permiso para modificar otros archivos o recursos.

En la conversación responde únicamente con un Caveman Return:
- estado o resultado esencial;
- atención requerida concreta o `Ninguna`;
- nombre/path del artefacto completo generado.

No reproduzcas en la conversación el contenido completo del artefacto de salida salvo que el artefacto lo exija explícitamente.
```

## Ejemplo — Planning Task con Exchange manual

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

En la conversación responde sólo con un Caveman Return: resultado esencial, atención requerida y archivo generado.
```

## Ejemplo — Execution Task con Exchange manual

```text
Ejecuta el artefacto IA-DOS indicado.

Tipo esperado: Execution Task

Archivo autoritativo:
C:\Users\usuario\Proyectos\Proyecto\proyecto-exch\inbox\PROYECTO-10-APP-20260821-130700-TASK.md

Directorio físico de salida:
C:\Users\usuario\Proyectos\Proyecto\proyecto-exch\outbox\

Lee completamente el archivo autoritativo antes de actuar.

El archivo define toda la autoridad. Este launcher no la amplía.

Materializa únicamente el Execution Report autorizado en el outbox y responde en la conversación sólo con un Caveman Return.
```
