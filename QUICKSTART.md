# Quickstart (5 minutos)

Guia corta para aplicar esta base en cualquier proyecto, sin CI y sin lock-in.

## 1) Copia base al proyecto objetivo

Copia estos archivos/carpetas al repo donde vas a trabajar:

- `START-UP.md`
- `AGENTS.md`
- `Skills/`
- `scripts/validate-skills.sh`

## 2) Abri el proyecto con tu agente

Usa OpenCode o Claude Code sobre el repo objetivo.

Prompt recomendado:

```text
Usa START-UP.md como protocolo. Analiza el repo completo, propone AGENTS.md por capas,
y crea/ajusta skills en formato Skills/<nombre>/SKILL.md segun contexto real.
No inventes comandos. Mantene reglas verificables y anti-ruido.
```

## 3) Crea skills con tipado correcto

Toda skill nueva debe tener:

- `metadata.skill_type: capability_uplift` (capacidad temporal, revisable)
- o `metadata.skill_type: encoded_preference` (preferencia estable)

Regla clave:

- Si es `capability_uplift`, incluye `metadata.review_by`.

## 4) Valida en local

Desde el proyecto objetivo:

```bash
./scripts/validate-skills.sh --dry-run
./scripts/validate-skills.sh
```

Interpretacion:

- `0`: contrato OK
- `1`: hay errores a corregir

## 5) Ajusta y repite

Si falla algo, corregi `AGENTS.md` o `Skills/*/SKILL.md` y vuelve a validar.

## Referencias

- `README.md` - vision general
- `START-UP.md` - protocolo completo
- `MIGRACION.md` - plan de evolucion y retiro de legacy
