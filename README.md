# Start-up IA Projects

Plantilla operativa para arrancar proyectos con IA de forma profesional, auditable y sin humo.

Este repositorio define un flujo genérico para que cualquier agente:

- entienda primero el contexto real del proyecto,
- proponga reglas y skills consistentes con el código,
- y valide calidad técnica antes de cerrar cambios.

## Qué incluye

- `START-UP.md`  
  Protocolo principal por fases para diseñar `AGENTS.md` y skills en cualquier repo.
- `Skills/skill-creator/SKILL.md`  
  Skill base para crear skills nuevas en formato moderno.
- `Skills/skill-sync/SKILL.md`  
  Skill base para auditar y sincronizar metadatos de skills.
- `Skills/*/assets` y `Skills/*/references`  
  Recursos opcionales por skill (plantillas, scripts, guias).
- `MIGRACION.md`  
  Plan por fases para mantener AGENTS y skills en formato moderno sin arrastrar deuda legacy.
- `QUICKSTART.md`  
  Guia corta para aplicarlo en un repo nuevo en 5 minutos.

## Formato moderno de skills

Este repo usa como formato canonico:

`Skills/<skill-name>/SKILL.md`

Compatibilidad:

- `Skills/*.md` queda como legacy temporal para no romper integraciones.
- La fuente de verdad siempre es `Skills/*/SKILL.md`.

### Tipos de skills (clave para arrancar bien)

- `capability_uplift`: agrega capacidades tecnicas que pueden quedar viejas cuando los modelos mejoran; deben revisarse y caducar cuando ya no aportan.
- `encoded_preference`: codifica preferencias estables del equipo/producto; no caducan por mejora de modelo, solo cambian si cambia tu forma de trabajar.

## Flujo recomendado

1. Copiá `START-UP.md` en el repo objetivo.
2. Ejecutá el Paso 0 obligatorio: preguntar tipo de proyecto y arquitectura.
3. Hacé análisis completo del repo (Fase 1).
4. Diseñá `AGENTS.md` por capas (Fase 2).
5. Diseñá/ajustá skills (Fase 3), apoyándote en `Skills/`.
6. Verificá coherencia técnica y documental (Fase 4).
7. Ejecutá validaciones técnicas del stack activo (Fase 5).
8. Ejecutá validacion de contrato de skills (comando canonico): `./scripts/validate-skills.sh`.

## Uso local (sin lock-in)

Este repo esta pensado para uso directo por cualquier persona o equipo:

1. Clona o descarga este repositorio.
2. Copia `START-UP.md`, `AGENTS.md` y `Skills/` al proyecto objetivo.
3. Abri ese proyecto con OpenCode o Claude Code.
4. Pedi crear/ajustar `AGENTS.md` y skills segun el contexto real del repo.
5. Corre localmente el validador canonico:

```bash
./scripts/validate-skills.sh
```

Ejemplo de salida esperada:

```text
[INFO] Validando skills en /ruta/al/repo
[INFO] Validando /ruta/al/repo/Skills/skill-creator/SKILL.md
[INFO] Validando /ruta/al/repo/Skills/skill-sync/SKILL.md

Resumen: 0 error(es), 0 warning(s)
```

Tambien hay enforcement en CI (GitHub Actions) para `push` y `pull_request`.

No requiere configuracion de plataforma propietaria para funcionar.

## Validacion automatizada

- Validador canonico: `./scripts/validate-skills.sh`
- Tests del validador: `./tests/validate-skills.test.sh`

## Regla de calidad no negociable

Para cualquier lenguaje o stack, SIEMPRE:

- definir y ejecutar un linter (o equivalente),
- ejecutar validaciones antes de cerrar fases,
- ejecutar validaciones antes de cada commit.

## Enfoque

Esta base es genérica a propósito. La IA debe adaptar comandos, paths, checkers y decisiones al contexto real de cada proyecto.

## Autor

Creado por **Ignacio Nicolas Basilio Buracco (Ignadev)**, basado en experiencia real en QA Automation y desarrollo.

- Sitio: `https://ignadev.com/`
- GitHub: `https://github.com/NachoBasilio`
- LinkedIn: `https://www.linkedin.com/in/ignacio-nicolas-basilio-buracco/`
- Email: `ignacio.n.basilio.b@gmail.com`

## Inspiración

Este enfoque está fuertemente influenciado por lo aprendido en la comunidad y contenidos de **Gentleman Programming**.

- YouTube: `https://www.youtube.com/@gentlemanprogramming`
- GitHub: `https://github.com/Gentleman-Programming`
