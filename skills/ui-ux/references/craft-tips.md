# Craft Tips — visual polish and micro-interactions

Load this file when building or polishing any screen (web or app), and as a final pass before delivery. These rules fill gaps in `quick-reference.md`: they are the small details that separate "fine" from "professional". Rules already covered elsewhere (destructive actions apart from Save, labels above fields, regular body weight, desaturated dark mode, CTA in empty states, shared-element expand, Fitts, Hick, response time) are not repeated here.

## Visual polish

| ID | Rule | Do | Don't |
|----|------|----|-------|
| `layered-shadows` | Build elevation from two stacked shadows: a tight contact shadow plus a large soft ambient one. | `box-shadow: 0 1px 2px rgb(15 23 42 / .06), 0 12px 24px rgb(15 23 42 / .08);` | One big blurry `0 4px 20px rgba(0,0,0,.25)` shadow. |
| `left-align-paragraphs` | Multi-line text is left-aligned (start-aligned in RTL). Center only short headings or 1–2 line blurbs. | `text-align: start` for any paragraph over two lines. | Centered paragraphs: every line starts in a new place and the eye loses its way. |
| `tinted-grays` | Give neutrals a slight hue (usually cool/blue, or the brand hue) instead of pure gray. | `hsl(220 15% 45%)`, Tailwind `slate`/`zinc` over `neutral`. | `#888`, `#ccc`, pure `hsl(0 0% x%)` everywhere: it looks dead next to color. |
| `tinted-text-on-color` | On a colored surface, text is a dark (or light) shade of that same hue, not black, white-gray or generic gray. | Green banner → text `hsl(145 60% 20%)`. | `color: #000` or `#666` on a green/blue/red surface. |
| `one-hue-per-color` | Each color in the system is one hue; its scale (50–900) only varies saturation and lightness. Related series (chart stacks, states) use shades of one hue. | `--blue-300: hsl(220 85% 56%)`, `--blue-700: hsl(220 85% 30%)`. | A "blue" scale that drifts to purple or teal; three unrelated hues for three parts of one stack. |
| `button-text-size` | Button label font size is about half the button height, and never tiny. | 40px button → 15–16px label; 48px → 16–18px. | 12px text in a 40px button: looks timid and is hard to read. |
| `wider-side-padding` | Pills, buttons, toasts and chips get roughly 2× more horizontal padding than vertical. | `.toast { padding: 12px 24px }`, `.btn { padding: 10px 20px }`. | Equal padding on all sides (`padding: 12px`) on text containers: looks cramped. |
| `tight-headline-leading` | Large headings use tight line-height; body keeps 1.5–1.75. | Display 1.0–1.1, H1/H2 1.1–1.25, plus slightly negative tracking for very large sizes. | Inheriting `line-height: 1.6` on a 48px headline: lines float apart. |
| `space-above-headings` | A heading sits closer to the content it introduces than to the content before it. | `h2 { margin-top: 48px; margin-bottom: 12px }` (≈ 3–4× above vs below). | Equal margins above and below: the heading floats and grouping is lost (proximity). |
| `gap-equals-small-text` | Gap between a big value and its small label ≈ the label's own text height. | 14px label under a big number → ~12–14px gap. | Label glued to the number, or drifting far away. |
| `right-align-numbers` | Numeric columns (prices, amounts, counts) are right-aligned and use tabular figures. | `text-align: right; font-variant-numeric: tabular-nums;` | Left-aligned or centered numbers: digits don't line up and comparison is hard. |
| `align-baseline` | When text of different sizes sits on one line (price + unit, title + meta, value + label), align on the text baseline. | `display: flex; align-items: baseline;` | `align-items: center` on mixed sizes: small text floats up. |
| `sentence-case-labels` | Labels, buttons, menu items and headings use sentence case. | "Create new project", "Payment method". | Title Case On Every Word, or ALL CAPS labels everywhere. |
| `buttons-say-the-action` | A button names the exact outcome with a verb (+ object). Keep the same verb through the flow ("Publish" → toast "Published"). | "Save changes", "Send invoice", "Start free trial". | "Submit", "OK", "Yes", "Continue" when something specific happens. |

## Micro-interactions

Respect `prefers-reduced-motion` for all of these (fall back to an instant state change or a plain opacity fade). Animate only `transform`, `opacity` and `filter`.

| ID | Rule | Recipe |
|----|------|--------|
| `pulse-to-confirm` | Confirm an action on the element itself with a short pulse instead of (or before) a toast. | Scale 1 → 1.06 → 1 in ~250–300ms with a soft color/ring flash; swap icon to a check. |
| `crossfade-icons-blur` | When an icon changes state (copy → copied, play → pause, menu → close), crossfade with scale + blur instead of a hard swap. | Outgoing: opacity 1→0, scale 1→0.6, blur 0→4px. Incoming: reverse. ~150–200ms, both icons stacked in the same box. |
| `rubber-band-edges` | Scrolling or dragging past a boundary resists and springs back instead of stopping dead. | Displacement = drag × ~0.3 (diminishing), then spring back on release. Use native overscroll where it exists; never disable it on iOS. |
| `reveal-with-masks` | Reveal content (text lines, images, panels) by animating a mask/clip instead of just fading. | `clip-path: inset(0 0 100% 0)` → `inset(0)` or a `mask-image` gradient sweep, ~300–500ms, ease-out. Reserve for hero or key moments. |
| `stage-the-focus` | When one element needs attention (new item, modal, onboarding step), dim or blur the rest so the eye goes there, and sequence entrances so the most important thing arrives first. | Backdrop `opacity .4` / `backdrop-filter: blur(4px)`; primary element first, secondary 50–80ms later. |

## Quick checklist

- [ ] Shadows are layered (contact + ambient), not one heavy blur
- [ ] No centered paragraphs; numbers right-aligned with tabular figures
- [ ] Grays are tinted; text on colored surfaces uses that surface's hue
- [ ] Each color scale keeps one hue
- [ ] Button text ≈ half button height; horizontal padding ≈ 2× vertical
- [ ] Headlines have tight leading; more space above headings than below
- [ ] Mixed-size text aligned on baseline
- [ ] Sentence case; buttons say the action with a verb
- [ ] State changes confirmed on the element (pulse / icon crossfade), with reduced-motion fallback

## Sources

Tips curated from two short-form design videos (Ryan Naghibzadeh, "20 design tips your app needs", and theecommguy, "10 design tips for better UI/UX", November 2026), rewritten as rules.
