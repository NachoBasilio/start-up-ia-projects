---
name: skill-sync
description: >
  Audita y sincroniza metadata de skills para mantener coherencia entre
  Skills/*/SKILL.md, AGENTS.md y start-up.md. Usar despues de crear/modificar
  skills o al migrar desde formato legacy.
license: Apache-2.0
metadata:
  author: ignadev
  version: "2.0.0"
  scope:
    - root
  auto_invoke:
    - "sincronizar skills"
    - "validar skills"
    - "actualizar AGENTS skills"
    - "migrar skills legacy"
  owner: repo-maintainers
  skill_type: encoded_preference
  risk_level: medium
  allowed_tools:
    - read
    - glob
    - grep
    - apply_patch
---

# skill-sync

## Cuando usar

- Despues de crear o modificar cualquier skill.
- Cuando AGENTS/README/start-up quedan desalineados con Skills.
- Antes de cerrar una migracion legacy a formato moderno.

## Validaciones obligatorias

1. Estructura: `Skills/<nombre>/SKILL.md`.
2. Metadata minima: `name`, `description`, `license`, `metadata.scope`, `metadata.auto_invoke`, `metadata.version`, `metadata.owner`.
3. Taxonomia: `metadata.skill_type` debe ser `capability_uplift` o `encoded_preference`.
4. Ciclo de vida: si `skill_type=capability_uplift`, `review_by` es obligatorio y `sunset_at` recomendado.
5. Permanencia: si `skill_type=encoded_preference`, no exigir caducidad por mejora de modelo.
6. Casing correcto: usar `Skills/` (no `skills/`).
7. Referencias vivas: AGENTS/README/start-up apuntan a rutas existentes.
8. Compatibilidad: archivos legacy `Skills/*.md` solo como redirect.

## Reglas criticas

- No inventar scripts: si no existe automatizacion, dejarlo como pendiente explicito.
- Priorizar cambios auditables y pequenos.
- Evitar ruido: actualizar solo secciones afectadas.

## Checklist rapido

- [ ] Todas las skills activas estan en formato moderno.
- [ ] Las referencias legacy no son fuente de verdad.
- [ ] Toda skill declara `skill_type` valido.
- [ ] Las `capability_uplift` tienen `review_by`.
- [ ] No hay paths con `skills/` minuscula.
- [ ] AGENTS y README reflejan la estructura real.

## Comandos

```bash
./scripts/validate-skills.sh --dry-run
./scripts/validate-skills.sh
```
