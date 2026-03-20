# Start-up con IA que no sea un desastre

Después de ver mil proyectos donde la IA genera código que "funciona" pero es un quilombo mantenible, armé esta plantilla para empezar proyectos con agentes de manera seria.

La idea es simple: que la IA entienda realmente tu proyecto antes de tocar una línea de código, que proponga cosas que tengan sentido con tu stack, y que valide que no rompió nada antes de mandarte el commit.

## Lo que encontrás acá

**START-UP.md** → El protocolo completo por fases. Lo que realmente necesitás para que un agente no haga cualquier cosa en tu repo.

**Skills/** → Templates para crear skills que no sean genéricas. Divididas en dos tipos:
- `capability_uplift`: capacidades técnicas que van a quedar obsoletas cuando los modelos mejoren
- `encoded_preference`: tus preferencias de trabajo que no cambian porque OpenAI saque GPT-X

**MIGRACION.md** → Cómo migrar sin romper todo si ya tenés algo armado.

**scripts/validate-skills.sh** → Validador que realmente funciona, no como esos linters que "pasan" pero el código es una mierda.

**tests/** → Tests del validador porque sí, hasta los scripts de validación necesitan tests.

**.github/workflows/** → CI que no rompe, enforcement automático sin ser un pain in the ass.

## Skills: el formato que no te va a cagar

Acá uso `Skills/<skill-name>/SKILL.md` como estándar. 

Los archivos viejos `Skills/*.md` los mantengo por compatibilidad, pero la verdad está siempre en el subdirectorio. Cuando tengas tiempo, migralos.

### Por qué dos tipos de skills

Después de romper algunos proyectos, me di cuenta que hay skills que:

- **capability_uplift**: Agregan algo técnico que el modelo no sabe hacer bien todavía. Estas van a quedar obsoletas cuando GPT-5 o Claude-Next las hagan nativas.

- **encoded_preference**: Son TUS reglas de trabajo. Cómo querés que se nombre las variables, qué patterns usás, etc. Estas no caducan porque son tuyas, no del modelo.

## La regla que no se negocia

No importa si usás React, Go, Python o COBOL. SIEMPRE:

- **Linter configurado** y corriendo
- **Validaciones antes de commit** 
- **Tests que realmente prueban algo**

Sin esto, cualquier IA va a generar código que "funciona" en su máquina pero es un desastre en producción.

## La filosofía detrás de esto

Este template es genérico a propósito. No te va a decir "usá React con TypeScript y Tailwind" porque no soy idiota. La IA tiene que adaptarse a TU stack, TU forma de trabajar, TU arquitectura.

He visto demasiados proyectos donde el agente propone "mejores prácticas" que no tienen nada que ver con lo que ya está funcionando. Este approach fuerza a la IA a entender primero, proponer después.

## Créditos donde corresponde

Esto lo armé yo, **Ignacio Nicolas Basilio Buracco (Ignadev)**, después de años rompiendo y arreglando código en QA Automation.

- Web: [ignadev.com](https://ignadev.com/)
- GitHub: [@NachoBasilio](https://github.com/NachoBasilio)
- LinkedIn: [ignacio-nicolas-basilio-buracco](https://www.linkedin.com/in/ignacio-nicolas-basilio-buracco/)

Pero la base conceptual la saqué de todo lo que aprendí viendo [Gentleman Programming](https://www.youtube.com/@gentlemanprogramming). Si no los conocés, están haciendo el mejor contenido en español sobre desarrollo serio.

---

*PD: Si esto te sirvió y lo mejorás, mandá un PR. Si lo usás y algo no funciona, abrí un issue. Si no te gusta, está todo bien, probably no es para vos.*
