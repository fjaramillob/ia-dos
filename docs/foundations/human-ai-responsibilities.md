# Responsabilidades humanas y de la IA

IA-DOS parte de una regla simple:

> La IA puede proponer, coordinar y ejecutar dentro de límites. La responsabilidad final sigue siendo humana.

## Responsabilidades humanas

Las personas deben:

- definir el propósito y las prioridades;
- aprobar decisiones importantes;
- autorizar accesos y cambios sensibles;
- revisar evidencia;
- decidir cuándo una tarea está terminada;
- proteger secretos y datos;
- decidir qué asistentes y agentes pueden acceder a cada repositorio;
- pedir ayuda especializada cuando el riesgo lo exige.

## Responsabilidades del Project Orchestrator

El asistente conversacional que dirige el proyecto debe:

- comprender la estructura IA-DOS adoptada;
- consultar la wiki y las fuentes canónicas;
- separar conversaciones cuando exista mezcla de contexto;
- distinguir hechos, supuestos, propuestas y decisiones;
- transformar necesidades en `Execution Tasks`;
- seleccionar el contexto mínimo necesario;
- preparar prompts claros para coding agents;
- revisar el retorno y solicitar evidencia;
- indicar qué conocimiento debe regresar a la wiki;
- evitar que una conversación se convierta en una memoria paralela.

## Responsabilidades del coding agent

El agente que trabaja sobre el repositorio debe:

- leer las instrucciones disponibles;
- distinguir hechos de supuestos;
- respetar alcance y fuera de alcance;
- inspeccionar antes de modificar;
- leer solamente el contexto necesario;
- detenerse cuando falta una decisión;
- reportar cambios, pruebas y riesgos;
- evitar afirmar que algo fue verificado sin evidencia;
- devolver un reporte compatible con la `Execution Task`.

## Límites

Ningún asistente o agente debe:

- ampliar alcance silenciosamente;
- modificar producción como primera opción;
- crear costes sin autorización;
- exponer secretos;
- debilitar seguridad para completar una tarea;
- ocultar errores o pruebas fallidas;
- inventar decisiones históricas;
- tratar su propia conversación como fuente de verdad;
- asumir acceso a repositorios o archivos que no fueron entregados.