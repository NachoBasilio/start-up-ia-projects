# AGENTS.md

Guia minima para agentes que trabajen en este repo.

## Objetivo

Evitar ruido: este archivo define solo reglas operativas no obvias.

## Fuente de verdad (orden de precedencia)

1. Solicitud explicita del usuario.
2. Este `AGENTS.md` (reglas minimas y verificables).
3. `README.md` (vision y flujo general).
4. `start-up.md` y `Skills/*.md` (proceso detallado y referencias).

Si dos fuentes se contradicen, gana la de mayor precedencia.

## Reglas obligatorias

1. No duplicar contenido: si una regla ya existe en `README.md`, `start-up.md` o `Skills/*.md`, referenciarla en lugar de reescribirla.
2. No inventar comandos: usar solo comandos realmente disponibles en el repo o declararlos como "pendientes de definir".
3. Mantener cambios auditables: cada cambio debe explicar que se hizo, por que y en que archivo.
4. Preservar coherencia: documentacion y contenido deben reflejar el estado real del repo.

## Flujo minimo para cambios de documentacion

1. Leer `README.md` y `start-up.md` para detectar reglas ya existentes.
2. Cambiar solo lo necesario para resolver la solicitud actual.
3. Eliminar redundancias evidentes en lugar de sumar texto nuevo.
4. Cerrar con un resumen corto de cambios por archivo.

## Definition of done

- No hay texto repetido entre `AGENTS.md`, `README.md`, `start-up.md` y `Skills/*.md`.
- Todas las reglas del archivo son accionables y verificables.
- El archivo se mantiene breve y enfocado en decisiones operativas.
