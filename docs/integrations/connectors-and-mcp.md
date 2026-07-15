# Conectores y MCP

IA-DOS puede trabajar con conectores, servidores MCP, herramientas nativas de una plataforma, archivos adjuntos o acceso local. Estas capacidades amplían el alcance operativo, pero no cambian la distribución de responsabilidades definida por el método.

## Principio

```text
El Project Orchestrator decide qué información o acción necesita.
La plataforma expone capacidades concretas.
La persona responsable autoriza accesos y cambios sensibles.
La herramienta ejecuta dentro del alcance permitido.
La evidencia confirma lo realizado.
```

Un conector o servidor MCP no es un agente autónomo ni una fuente de autoridad. Es un mecanismo de acceso o ejecución.

## Tipos de acceso

Una integración puede ofrecer una o varias capacidades:

- buscar o listar recursos;
- leer contenido;
- crear contenido;
- actualizar contenido;
- eliminar contenido;
- ejecutar comandos o procesos;
- consultar estado, logs o métricas;
- descargar o subir archivos;
- administrar permisos o configuración.

No se debe inferir una capacidad de escritura porque exista lectura, ni inferir eliminación porque exista actualización.

## Verificación antes de usar

Antes de delegar una tarea, el Project Orchestrator o coding agent debe confirmar:

1. qué herramienta está disponible en la sesión actual;
2. qué operaciones expone realmente;
3. qué cuenta, repositorio, proyecto o workspace está conectado;
4. si el acceso es de lectura o escritura;
5. qué alcance fue autorizado;
6. qué acciones requieren confirmación adicional;
7. qué evidencia puede devolver la herramienta;
8. cómo detenerse o degradar el flujo si la capacidad falta.

No afirmes acceso basándote en experiencias anteriores, documentación genérica o capacidades de otra plataforma.

## MCP

MCP estandariza la exposición de herramientas y recursos a modelos y aplicaciones compatibles. En IA-DOS se trata como una capa de integración, no como una obligación arquitectónica.

Un servidor MCP puede conectar repositorios, documentación, bases de datos, sistemas de tickets, almacenamiento o servicios internos. Su presencia no reemplaza:

- autenticación;
- autorización;
- límites de alcance;
- revisión humana;
- trazabilidad;
- validación del resultado.

IA-DOS debe seguir funcionando sin MCP mediante archivos, prompts, Git, CLI, APIs o conectores nativos.

## Lectura y escritura

Separa siempre:

```text
capacidad disponible
≠ permiso concedido
≠ acción autorizada
≠ acción ejecutada
≠ acción verificada
```

Una tarea que solo requiere comprensión debe preferir lectura. La escritura se habilita cuando existe un cambio autorizado y delimitado.

Las acciones destructivas, cambios de producción, permisos, costes, datos sensibles o eliminación requieren autorización explícita y controles proporcionales al riesgo.

## Contexto mínimo

No entregues automáticamente todos los conectores, repositorios o recursos disponibles a cada conversación o agente.

Selecciona únicamente:

- la fuente necesaria;
- la operación necesaria;
- el alcance mínimo;
- el periodo de acceso necesario;
- la evidencia requerida.

La conexión técnica no convierte una fuente en contexto relevante.

## Degradación segura

Cuando una capacidad requerida no está disponible:

1. no simules que la acción fue realizada;
2. separa lo que puede resolverse conceptualmente de lo que requiere acceso;
3. prepara un handoff o instrucción ejecutable para una herramienta adecuada;
4. solicita el artefacto mínimo cuando una carga manual sea suficiente;
5. detente cuando continuar implique inventar evidencia o asumir permisos.

Ejemplo:

```text
El Project Orchestrator puede preparar una Wiki Update Task sin acceso de escritura.
Codex, Antigravity o Claude Code puede materializarla cuando recibe acceso real al repositorio.
```

## Credenciales y secretos

- no copies tokens, API keys o contraseñas en prompts, wiki, issues o pull requests;
- utiliza los mecanismos seguros de la plataforma para autenticar conectores;
- no pidas credenciales cuando la herramienta puede solicitar autorización directamente;
- limita scopes y permisos;
- revoca accesos que ya no sean necesarios;
- no registres secretos en un Capability Manifest.

## Evidencia

Una integración que modifica una fuente externa debe devolver, según corresponda:

- recurso afectado;
- operación ejecutada;
- identificador o enlace;
- archivos o campos modificados;
- resultado de validaciones;
- errores o acciones parciales;
- estado final verificable.

La respuesta verbal del modelo no reemplaza la evidencia producida por la herramienta.

## Regla principal

```text
Los conectores y MCP habilitan capacidades.
La persona responsable autoriza.
El Project Orchestrator delimita.
La herramienta ejecuta.
La evidencia demuestra.
```
