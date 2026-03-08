# skill-creator (traducción operativa)

## Propósito

Crear nuevas skills para agentes de IA siguiendo una estructura consistente, reutilizable y auditable.

## Cuándo crear una skill

Creala cuando:

- Un patrón se repite y la IA necesita guía específica.
- Las convenciones del proyecto difieren de prácticas genéricas.
- Hay flujos complejos que requieren pasos claros.
- Necesitás reglas de decisión para elegir enfoques.

No la crees cuando:

- Ya existe documentación suficiente que se puede referenciar.
- Es un caso trivial o autoexplicativo.
- Es una tarea one-off.

## Estructura sugerida

```text
skills/{skill-name}/
├── SKILL.md
├── assets/        # opcional
└── references/    # opcional
```

## Plantilla mínima de SKILL.md

```yaml
---
name: { skill-name }
description: >
  {Qué hace}.
  Trigger: {Cuándo debe cargarse}.
license: Apache-2.0
metadata:
  author: { equipo-o-org }
  version: "1.0"
---
```

Secciones recomendadas:

- Cuándo usar
- Patrones críticos
- Ejemplos concretos
- Comandos
- Recursos

## Convenciones de naming

- Genérica: `{technology}`
- Específica de producto: `{producto}-{dominio}`
- Testing: `{producto}-test-{dominio}`
- Workflow: `{accion}-{objetivo}`

## Guía de contenido

Hacé:

- Reglas críticas primero.
- Ejemplos chicos y útiles.
- Checklists accionables.

Evitá:

- Texto largo sin decisiones concretas.
- Duplicar documentación existente.

## Checklist antes de cerrar

- [ ] La skill no duplica otra existente.
- [ ] El trigger es claro.
- [ ] El frontmatter está completo.
- [ ] Incluye comandos verificables.
- [ ] Está referenciada desde `AGENTS.md`.
