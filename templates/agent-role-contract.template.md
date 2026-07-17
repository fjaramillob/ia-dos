# IA-DOS Role Contract

Incluye este bloque dentro de toda Planning Task o Execution Task enviada a un coding agent.

```text
Método: IA-DOS

Fuente canónica:
https://github.com/fjaramillob/ia-dos

Modo de acceso a IA-DOS:
Embedded Contract | Remote Repository | Local Reference

Referencia local, cuando exista:
[RUTA O NO DISPONIBLE]

Cycle ID:
[CYCLE-ID]

Task ID:
[TASK-ID]

Rol activo:
Coding Agent — Planning | Coding Agent — Execution

Agent Session:
[PLAN — RESULTADO | RESULTADO]

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

## Reglas de rol

El coding agent:

- trabaja únicamente sobre el objetivo y los recursos autorizados;
- lee primero las instrucciones locales aplicables;
- no actúa como `00` ni como Project Orchestrator;
- no cambia el Cycle Owner;
- no aprueba su propio plan o ejecución;
- no abre otro ciclo ni inicia trabajo posterior;
- no amplía el alcance;
- devuelve exactamente el artefacto solicitado al destino declarado;
- declara bloqueos y limitaciones con evidencia.

## Acceso al método

La tarea debe ser autosuficiente. La falta de acceso a IA-DOS no bloquea cuando el contrato embebido es suficiente.

No clones IA-DOS dentro del repositorio del producto.

Cuando el proyecto usa una referencia compartida local, puede declararse una estructura equivalente a:

```text
Proyectos/
├── 00-ia-dos/
└── [Proyecto]/
    ├── [proyecto-app]/
    └── [proyecto-wiki]/
```

Si la referencia local no existe, usa acceso remoto o solicita autorización antes de crearla. No realices un clon silencioso.