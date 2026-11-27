# ui-ux — skill de UI/UX para Claude Code

Skill de diseño de interfaces (web, mobile y desktop) para Claude Code y otros agentes compatibles con `SKILL.md`.

Base: [UI/UX Pro Max](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) (MIT, commit `11ca2b3`), la skill de UI/UX más usada. Trae 141 reglas de UX, 80 estilos, 194 paletas, 74 combinaciones de fuentes, guías por stack y un buscador local en Python.

## Qué agregué

`skills/ui-ux/references/craft-tips.md`: 19 reglas de pulido visual y microinteracciones que la base no tenía:

- **Visual:** sombras en capas, párrafos alineados a la izquierda, grises con tinte, texto teñido sobre color, un tono por color, texto del botón ≈ mitad de su alto, más padding a los costados, interlineado ajustado en títulos, más espacio arriba de los títulos, gap = alto del texto chico, números alineados a la derecha, alineación por línea base, sentence case, botones que dicen la acción.
- **Movimiento:** pulso para confirmar, crossfade de íconos con blur, efecto rubber band en los bordes, revelar con máscaras, poner el foco en escena.

`skills/ui-ux/references/review-modes.md`: lo mejor de [Impeccable](https://github.com/pbakaus/impeccable) (Apache-2.0) que la base no cubría:

- **Modos de pantalla:** Persuade / Operate / Read / Experience, para decidir cuánto arriesgar.
- **Comandos de trabajo:** `critique` (carga cognitiva + 10 heurísticas de Nielsen con puntaje 0–4 + severidad P0–P3), `polish`, `harden` (casos extremos, i18n, errores), `clarify` (textos de UX), `bolder` / `quieter` / `distill`.
- **Piso anti look genérico:** patrones que delatan una UI hecha con plantilla o IA, y personalizar las superficies del navegador (selección, scrollbar, caret, foco).

El `SKILL.md` referencia ambos archivos para que se lea siempre al construir una pantalla y se corra su checklist antes de entregar.

## Instalar

Global (todos los proyectos):

```powershell
git clone https://github.com/santinohicke/ui-ux-skill "$env:TEMP\ui-ux-skill"; Copy-Item -Recurse "$env:TEMP\ui-ux-skill\skills\ui-ux" "$HOME\.claude\skills\ui-ux"
```

Por proyecto: copiá `skills/ui-ux` a `.claude/skills/ui-ux` del repo.

El buscador necesita Python 3 (sin dependencias): `python scripts/search.py "<consulta>" --domain ux`.

## Licencia

MIT. Copyright original de Next Level Builder (ver `LICENSE`). `review-modes.md` adapta contenido de Impeccable bajo Apache-2.0 (ver `THIRD_PARTY_NOTICES.md`).
