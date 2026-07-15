# Seguridad

IA-DOS contiene documentación, plantillas y prácticas operativas. Aun así, una contribución podría introducir instrucciones inseguras o exponer información sensible.

## No publiques secretos

No incluyas en issues, pull requests, ejemplos o documentos:

- contraseñas;
- tokens;
- API keys;
- credenciales cloud;
- claves privadas;
- datos personales sensibles;
- URLs internas con acceso restringido.

## Conectores, MCP y herramientas externas

La existencia de un conector, servidor MCP, API o herramienta con acceso no autoriza automáticamente su uso.

Antes de operar sobre una fuente externa:

- verifica la identidad, cuenta, workspace, proyecto o repositorio conectado;
- limita permisos y scopes al mínimo necesario;
- separa lectura, escritura, eliminación, ejecución y administración;
- exige autorización explícita para acciones sensibles o destructivas;
- evita copiar credenciales en prompts, wiki, issues o pull requests;
- utiliza mecanismos seguros de autenticación provistos por la plataforma;
- registra evidencia sin exponer secretos;
- revoca accesos que ya no sean necesarios.

Un `Capability Manifest` nunca debe contener credenciales. Su función es describir capacidades y límites, no almacenar secretos ni conceder permisos.

## Reportar un problema

Si detectas una vulnerabilidad o una instrucción que podría causar pérdida de datos, exposición de secretos o cambios inseguros en producción, evita publicarla inicialmente en un issue abierto.

Contacta al maintainer mediante un canal privado disponible en su perfil de GitHub e incluye:

- descripción del problema;
- archivo o sección afectada;
- posible impacto;
- pasos para reproducirlo cuando corresponda;
- propuesta de mitigación, si existe.

## Alcance

Esta política cubre el contenido oficial del repositorio IA-DOS. Los proyectos que adopten el framework mantienen la responsabilidad sobre su propia seguridad, infraestructura, credenciales, conectores, servidores MCP y código.
