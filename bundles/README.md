# Bundles de IA-DOS

Esta carpeta conserva artefactos de distribución offline de distintas generaciones de IA-DOS.

## Bundle vigente

Para un onboarding nuevo sin acceso al repositorio canónico usa **únicamente**:

```text
ia-dos-current-offline-pack.md
```

Ese archivo debe declarar en su encabezado:

- `Estado: VIGENTE`;
- baseline canónico o versión de IA-DOS con la que fue sincronizado.

Si el encabezado no declara vigencia y baseline, no lo trates como pack actual.

## Bundles históricos

Los siguientes archivos se conservan para trazabilidad y compatibilidad con referencias antiguas, pero **no deben utilizarse para nuevos onboardings**:

```text
ia-dos-project-orchestrator-pack.md
ia-dos-agent-role-and-artifact-loop-addon.md
ia-dos-fast-planning-addon.md
ia-dos-typed-compact-addon.md
```

Pueden contener conceptos, nombres, contratos o instrucciones que fueron reemplazados posteriormente.

No combines esos archivos entre sí para reconstruir el método actual y no los agregues al Current Offline Pack.

## Fuente canónica

Cuando el asistente puede navegar el repositorio, la fuente canónica son los documentos vigentes de `main`.

El bundle offline es un artefacto de distribución, no una segunda fuente de verdad.

## Regla de actualización

Cuando cambien contratos canónicos que afecten onboarding u operación offline:

1. actualiza primero la documentación canónica;
2. valida su coherencia;
3. regenera `ia-dos-current-offline-pack.md`;
4. actualiza su baseline declarado;
5. verifica que los bundles históricos sigan marcados como históricos.

No edites un bundle histórico para convertirlo silenciosamente en el método vigente. Si deja de representar la versión a la que pertenecía, pierde valor como evidencia histórica.
