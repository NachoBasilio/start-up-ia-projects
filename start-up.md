# Start-up para cualquier IA

Usá este archivo como protocolo de arranque antes de crear o refactorizar `AGENTS.md` y `skills`.

## Objetivo

Crear una base profesional, en español y GENÉRICA para cualquier proyecto, que luego se adapte al contexto real después de un análisis completo del repositorio.

Incorporar un criterio de minimalismo operativo para `AGENTS.md`: incluir solo señales de alto valor y evitar texto redundante.

## Reglas de trabajo

1. Todo en español claro y profesional.
2. "Hazlo simple, pero no fácil": evitar atajos frágiles.
3. No inventar reglas; derivarlas del código, estructura y convenciones existentes.
4. No romper comportamiento actual del proyecto.
5. Documentación y skills deben reflejar la realidad (si no se cumple, ajustar texto o código).
6. Para CUALQUIER lenguaje del proyecto, definir y ejecutar un validador de calidad de código (linter y/o análisis equivalente) de forma obligatoria.
7. `AGENTS.md` debe ser corto, específico y verificable: no copiar contenido que ya exista en `README`, `docs` o skills.
8. Evitar sobre-instrucciones: cada regla en `AGENTS.md` debe reducir decisiones, no abrir ramas nuevas.

## Principio anti-ruido para AGENTS.md

Basado en evidencia empírica reciente (arXiv:2602.11988), más contexto no implica mejores resultados para agentes. Por defecto:

- No agregar "overview" largo de carpetas o componentes si es inferible del repo.
- No duplicar comandos o políticas que ya estén bien documentadas.
- No meter procesos completos en `AGENTS.md`; referenciar la fuente canónica.
- Priorizar restricciones de alto impacto: seguridad, contratos, compatibilidad y validaciones mínimas.

Excepción controlada:

- Si el repo tiene documentación muy pobre o inexistente, ampliar `AGENTS.md` solo con lo mínimo necesario para ejecutar setup/tests.

## Fase 1 - Análisis completo (obligatoria)

### Paso 0 - Preguntas obligatorias al iniciar

Antes de analizar o proponer cambios, la IA debe preguntar y confirmar:

- Tipo de proyecto (web, API, mobile, desktop, librería, monorepo, etc.).
- Arquitectura esperada o existente (por capas, hexagonal, clean, modular, feature-first, etc.).

Si el usuario no lo define con claridad:

- La IA debe proponer una hipótesis inicial basada en el repo.
- Debe marcarla explícitamente como "suposición a validar".
- No debe cerrar AGENTS/skills finales sin esta validación.

Antes de escribir cualquier AGENTS/skill:

- Detectar stack, framework, estructura de carpetas y tipo de proyecto.
- Revisar configuración real (`package.json`, lint, release, build, rutas, etc.).
- Buscar documentación existente (`AGENTS.md`, `notes`, `README`, skills previas).
- Detectar convenciones reales de commits con `git log`.
- Identificar zonas críticas y patrones repetidos del proyecto.

Salida mínima de esta fase:

- Mapa de carpetas clave.
- Reglas verificables (las que sí se pueden cumplir y auditar).
- Lista de skills necesarias y dónde aplican.

## Fase 2 - Diseño de AGENTS.md

Crear jerarquía por contexto:

- `AGENTS.md` en raíz (reglas globales + tabla de skills + auto-invocación).
- `AGENTS.md` por áreas importantes (`src`, `components`, `routes`, `services`, etc.), según corresponda.
- Regla de precedencia: la guía más cercana al código manda.

Diseño recomendado (minimalista):

- 4 a 6 secciones máximas.
- 3 a 5 reglas obligatorias máximas.
- Una sola línea de criterio de finalización verificable (`Definition of done`).
- Referencias explícitas a documentos fuente en vez de duplicar contenido.

Cada AGENTS debe incluir:

- alcance,
- reglas específicas,
- auto-invocar skills,
- checklist obligatorio.

Checklist anti-redundancia obligatorio:

- [ ] Cada regla aporta información no presente en `README`, `docs` o skills.
- [ ] No hay secciones narrativas largas sin decisión operativa.
- [ ] No hay listas extensas de herramientas/comandos sin condición de uso.
- [ ] Se define precedencia de fuentes para resolver contradicciones.

## Fase 3 - Diseño de skills

Crear skills accionables (no teóricos):

- ubicación: `skills/<nombre>/SKILL.md`
- frontmatter + trigger claro
- reglas críticas
- checklist rápido
- comandos de validación cuando aplique

Siempre enlazar skills nuevas en `AGENTS.md`.

### Referencia obligatoria para crear/sincronizar skills (traducido)

- **`skill-creator`** (crear skills):
  - Úsalo cuando necesites crear una skill nueva reusable para el proyecto.
  - Define estructura estándar: `skills/<nombre>/SKILL.md` (+ `assets/` y `references/` opcionales).
  - Incluye frontmatter completo, reglas críticas, ejemplos mínimos y comandos.
  - Evitá skills para casos triviales o one-off.
  - Referencia local: `Skills/skill-creator.md`

- **`skill-sync`** (sincronizar metadatos en AGENTS):
  - Úsalo después de crear/modificar una skill.
  - Exige `metadata.scope` y `metadata.auto_invoke` en `SKILL.md`.
  - Sincroniza automáticamente tablas de auto-invocación en `AGENTS.md`.
  - Ejecutá el comando/script de sincronización que exista en el proyecto (por ejemplo el `sync.sh` del skill).
  - Referencia local: `Skills/skill-sync.md`

Nota de adaptación automática:

- Esta guía es deliberadamente genérica.
- La IA debe ajustar herramientas, comandos, paths y validadores al stack real detectado en el proyecto actual.

## Fase 4 - Verificación de coherencia

Auditar que no haya contradicciones entre:

- AGENTS,
- skills,
- configuración real del proyecto,
- comportamiento actual del código.

Si hay conflicto, corregir de inmediato (no dejar “mentiras” en documentación).

## Fase 5 - Validación técnica

Ejecutar validaciones del proyecto (mínimo):

- lint (o equivalente para el lenguaje: por ejemplo `ruff`, `golangci-lint`, `eslint`, `flake8`, etc.)
- typecheck/build (según stack)

Regla obligatoria de calidad:

- Antes de cerrar una fase de cambios y antes de commitear, correr validadores de código del stack activo.
- Si no existe linter configurado, definir uno o un mecanismo equivalente de análisis estático antes de continuar.

Luego resumir cambios por grupos lógicos.

## Entrega esperada

- AGENTS en español, por capas y sin contradicciones.
- Skills profesionales y personalizadas al proyecto.
- Checklist operativo para mantener calidad.
- Resumen claro de qué se creó, por qué y dónde.
