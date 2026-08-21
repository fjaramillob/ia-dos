# IA-DOS Role Contract

Incluye este bloque dentro de una Planning Task o Execution Task cuando el receptor necesite un contrato embebido de rol.

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
Planning Task | Execution Task

Artefacto de salida:
Implementation Plan | Execution Report

Destino del artefacto:
[CONVERSATION SPACE]

Autoridad:
Solo lectura | Escritura acotada según la tarea
```

Usa sólo el campo de sesión o célula pertinente al rol. Un nombre de Planning puede funcionar como identificador lógico, pero IA-DOS no exige abrir una conversación de planificación nueva por cada tarea.

Para ejecución, `Execution Cell o sesión` no se deriva del nombre del resultado. Reutiliza una Execution Cell activa cuando el proyecto la adopta y siga respondiendo bien.

## Reglas de rol

El coding agent:

- trabaja únicamente sobre el objetivo y recursos autorizados;
- lee primero las instrucciones locales aplicables;
- no actúa como `00` ni como Project Orchestrator;
- no cambia el Cycle Owner;
- no aprueba su propio plan o ejecución;
- no abre otro ciclo ni inicia trabajo posterior;
- no amplía el alcance;
- devuelve exactamente el artefacto solicitado al destino declarado;
- declara bloqueos y limitaciones con evidencia.

La separación entre Planning y Execution es una frontera de autoridad. No implica que la futura ejecución deba abrir una conversación nueva: una Execution Task puede reutilizar una Execution Cell existente, pero vuelve a declarar permisos completos.

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
