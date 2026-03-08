# Start-up IA Projects

Plantilla operativa para arrancar proyectos con IA de forma profesional, auditable y sin humo.

Este repositorio define un flujo genérico para que cualquier agente:

- entienda primero el contexto real del proyecto,
- proponga reglas y skills consistentes con el código,
- y valide calidad técnica antes de cerrar cambios.

## Qué incluye

- `start-up.md`  
  Protocolo principal por fases para diseñar `AGENTS.md` y skills en cualquier repo.
- `Skills/skill-creator.md`  
  Guía traducida y operativa para crear skills nuevas.
- `Skills/skill-sync.md`  
  Guía traducida y operativa para sincronizar metadatos y auto-invocación de skills.

## Flujo recomendado

1. Copiá `start-up.md` en el repo objetivo.
2. Ejecutá el Paso 0 obligatorio: preguntar tipo de proyecto y arquitectura.
3. Hacé análisis completo del repo (Fase 1).
4. Diseñá `AGENTS.md` por capas (Fase 2).
5. Diseñá/ajustá skills (Fase 3), apoyándote en `Skills/`.
6. Verificá coherencia técnica y documental (Fase 4).
7. Ejecutá validaciones técnicas del stack activo (Fase 5).

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
