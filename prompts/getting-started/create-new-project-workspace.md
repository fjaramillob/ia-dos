# Prompt para crear un proyecto nuevo dentro del workspace

Este prompt está dirigido a un coding agent con acceso al sistema de archivos y Git.

```text
Artifact Type: Execution Task
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
Forbidden Output: elegir stack | generar funcionalidades | crear recursos no autorizados | ampliar topología
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [TASK-ID]

Objetivo
Crear únicamente la estructura local autorizada para un proyecto nuevo, sin elegir stack, generar funcionalidades ni inventar arquitectura.

Información entregada
- ruta del workspace, cuando aplique;
- nombre del proyecto;
- project-slug, cuando aplique;
- resumen confirmado del propósito;
- recursos que deben crearse: implementación, memoria u otros;
- modelo de adopción elegido;
- autorización explícita para crear carpetas y, cuando corresponda, inicializar Git.

Antes de actuar
1. Detecta el sistema operativo.
2. Resuelve y muestra las rutas absolutas afectadas.
3. Verifica que las rutas padre existan.
4. Si se usa project-slug, verifica `^[a-z0-9]+(?:-[a-z0-9]+)*$`.
5. Verifica que no existan carpetas o repositorios en conflicto.
6. Confirma exactamente qué recursos están autorizados.
7. No crees una Wiki sólo porque aparezca en un ejemplo de IA-DOS.

Topología
Usa exclusivamente la topología aprobada en la tarea.

Ejemplo posible, no obligatorio:
proyectos/
├── 00-ia-dos/
└── <project-slug>/
    ├── <project-slug>-app/
    └── <project-slug>-wiki/

Acciones permitidas
- crear las carpetas explícitamente autorizadas;
- crear un README.md mínimo en una implementación nueva cuando corresponda;
- copiar `templates/wiki-starter/` sólo cuando la tarea autorice crear memoria Markdown;
- crear `.ia-dos.yaml` desde `templates/adoption.template.yaml` cuando esté incluido;
- inicializar Git únicamente en los recursos y condiciones autorizados;
- ejecutar verificaciones de solo lectura;
- reportar rutas y estado.

Contenido mínimo de la implementación nueva
- nombre del proyecto;
- propósito confirmado;
- estado real, por ejemplo implementación no iniciada;
- referencia a memoria durable cuando ya exista;
- no asumir stack o arquitectura.

Memoria durable
Cuando esté autorizada una Wiki nueva:
- usa directamente el starter vigente;
- no crees `index.md` provisional;
- no crees `tasks/`, `context-packs/`, `log.md` ni arquitectura vacía;
- conserva `00-home.md`, `project-brief.md`, `status/current-state.md`, `AGENTS.md`, `decisions/` y `sources/` según el starter;
- completa sólo información confirmada.

Acciones prohibidas
- elegir framework, base de datos o proveedor cloud;
- generar código, dependencias o configuración funcional;
- crear `.env`;
- crear pipelines o despliegues;
- crear Exchange salvo autorización explícita;
- crear repositorios remotos o definir visibilidad sin autorización;
- crear commits, push o pull requests no autorizados;
- convertir la carpeta exterior en repositorio Git por defecto;
- sobrescribir carpetas o archivos existentes;
- inventar contenido para completar la memoria.

Condiciones de detención
Detente antes de escribir cuando:
- la ruta sea ambigua;
- exista una carpeta o repositorio en conflicto;
- falte autorización;
- la topología física no esté decidida y el cambio sea difícil de revertir;
- la solicitud implique tomar decisiones técnicas aún no confirmadas.

Validaciones obligatorias
- rutas absolutas correctas;
- sólo existen los recursos autorizados;
- ausencia de secretos;
- ausencia de código o dependencias no solicitadas;
- si se creó memoria, el starter vigente fue aplicado sin estructura legada;
- Git y operaciones remotas coinciden con las autorizaciones;
- diff o listado final revisable.

Reporte final
Devuelve un Execution Report con:
- sistema operativo y workspace utilizado;
- recursos y archivos creados;
- repositorios Git inicializados, si aplica;
- comandos ejecutados;
- validaciones;
- acciones omitidas por fuera de alcance;
- riesgos o decisiones pendientes;
- siguiente decisión requerida del Cycle Owner.

No continúes con desarrollo de producto sin otra Execution Task.
```
