# Preparar el workspace local

El workspace local se prepara cuando una tarea definida en conversación necesita acceso real a repositorios, archivos, Git o un coding agent. No es un requisito previo para iniciar IA-DOS.

La secuencia correcta es:

```text
00 orienta
→ se define una tarea verificable
→ se confirma que requiere ejecución local
→ se prepara el workspace
→ se ejecuta y se devuelve evidencia
```

## Estructura recomendada

```text
proyectos/
├── 00-ia-dos/
├── proyecto-a/
│   ├── proyecto-a-app/
│   └── proyecto-a-wiki/
└── proyecto-b/
    ├── proyecto-b-app/
    └── proyecto-b-wiki/
```

La ubicación por defecto puede ser `$HOME\proyectos` en Windows o `~/proyectos` en macOS y Linux, pero es una convención, no una obligación.

## Principios

- IA-DOS se instala una sola vez como `00-ia-dos/`;
- cada proyecto mantiene su implementación y su memoria durable;
- app y Wiki pueden estar separadas o convivir cuando una excepción documentada lo justifique;
- la carpeta exterior del proyecto normalmente no es un repositorio Git;
- un coding agent recibe solo los repositorios y rutas necesarios para la tarea actual;
- no se mueve un proyecto existente solo para cumplir esta estructura.

## Proyecto nuevo

La estructura recomendada es:

```text
nombre-proyecto/
├── nombre-proyecto-app/
└── nombre-proyecto-wiki/
```

La creación física debe ocurrir después de contar con una definición inicial en `00 — Dirección y definición` y con autorización para crear carpetas o repositorios.

## Proyecto existente

Antes de mover o reorganizar, revisa:

- rutas absolutas y relativas;
- variables de entorno;
- scripts y pipelines;
- configuraciones del editor;
- despliegues;
- enlaces entre repositorios;
- accesos de colaboradores.

Cuando mover sea riesgoso, conserva la ubicación actual y documenta la excepción.

## Acceso de agentes

No abras toda la carpeta `proyectos/` como contexto cotidiano. Para una tarea normal, entrega únicamente:

- el repositorio de producto correspondiente;
- las rutas específicas de la Wiki necesarias;
- la `Execution Task`;
- instrucciones técnicas aplicables.

El repositorio `00-ia-dos/` se consulta para guías, plantillas, prompts o cambios de versión, no como contexto completo de cada ejecución.

## Seguridad

No guardes en IA-DOS ni en la Wiki:

- contraseñas;
- API keys;
- tokens;
- claves privadas;
- credenciales cloud;
- archivos `.env` con valores reales;
- datos personales sensibles.

## Verificación

Antes de ejecutar una tarea, confirma:

- [ ] la ruta del workspace es estable;
- [ ] IA-DOS tiene una sola ubicación;
- [ ] el proyecto y sus repositorios están identificados;
- [ ] app y Wiki están separadas o la excepción está documentada;
- [ ] no se entregará acceso a proyectos no relacionados;
- [ ] no existen secretos dentro del contexto compartido;
- [ ] la tarea que justificó preparar el workspace sigue vigente.

## Siguiente paso

Continúa con [Instalar IA-DOS en el workspace](install-ia-dos.md) solo cuando la tarea requiera acceso local al framework, sus plantillas o sus guías.
