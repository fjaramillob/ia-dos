# Criterios editoriales

La documentación principal de IA-DOS está escrita en español.

## Estilo

- usar lenguaje directo;
- explicar términos técnicos;
- evitar promesas no implementadas;
- evitar adornos innecesarios;
- distinguir recomendaciones de requisitos;
- utilizar ejemplos genéricos;
- no asumir experiencia avanzada en programación.

## Agnosticismo

IA-DOS es agnóstico respecto de proyectos, dominios, proveedores, plataformas, modelos, editores, agentes, stacks y servicios.

La documentación normativa, las plantillas, los prompts y los packs deben usar roles genéricos como:

- asistente conversacional;
- Project Orchestrator;
- Conversation Space;
- coding agent;
- entorno de ejecución;
- repositorio de producto;
- LLM Wiki.

Los nombres concretos de herramientas pueden aparecer únicamente como ejemplos opcionales y no vinculantes. Nunca deben convertirse en requisitos, pasos obligatorios o supuestos de capacidad.

Una regla debe seguir siendo válida aunque cambien el proveedor, el modelo, el editor, la plataforma de conversación, el servicio de control de versiones o la infraestructura.

## Aislamiento entre proyectos

Todo artefacto generado para un proyecto debe utilizar únicamente:

- el nombre del proyecto actual recibido como parámetro;
- sus fuentes autorizadas;
- sus rutas, dominios y repositorios explícitos;
- sus decisiones y evidencias verificadas.

No deben arrastrarse referencias provenientes de:

- proyectos usados durante pruebas;
- conversaciones anteriores;
- ejemplos privados;
- otros repositorios conectados;
- memoria no confirmada;
- respuestas de validación del framework.

Una frase como “se revisó [PROYECTO EXTERNO] contra IA-DOS” no debe aparecer en otro proyecto. La forma correcta es genérica:

```text
Se revisaron las fuentes del proyecto actual contra las reglas canónicas de IA-DOS.
```

## Nombres estructurales

Las carpetas y archivos técnicos utilizan nombres en inglés cuando facilita compatibilidad y colaboración.

Ejemplos:

- `docs/`;
- `templates/`;
- `prompts/`;
- `research/`;
- `README.md`;
- `AGENTS.md`.

## Terminología

Los términos técnicos establecidos pueden mantenerse en inglés, pero deben explicarse en español al aparecer por primera vez.

## Sanitización para contenido público

Todo contenido incorporado al repositorio público debe revisarse antes de publicarse.

No deben aparecer:

- nombres de proyectos personales, laborales o de clientes;
- dominios, marcas, repositorios o rutas que permitan identificar proyectos reales;
- nombres de personas, equipos, empresas o comunidades usados como contexto privado;
- secretos, credenciales, tokens, API keys o variables de entorno reales;
- datos personales, financieros, contractuales o internos;
- configuraciones privadas;
- capturas, logs o ejemplos copiados desde proyectos reales sin anonimización.

Cuando se necesite un ejemplo, utiliza nombres sintéticos como:

```text
portal-clientes
sistema-inventario
agenda-equipos
```

Los ejemplos deben enseñar la convención sin depender de la historia de una persona o proyecto específico.

## Revisión antes de publicar o reutilizar

Antes de cerrar un handoff, prompt, documento, pack o reporte:

1. confirma que todas las referencias pertenecen al proyecto actual o son placeholders;
2. reemplaza marcas y herramientas por roles genéricos cuando formen parte de una regla;
3. elimina nombres y rutas heredadas de pruebas;
4. distingue ejemplos opcionales de requisitos normativos;
5. verifica que el artefacto pueda reutilizarse en otro entorno sin reescritura estructural.

## Contenido no permitido

La documentación común no debe incluir:

- nombres de proyectos particulares;
- secretos;
- configuraciones privadas;
- afirmaciones de capacidades inexistentes;
- reglas basadas únicamente en preferencias personales sin justificación;
- dependencias normativas de una plataforma o proveedor específico.