# Modelo operativo

IA-DOS organiza el desarrollo asistido por inteligencia artificial mediante un ciclo simple:

```text
Entender
→ documentar
→ delimitar
→ ejecutar
→ verificar
→ registrar
```

## 1. Entender

Antes de modificar un proyecto, se debe revisar su estado real.

Esto puede incluir:

- propósito del producto;
- estructura del repositorio;
- arquitectura actual;
- decisiones vigentes;
- riesgos;
- pruebas existentes;
- cambios locales pendientes.

El objetivo es reducir supuestos.

## 2. Documentar

El contexto importante debe quedar fuera de la conversación.

IA-DOS recomienda una wiki versionada que contenga, según corresponda:

- visión y alcance;
- estado actual;
- arquitectura;
- decisiones;
- riesgos;
- fuentes;
- preguntas abiertas.

La wiki describe el proyecto. No reemplaza el código ni debe contener secretos.

## 3. Delimitar

Antes de pedir una implementación, se define una unidad de trabajo acotada.

La tarea debe indicar:

- objetivo;
- problema;
- alcance;
- fuera de alcance;
- archivos o repositorios autorizados;
- criterios de aceptación;
- pruebas esperadas;
- condiciones de detención.

## 4. Ejecutar

El agente trabaja dentro de los límites declarados.

Durante esta etapa debe:

- inspeccionar antes de modificar;
- evitar cambios no solicitados;
- no introducir dependencias sin justificación;
- detenerse si falta una decisión importante;
- registrar los archivos modificados.

## 5. Verificar

El resultado se comprueba mediante evidencia aplicable al tipo de cambio.

Puede incluir:

- revisión del diff;
- lint;
- typecheck;
- build;
- pruebas unitarias o de integración;
- revisión visual;
- revisión de seguridad;
- prueba manual reproducible.

No todos los controles aplican a todas las tareas, pero toda tarea debe indicar cómo fue verificada.

## 6. Registrar

Al cerrar el trabajo se actualiza la fuente de verdad correspondiente:

- código en el repositorio de aplicación;
- decisión en la wiki;
- evidencia en el pull request o reporte;
- estado de la tarea en el issue o mecanismo elegido;
- documentación cuando cambió el comportamiento del sistema.

## Capas de información

```text
IA-DOS
    define cómo trabajar

Wiki del proyecto
    explica qué se construye, por qué y cuál es su estado

Repositorio de aplicación
    contiene la implementación

Issues o Execution Tasks
    delimitan el trabajo

Branches, commits y pull requests
    trazan los cambios

Pruebas y revisiones
    verifican el resultado
```

## Fuentes de verdad

IA-DOS busca evitar que la misma información se mantenga manualmente en varios lugares.

| Tipo de información | Destino recomendado |
|---|---|
| Propósito y estado del proyecto | Wiki |
| Arquitectura vigente | Wiki |
| Decisión durable | Registro de decisión en la wiki |
| Instrucciones para agentes | `AGENTS.md` |
| Trabajo pendiente | GitHub Issue o mecanismo elegido por el proyecto |
| Implementación | Repositorio de aplicación |
| Revisión y evidencia del cambio | Pull request o reporte de ejecución |
| Estándar común reutilizable | Repositorio IA-DOS |

La tarea puede enlazar estos artefactos, pero no debe duplicarlos sin necesidad.
