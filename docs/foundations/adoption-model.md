# Modelo de adopción

IA-DOS se adopta por proyecto. No se copia completo dentro de cada repositorio.

## Relación entre IA-DOS y un proyecto

```text
IA-DOS
    define cómo trabajar

Proyecto
    define qué construir, para quién y bajo qué decisiones
```

Cada proyecto mantiene su propia:

- aplicación;
- wiki;
- arquitectura;
- decisiones;
- tareas;
- riesgos;
- historial.

## Estructura recomendada

```text
proyectos/
├── 00-ia-dos/
└── nombre-proyecto/
    ├── nombre-proyecto-app/
    └── nombre-proyecto-wiki/
```

IA-DOS recomienda con fuerza esta separación porque ayuda a distinguir implementación y memoria. Sin embargo, no es obligatoria.

Un proyecto puede utilizar:

- dos repositorios separados;
- un monorepo;
- documentación dentro del mismo repositorio;
- una wiki privada o exclusivamente local.

La excepción debe quedar documentada cuando afecte la forma de trabajo.

## Visibilidad

La app y la wiki pueden ser públicas o privadas según la naturaleza del proyecto.

La wiki nunca debe contener secretos, contraseñas, API keys ni credenciales.

## Versión adoptada

Cada proyecto debe declarar qué versión de IA-DOS utiliza.

La primera plantilla de adopción se incorporará en un siguiente incremento de `v0.1.0-alpha.1`.

Los proyectos no reciben cambios del framework de forma silenciosa. Cada actualización debe revisarse antes de adoptarse.
