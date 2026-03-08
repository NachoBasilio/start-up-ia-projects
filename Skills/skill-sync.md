# skill-sync (traducción operativa)

## Propósito

Mantener sincronizadas las secciones de auto-invocación en `AGENTS.md` a partir de los metadatos definidos en cada skill.

## Cuándo usar

- Después de crear/modificar una skill.
- Cuando una skill no aparece en tablas de auto-invocación.
- Cuando se regenere documentación de skills.

## Metadatos requeridos en cada skill

En `SKILL.md`:

```yaml
metadata:
  author: { equipo-o-org }
  version: "1.0"
  scope: [root] # o múltiples scopes
  auto_invoke: "Acción" # string o lista de acciones
```

`auto_invoke` puede ser:

- una sola acción (`"Crear componentes"`)
- una lista de acciones (`["Crear componentes", "Refactor de estructura"]`)

## Flujo recomendado

1. Editar o crear la skill.
2. Verificar que tenga `metadata.scope` y `metadata.auto_invoke`.
3. Ejecutar el script/comando de sincronización que use el proyecto.
4. Revisar cambios en `AGENTS.md`.

## Comandos ejemplo

```bash
# Ejecutar sync completo (si existe en el proyecto)
./skills/skill-sync/assets/sync.sh

# Simular cambios
./skills/skill-sync/assets/sync.sh --dry-run

# Sincronizar un scope
./skills/skill-sync/assets/sync.sh --scope root
```

## Checklist antes de cerrar

- [ ] Todas las skills nuevas tienen `scope`.
- [ ] Todas las skills nuevas tienen `auto_invoke`.
- [ ] Se ejecutó sincronización.
- [ ] Se validó que `AGENTS.md` quedó consistente.
