# Versionado

IA-DOS utiliza versionado semántico:

```text
MAJOR.MINOR.PATCH
```

Ejemplos:

```text
0.1.0-alpha.4
0.1.0
0.2.0
1.0.0
```

## PATCH

Se utiliza para:

- correcciones;
- aclaraciones;
- enlaces;
- mejoras editoriales;
- cambios que no alteran obligaciones.

## MINOR

Se utiliza para:

- nuevas plantillas;
- nuevos documentos;
- nuevos flujos compatibles;
- ampliaciones que no rompen adopciones existentes.

## MAJOR

Se utiliza para:

- cambios incompatibles;
- nuevas obligaciones centrales;
- eliminación o sustitución de contratos operativos;
- cambios profundos en la forma de adopción.

## Etapa `0.x` y prereleases

Durante la etapa experimental, IA-DOS puede usar identificadores prerelease como `alpha.N` para distinguir baselines operativos antes de estabilizar una versión.

Cada identificador prerelease debe tener un único significado vigente entre Roadmap, Current Offline Pack y documentación de adopción. No reutilices el mismo `alpha.N` para dos outcomes distintos.

Una versión minor o prerelease puede incluir ajustes importantes. Estos cambios deben quedar descritos en `CHANGELOG.md`.

## Adopción por proyectos

Cada proyecto fija una versión concreta de IA-DOS.

No se recomienda declarar adopción mediante referencias como `latest` o `main`.

Un proyecto debe revisar los cambios antes de actualizar la versión adoptada.
