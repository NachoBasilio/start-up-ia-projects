# Migracion continua: AGENTS + Skills

Este repo NO es un museo. Es una base de arranque que debe mantenerse a la vanguardia.

Objetivo: migrar y mantener `AGENTS.md` y `Skills/*/SKILL.md` alineados con:

- formato moderno de skills,
- taxonomia `capability_uplift` vs `encoded_preference`,
- principio anti-ruido (arXiv:2602.11988) para no inflar contexto inutil.

## Alcance

- Estructura de skills y metadata.
- Gobernanza de `AGENTS.md`.
- Compatibilidad temporal de archivos legacy `Skills/*.md`.
- Proceso de revision periodica por mejoras de modelos.

## Versiones objetivo

- AGENTS contract: v2.x (breve, verificable, sin duplicacion)
- Skills contract: v2.x (`Skills/<name>/SKILL.md` + metadata obligatoria)

## Principios de migracion

1. Minimalismo operativo: menos texto, mas reglas accionables.
2. Compatibilidad sin deuda eterna: legacy solo como puente temporal.
3. Evidencia antes de reglas: no inventar politicas sin base en repo o fuentes.
4. Evolucion controlada: versionar cambios y definir retiro de lo viejo.

## Taxonomia obligatoria de skills

Toda skill debe tener `metadata.skill_type`:

- `capability_uplift`:
  - agrega capacidad tecnica temporal,
  - debe tener `review_by`,
  - debe planificar retiro (`sunset_at`) cuando el modelo ya cubre esa capacidad.
- `encoded_preference`:
  - codifica preferencias estables de equipo/producto,
  - no caduca por mejoras del modelo,
  - solo cambia si cambia la decision de negocio/equipo.

## Plan de migracion por fases

### Fase 1 - Inventario

- Listar todas las skills activas y legacy.
- Detectar referencias en `README.md`, `AGENTS.md`, `START-UP.md`.
- Marcar gaps de metadata obligatoria.

Salida esperada:

- Tabla: skill, ruta, tipo, estado (moderna/legacy), riesgo.

### Fase 2 - Normalizacion de estructura

- Convertir skills activas a `Skills/<name>/SKILL.md`.
- Mantener `Skills/*.md` solo como redirect temporal.
- Unificar rutas con `Skills/` (S mayuscula).

Salida esperada:

- Cero skills activas en formato legacy.

### Fase 3 - Normalizacion de metadata

Metadata minima obligatoria:

- `name`, `description`, `license`
- `metadata.author`, `metadata.version`, `metadata.scope`, `metadata.auto_invoke`
- `metadata.owner`, `metadata.skill_type`, `metadata.risk_level`, `metadata.allowed_tools`
- `metadata.review_by` obligatorio para `capability_uplift`
- `metadata.sunset_at` recomendado para `capability_uplift`

Salida esperada:

- 100% skills con metadata valida.

### Fase 4 - Alineacion documental

- Actualizar `AGENTS.md` con fuente de verdad y reglas de compatibilidad.
- Actualizar `README.md` para onboarding en espanol.
- Mantener `START-UP.md` como protocolo canonico.

Salida esperada:

- No hay contradicciones entre AGENTS, README, START-UP y skills.

### Fase 5 - Retiro de legacy

- Definir fecha de corte para redirects `Skills/*.md`.
- Comunicar breaking change en release notes.
- Eliminar redirects al finalizar ventana de compatibilidad.

Salida esperada:

- Solo existe formato moderno.

## Cadencia de mantenimiento (vanguardia real)

- Revision mensual de `capability_uplift`.
- Revision extraordinaria ante release fuerte de modelo.
- Cada revision clasifica cada skill en:
  - `keep`: sigue aportando valor,
  - `refine`: requiere ajuste,
  - `sunset`: retirar por obsolescencia.

## Checklist rapido de migracion

- [ ] No se agregaron skills nuevas en `Skills/*.md`.
- [ ] Toda skill declara `skill_type`.
- [ ] Todas las `capability_uplift` tienen `review_by`.
- [ ] `AGENTS.md` no duplica contenido de otras fuentes.
- [ ] `README.md` explica tipos de skills para usuarios nuevos.
- [ ] Rutas y referencias validas (`Skills/` correcto).
- [ ] Se ejecuto `./scripts/validate-skills.sh` con resultado exitoso.

## Automatizacion recomendada

Usar estos comandos en local (sin depender de CI):

```bash
./scripts/validate-skills.sh --dry-run
./scripts/validate-skills.sh
```

Semantica de salida:

- `0`: validacion OK
- `1`: hay errores de contrato/migracion

## Definicion de done

- Estructura moderna aplicada.
- Taxonomia aplicada y auditable.
- Legacy encapsulado o retirado segun fase.
- Documentacion consistente y sin ruido.
