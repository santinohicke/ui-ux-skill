# Review modes — surface modes, work commands, anti-generic floor

Adapted from [Impeccable](https://github.com/pbakaus/impeccable) (Apache-2.0, commit `2fc5e14`). Only what `quick-reference.md`, `pro-rules.md` and `craft-tips.md` don't already cover is kept here.

## 1. Pick the surface mode first

The mode names what success looks like on **this surface** (not the product). Decide it before any visual choice.

| Mode | Visitor's goal | Surfaces | How ambition shows |
|------|----------------|----------|--------------------|
| **Persuade** | Decide and act | Landing, marketing, pricing, campaigns | Bold, distinct, a point of view; real imagery when needed |
| **Operate** | Finish a task | App UI, dashboards, editors, admin, settings | Precision and restraint; scanability, consistency, native patterns win over expression |
| **Read** | Understand something | Docs, articles, help, changelogs | Structure for comprehension, comfortable measure, one reading path |
| **Experience** | Be inside the work | Portfolios, galleries, showcases | The artifact leads from the first viewport; UI recedes |

A tool's landing page is Persuade; its docs are Read. Persuade/Experience may be asymmetric or disruptive; Operate/Read treat predictable structure and stable density as affordances.

**Refinement preserves, redesign replaces.** A refinement keeps the existing identity, copy and behavior. A redesign keeps content and function but treats the old look as anti-reference. Never split the difference by polishing a look you meant to discard. The brief always wins over taste.

## 2. Work commands

When the user asks for one of these (by name or by intent), follow its playbook.

### `critique` — UX review with scores

1. **Cognitive load checklist** (count failures: 0–1 good, 2–3 moderate, 4+ critical): single focus · chunks of ≤4 items · related items grouped · obvious hierarchy · one decision at a time · ≤4 visible options per decision · no need to remember info from a previous screen · progressive disclosure.
2. **Nielsen's 10 heuristics, 0–4 each** (4 = genuinely excellent, not "good enough"): system status · match with real world · user control & freedom · consistency · error prevention · recognition over recall · flexibility & efficiency · aesthetic & minimalist · error recovery · help & docs.
3. **Squint test:** blur the screen; you should still see the primary element, the secondary one and the main groups in order.
4. Report issues by severity: **P0** blocks the task or loses data · **P1** major friction or inaccessible · **P2** noticeable inconsistency · **P3** cosmetic. Each with evidence and a concrete fix.

Common violations to name: wall of options, memory bridge (step 3 needs info from step 1), hidden navigation, jargon barrier, visual noise floor (everything same weight), inconsistent pattern, multi-task demand, context switch.

### `polish` — final pass before shipping

Refinement only; if the concept is wrong, say so and recommend redesign or `bolder`. Triage in this order and don't perfect one corner while the rest is below the bar:

1. Broken/blocked tasks, data loss, misleading state, inaccessible paths
2. Missing loading, empty, error, success, disabled, permission states
3. Flow, hierarchy, responsive and design-system drift
4. Visual and motion inconsistencies
5. Code and asset cleanup (debug output, dead styles, one-off values → tokens only if reused)

Classify each drift before fixing: missing token · one-off that should use a shared component · conceptual mismatch with neighboring flows · local defect. Fix at the narrowest correct level. Finish by walking the whole path with mouse, keyboard and touch at mobile, intermediate and wide sizes.

### `harden` — survive real data

Test and fix with: names of 100+ chars, single char, empty · emoji, accents, RTL, CJK · millions/billions · 1000+ items, 50+ options · offline, slow 3G, timeout · 400/401/403/404/429/500 · double-clicking submit 10 times · second finger mid-drag, pointer released outside, window blur mid-drag · no-permission and read-only.

Key fixes: `min-width: 0` on flex/grid children · `line-clamp` or wrap instead of fixed widths · budget 30–40% extra width for translations · logical properties (`margin-inline-start`, `padding-inline`) · `Intl.NumberFormat` / `Intl.DateTimeFormat` / plural rules instead of string concatenation · one failing component never blanks the whole screen · prevent double submit and roll back optimistic updates on failure.

### `clarify` — UX copy

For each state decide: the one fact the user needs now → the next action → context that changes the decision → tone for the moment. Say each idea once; if the heading explains the state, drop the intro.

- Errors answer **what failed, why (if known), how to recover**. No internal codes as the main message, no blame, no jokes on payment/privacy/deletion.
- Destructive actions name the object and consequence; prefer undo over confirmation when recovery is safe; confirm buttons repeat the verb ("Delete project"), never Yes/OK.
- Loading names the real operation ("Loading your projects…"); never fake progress.
- Empty states distinguish first use, no results, filtered out, no permission, and failure, each with its own next action.

### `bolder` / `quieter` / `distill`

- **bolder** (safe, bland): commit to one memorable element — larger type contrast, a stronger color decision, an authored motion moment, real imagery. Keep everything around it disciplined.
- **quieter** (loud, overstimulating): reduce simultaneous accents to one, lower saturation, remove decorative motion, unify weights and radii, add whitespace.
- **distill** (complex): remove elements until the primary task is obvious; merge duplicate actions; move rare options behind progressive disclosure; cut every line of copy that repeats another.

## 3. Anti-generic floor (refuse unless the brief asks for it)

These are the defaults that make a UI look template- or AI-made. If the brief leaves the axis free, don't spend it here:

- Page built from identical cards of icon + heading + text; **nested cards are always wrong**
- Hero-metric template: big number, small label, supporting stats, gradient accent
- **Eyebrow/kicker label above headings** (ban) and section numbers 01/02/03 when the content isn't a real sequence
- Gradient text; glass/blur as decoration; colored side-bar stripe on a rounded box (use full border, tint or leading icon)
- Hard offset shadows (`4px 4px 0`) outside a genuinely neobrutalist world; 1px border **plus** wide soft shadow (pick one)
- Monospace as a "technical" costume instead of for code/data; emoji or Unicode as icons
- Sketch/doodle SVG illustrations and noise grain; decorative stripes or grid backgrounds with nothing to measure
- A modal for a task that needs neither interruption nor protected focus
- Light vs dark chosen by category instead of by the real use scene (who, where, what light)
- Tracking tighter than -0.04em (−0.02 to −0.03em reads better); card radii outside 12–16px; pills on large containers

**Theme the browser surfaces** — the cheapest sign a page was built rather than assembled: `::selection`, `caret-color`, scrollbars, focus rings, `text-underline-offset`, and tabular numerals, all from the palette.

**Verify by looking**: render at the sizes it ships at and batch all checks in one look (contrast, depth, spacing, type measure 65–75ch, one authored motion moment, every state, real copy at every breakpoint) before looking again.
