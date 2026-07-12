# Aplicar las plantillas mínimas de adopción

Este paso convierte una estructura de carpetas en un proyecto que declara formalmente cómo adopta IA-DOS.

Las plantillas no deben copiarse sin revisión. Deben adaptarse al proyecto y completarse solo con información confirmada.

## Plantillas disponibles

```text
templates/
├── adoption.template.yaml
├── AGENTS.template.md
└── wiki-starter/
    ├── index.md
    ├── project-brief.md
    ├── current-state.md
    ├── architecture.md
    ├── log.md
    ├── AGENTS.md
    ├── context-packs/core.md
    ├── decisions/README.md
    ├── tasks/README.md
    └── sources/README.md
```

## Destino recomendado

```text
nombre-proyecto/
├── nombre-proyecto-app/
│   └── AGENTS.md
└── nombre-proyecto-wiki/
    ├── .ia-dos.yaml
    ├── index.md
    ├── project-brief.md
    ├── current-state.md
    ├── architecture.md
    ├── log.md
    ├── AGENTS.md
    ├── context-packs/core.md
    ├── decisions/README.md
    ├── tasks/README.md
    └── sources/README.md
```

## Paso 1 — Crear el manifiesto de adopción

Copia:

```text
templates/adoption.template.yaml
```

como:

```text
nombre-proyecto-wiki/.ia-dos.yaml
```

Completa:

- nombre y `project-slug`;
- rutas reales de app y wiki;
- modelo de adopción;
- Project Orchestrator utilizado;
- fuente canónica de tareas;
- fuente canónica de decisiones;
- excepciones;
- rutas de contexto.

No declares `main`, `latest` o `current` como versión adoptada.

## Paso 2 — Incorporar `AGENTS.md` en la app

Copia:

```text
templates/AGENTS.template.md
```

como:

```text
nombre-proyecto-app/AGENTS.md
```

Adapta:

- propósito del repositorio;
- ruta o URL de la wiki;
- ubicación de `.ia-dos.yaml`;
- fuente canónica de tareas;
- comandos y verificaciones reales del proyecto;
- zonas permitidas y prohibidas;
- condiciones de detención específicas.

No agregues comandos que todavía no existan en el repositorio.

## Paso 3 — Crear la wiki mínima

Copia el contenido de:

```text
templates/wiki-starter/
```

hacia la raíz del repositorio wiki.

Completa primero:

1. `index.md`;
2. `project-brief.md`;
3. `current-state.md`;
4. `context-packs/core.md`;
5. `.ia-dos.yaml`.

`architecture.md` puede permanecer como `Por definir` o `Desconocida` cuando todavía no existe evidencia suficiente.

## Paso 4 — Separar hechos de propuestas

Durante el bootstrap utiliza estados explícitos:

```text
Implementado
Parcialmente implementado
Planificado
Deprecado
Desconocido
```

En un proyecto nuevo, `current-state.md` debe declarar que la implementación todavía no comenzó cuando corresponda.

En un proyecto existente, la información debe derivarse de evidencia, documentación o inspección del repositorio.

## Paso 5 — Verificar rutas y fuentes canónicas

Confirma:

- la app puede localizar la wiki;
- la wiki puede localizar la app;
- `.ia-dos.yaml` utiliza rutas válidas;
- existe una sola fuente canónica para tareas;
- existe una sola fuente canónica para decisiones;
- `CORE` enlaza documentos, no los duplica;
- los agentes no reciben acceso automático a todo el workspace.

## Qué no hacen estas plantillas

Las plantillas no:

- eligen stack;
- crean arquitectura;
- generan código;
- crean repositorios remotos;
- sustituyen la revisión humana;
- convierten información desconocida en hechos;
- configuran automáticamente ChatGPT, Gemini o coding agents.

## Verificación final

- [ ] `.ia-dos.yaml` declara una versión concreta.
- [ ] App y wiki tienen rutas correctas.
- [ ] La app contiene `AGENTS.md` adaptado.
- [ ] La wiki tiene un punto de entrada claro.
- [ ] `current-state.md` refleja realidad comprobada.
- [ ] `CORE` es breve.
- [ ] Las decisiones tienen una carpeta canónica.
- [ ] Las tareas tienen una fuente canónica.
- [ ] No existen secretos.
- [ ] No quedan placeholders interpretables como hechos.

## Siguiente paso

Después de aplicar y revisar las plantillas, el proyecto está preparado para crear su primera `Execution Task` y validar el handoff hacia un coding agent.
