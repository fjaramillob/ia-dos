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

## Method Resolution Policy

Un proyecto puede resolver qué IA-DOS obedecer de dos formas:

```text
Method Resolution Policy:
FOLLOW_CURRENT | PINNED
```

### FOLLOW_CURRENT

Usa la referencia canónica vigente del repositorio IA-DOS cuando comienza un nuevo outcome, sesión relevante o alineación metodológica.

Es apropiado cuando el proyecto prefiere incorporar mejoras del método sin mantener un ciclo manual de upgrades.

Reglas:

- una mención de versión o SHA en un chat, prompt, Execution Report o mensaje histórico **no constituye un pin durable**;
- no incrustes un SHA fijo en prompts operativos cotidianos salvo que el objetivo sea reproducir deliberadamente un baseline histórico;
- resuelve el método al comienzo del outcome y mantén ese snapshot metodológico estable durante la ejecución;
- no cambies reglas a mitad de una Execution sólo porque `main` avance;
- antes del siguiente outcome relevante vuelve a resolver la referencia vigente.

### PINNED

El proyecto declara durablemente una versión, tag o commit concreto, por ejemplo en `.ia-dos.yaml` o una fuente equivalente de adopción.

Es apropiado cuando se necesita reproducibilidad, auditoría estricta o upgrades deliberados.

Reglas:

- el pin debe existir en una fuente durable del proyecto;
- un proyecto PINNED revisa los cambios antes de adoptar otra versión;
- mientras el pin siga vigente, `main`, `latest` o una mención conversacional más nueva no lo sustituyen.

## Resolución por defecto

Si el proyecto no declara de forma durable una política o pin:

```text
Method Resolution Policy = FOLLOW_CURRENT
```

Esto evita que conversaciones antiguas congelen accidentalmente IA-DOS.

La reproducibilidad debe ser una decisión explícita, no un efecto lateral de haber pegado alguna vez un SHA en un prompt.
