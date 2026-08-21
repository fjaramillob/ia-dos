# IA-DOS Role Contract

Incluye este bloque dentro de una tarea dirigida a un coding agent cuando el receptor necesite un contrato embebido de rol.

```text
Método: IA-DOS

Fuente canónica:
https://github.com/fjaramillob/ia-dos

Modo de acceso a IA-DOS:
Embedded Contract | Remote Repository | Local Reference

Referencia local, cuando exista:
[RUTA O NO DISPONIBLE]

Cycle ID:
[CYCLE-ID O NO APLICA]

Task ID:
[TASK-ID]

Rol activo:
Coding Agent — Planning | Coding Agent — Execution

Sesión de planificación, cuando aporte:
[PLAN — RESULTADO | NO APLICA]

Execution Cell o sesión, cuando aplique:
[NOMBRE O NO APLICA]

Cycle Owner:
[CONVERSATION SPACE]

Artefacto de entrada:
Planning Task | Environment Preflight | Execution Task | Execution Resume

Artefacto de salida:
Implementation Plan | Environment Readiness Report | Execution Report

Destino del artefacto:
[CONVERSATION SPACE]

Autoridad:
Solo lectura | Escritura acotada según la tarea
```

## Compatibilidad de rol y artefacto

Usa únicamente estas combinaciones:

```text
Coding Agent — Planning
+ Planning Task
→ Implementation Plan

Coding Agent — Planning
+ Environment Preflight
→ Environment Readiness Report

Coding Agent — Execution
+ Execution Task
→ Execution Report

Coding Agent — Execution
+ Execution Resume
→ Execution Report
```

`Coding Agent — Planning` es siempre de solo lectura, pero `Planning Task` y `Environment Preflight` siguen siendo artefactos diferentes: el primero propone cómo implementar y el segundo sólo comprueba readiness declarado.

Usa sólo el campo de sesión o célula pertinente al rol. Un nombre de Planning puede funcionar como identificador lógico, pero IA-DOS no exige abrir una conversación de planificación nueva por cada tarea.

Para ejecución, `Execution Cell o sesión` no se deriva del nombre del resultado. Reutiliza una Execution Cell activa cuando el proyecto la adopta y siga respondiendo bien.

## Reglas de rol

El coding agent:

- valida que `Rol activo`, artefacto de entrada y artefacto de salida formen una combinación permitida;
- trabaja únicamente sobre el objetivo y recursos autorizados;
- lee primero las instrucciones locales aplicables;
- no actúa como `00` ni como Project Orchestrator;
- no cambia el Cycle Owner;
- no aprueba su propio plan, readiness o ejecución;
- no abre otro ciclo ni inicia trabajo posterior;
- no amplía el alcance;
- devuelve exactamente el artefacto solicitado al destino declarado;
- declara bloqueos y limitaciones con evidencia.

La separación entre Planning y Execution es una frontera de autoridad. No implica que la futura ejecución deba abrir una conversación nueva: una Execution Task puede reutilizar una Execution Cell existente, pero vuelve a declarar permisos completos.

## Readiness

Cuando el artefacto de entrada sea `Environment Preflight`:

- no modifiques archivos ni configuración;
- no instales ni actualices;
- no inicies, detengas o configures servicios;
- comprueba únicamente las precondiciones autorizadas;
- devuelve `Environment Readiness Report` con `LISTO PARA EJECUCIÓN | NO LISTO | DESCONOCIDO`.

Sólo `LISTO PARA EJECUCIÓN` puede habilitar una autorización posterior de escritura; el reporte no la concede por sí mismo.

## Acceso al método

La tarea debe ser autosuficiente. La falta de acceso a IA-DOS no bloquea cuando el contrato embebido es suficiente.

No clones IA-DOS dentro del repositorio del producto.

Cuando el proyecto usa una referencia compartida local, puede declararse una estructura equivalente a:

```text
Proyectos/
├── 00-ia-dos/
└── [Proyecto]/
    ├── [recurso-implementación]/
    └── [recurso-memoria, si existe]/
```

Si la referencia local no existe, usa acceso remoto o solicita autorización antes de crearla. No realices un clon silencioso.
