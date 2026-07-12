# Prompt para crear un proyecto nuevo dentro del workspace

Este prompt está dirigido a Codex, Claude Code, Antigravity u otro agente con acceso al sistema de archivos y Git.

```text
Objetivo
Crear la estructura inicial de un proyecto nuevo dentro del workspace IA-DOS, sin elegir stack, generar funcionalidades ni inventar arquitectura.

Información entregada por el usuario
- ruta del workspace;
- nombre del proyecto;
- project-slug;
- resumen confirmado del propósito;
- decisión sobre si app y wiki serán repositorios Git independientes;
- autorización explícita para crear carpetas y, cuando corresponda, inicializar Git.

Estructura recomendada
proyectos/
├── 00-ia-dos/
└── <project-slug>/
    ├── <project-slug>-app/
    └── <project-slug>-wiki/

Antes de actuar
1. Detecta el sistema operativo.
2. Resuelve y muestra todas las rutas absolutas.
3. Verifica que el workspace exista.
4. Verifica que el project-slug cumpla `^[a-z0-9]+(?:-[a-z0-9]+)*$`.
5. Verifica que no exista ya la carpeta exterior ni carpetas en conflicto.
6. Confirma el alcance autorizado.

Acciones permitidas
- crear la carpeta exterior del proyecto;
- crear las carpetas app y wiki;
- crear un README.md mínimo en la app;
- crear un index.md mínimo en la wiki;
- inicializar Git por separado en app y wiki solo cuando esté autorizado;
- ejecutar verificaciones de solo lectura;
- reportar rutas y estado.

Contenido mínimo de la app
- nombre del proyecto;
- propósito resumido confirmado;
- estado: implementación no iniciada;
- ruta hacia la wiki;
- advertencia de que stack y arquitectura aún no están definidos.

Contenido mínimo de la wiki
- nombre del proyecto;
- estado: wiki pendiente de bootstrap;
- fuente inicial: conversación `00 — Dirección y definición`;
- ruta hacia la app;
- siguiente paso: crear la LLM Wiki.

Acciones prohibidas
- elegir framework, base de datos o proveedor cloud;
- generar código, dependencias o configuración;
- crear `.env`;
- crear pipelines o despliegues;
- crear repositorios remotos públicos;
- crear commits sin autorización;
- convertir la carpeta exterior en repositorio Git;
- sobrescribir carpetas o archivos existentes;
- inventar contenido para completar la wiki.

Condiciones de detención
Detente antes de escribir cuando:
- la ruta sea ambigua;
- el project-slug sea inválido;
- exista una carpeta en conflicto;
- falte autorización;
- no esté clara la visibilidad de los futuros repositorios;
- la solicitud implique tomar decisiones técnicas aún no confirmadas.

Validaciones obligatorias
- rutas absolutas correctas;
- carpeta exterior creada una sola vez;
- app y wiki presentes;
- carpeta exterior sin `.git` salvo excepción documentada;
- ausencia de secretos;
- ausencia de código o dependencias no solicitadas;
- contenido mínimo revisable;
- siguiente paso claramente indicado.

Reporte final
Entrega:
1. sistema operativo;
2. workspace utilizado;
3. project-slug;
4. carpetas y archivos creados;
5. repositorios Git inicializados, si aplica;
6. comandos ejecutados;
7. validaciones;
8. advertencias o decisiones pendientes;
9. siguiente paso recomendado.

No continúes con desarrollo de producto sin una instrucción separada.
```
