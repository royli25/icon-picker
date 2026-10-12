---
name: icon-picker
description: Select, source, scale, and implement interface icons for websites, apps, and Figma designs. Use when choosing or adding UI icons, matching their visual weight, or reviewing icon consistency and accessibility. Defaults to Untitled UI free icons unless the user directs otherwise.
---

# Icon picker

Choose icons that clarify content and actions, fit surrounding typography, and remain consistent across the interface.

## User preferences

- Unless the user directs otherwise, always source interface icons from **https://www.untitledui.com/free-icons**. This is the canonical starting point, not merely a stylistic reference.
- **Scale icons; never resize them.** Apply uniform scaling to the whole icon, including its strokes. Do not independently change icon width/height, stretch paths, or resize a vector bounding box while leaving stroke widths unchanged. Containers and hit areas can have their own dimensions.
- Match visual weight to the website's content, typography, density, and hierarchy. Keep a coherent treatment within each component family.
- When making Figma frames as iterations, **only name the frames; never add frame captions**.
- A specific user direction can override the default source or treatment for the requested scope. Do not infer a library override merely because another library is installed.

## Establish the context

Inspect the relevant screen, component, design tokens, and existing icon conventions before selecting assets. Identify the icon's purpose: action, navigation, status, content category, or decoration. Read nearby copy and understand what the control actually does.

Reuse an existing verified Untitled UI asset or component when it fits. Limit edits to the requested feature or review scope; adding an icon does not authorize replacing every icon in a project.

If the request is selection only, deliver recommendations. If implementation is requested, implement and inspect the result. Ask a question only when an unresolved meaning, brand requirement, or source exception materially blocks a correct choice.

## Source real assets

1. Start with the free catalog, search the intended action and synonyms, and inspect candidates in context.
2. Follow the catalog's actual links or copy/download controls to obtain the original SVG or linked Figma library asset. Existing assets are acceptable when their Untitled UI provenance is established.
3. Verify the exact catalog name and free availability. Never invent an icon name, SVG path, package export, download URL, weight variant, or Figma component key.
4. Preserve the source viewBox, path geometry, aspect ratio, line caps, and joins. Prefer vector assets over screenshots or raster substitutes.
5. Keep a source URL and original icon name in existing asset metadata, a code comment, or the relevant handoff. Do not add visible attribution to the interface unless required by applicable terms or requested.

Do not silently substitute Lucide, Heroicons, Material, emoji, Unicode symbols, hand-drawn approximations, or generated imagery for interface icons. If the catalog is unavailable, use a previously verified local Untitled UI asset when appropriate. Otherwise explain the limitation and leave the asset unresolved or use a clear text-only control. A placeholder must not be presented as a completed sourced icon.

If no exact metaphor exists, prefer a simpler accurate icon with a label or a text-only control. Ask about an alternative source only if necessary. Treat branded marks separately: never fabricate a company logo from a generic UI icon. Do not purchase assets or assume access to paid variants. Consult applicable source terms when use or redistribution requires clarification.

## Pick for meaning

- Choose the most recognizable metaphor for the actual action. Distinguish download from share, archive from delete, close from back, and filtering from sorting.
- Reuse the same icon for the same meaning. Avoid assigning the same icon to different meanings in the same context.
- Prefer a simpler silhouette at small scales. If an icon needs an explanation, supply a visible label rather than relying on a tooltip.
- Use arrows for directional actions and chevrons for disclosure where those conventions fit the product. Verify destination and expansion behavior before choosing direction.
- Avoid decorative icons on every heading, bullet, and card. Add one when it improves recognition, scanning, or a deliberate visual hierarchy.
- For localization, mirror only icons whose meaning follows reading direction. Do not indiscriminately mirror logos, numbers, media symbols, or other fixed meanings.

## Match weight and scale

Judge weight beside real text at the final rendered scale, not on an isolated enlarged icon sheet. Stroke thickness, silhouette density, size, and contrast all affect perceived weight. A font's numeric weight does not map directly to an SVG stroke value.

Start with the source's native stroke treatment. Prefer an officially available variant if a different weight is necessary; verify availability rather than assuming the free catalog offers multiple weights. If no suitable variant exists, first reconsider icon complexity, scale, or placement. If a custom stroke adjustment is necessary, treat it as an explicit, consistently applied style decision, document it, and inspect legibility. Do not accidentally change weight through a resize operation or fake weight with shadows, blur, or duplicate offset paths.

Use these as judgment guides, not fixed prescriptions:

| Context | Selection and weight guidance |
| --- | --- |
| Editorial or restrained content | Simple, quiet icons that support the text; avoid strokes too faint to read. |
| Dense tools and dashboards | Compact, distinguishable silhouettes with consistent weight across controls. |
| Bold marketing content | Visually substantial shapes that sit comfortably beside headlines; avoid enlarging utility icons into illustrations by default. |
| Warnings, errors, and success | Familiar status metaphors and explicit text; use semantic color without depending on color alone. |

Use the project's existing size tokens. If none exist, consider 16, 20, and 24 as initial UI scales and validate against the actual type and controls. These are starting points, not mandatory sizes. Derive a uniform scale factor from actual source dimensions; do not assume every SVG has a 24-unit viewBox.

Separate three concerns: source artwork, scaled visual footprint, and control hit area. Optical alignment may use a small translation or spacing adjustment; never deform geometry to make an icon appear centered. Keep outer boxes stable across interaction states to prevent layout shifts.

## Implement in the target environment

Read the relevant sections of [implementation.md](references/implementation.md) for Figma scaling, web transform patterns, accessibility, and inspection guidance. Use available environment tools and their required skills when actually editing; this skill does not require Figma for web work.

- **Figma:** preserve vectors or component instances and use the Scale operation or supported uniform rescale API. Adjust the surrounding layout separately.
- **Web:** retain native SVG dimensions and scale artwork uniformly. Reserve the intended layout footprint with a wrapper. Inherit semantic color where appropriate and reuse the project's icon component conventions.
- **Other environments:** use the platform's uniform vector scaling equivalent and separate artwork from the interactive target.

## Accessibility and states

- Give icon-only controls an accessible name describing the action, not the icon's shape. Hide redundant decorative SVGs from assistive technology.
- Use native buttons and links for actions and navigation. Preserve keyboard access and visible focus treatment.
- Keep click/touch targets comfortable independently of artwork size. Do not enlarge the SVG merely to enlarge the hit area.
- Check hover, focus, active/selected, disabled, and loading states that the component actually supports. A selection must remain understandable without color alone.
- Check sufficient contrast in applicable themes. Do not use low opacity as a universal shortcut for secondary icons.
- Respect reduced-motion preferences when icon animation is part of the requested interaction. Do not add animation merely because an icon supports it.

## Verify and hand off

Inspect the result at actual scale, beside adjacent text and related icons, including relevant narrow layouts and themes. Check that strokes scale with paths, there is no clipping or distortion, alignment feels balanced, and controls remain accessible. Use relevant project checks for implementation changes; do not claim visual verification from source inspection alone.

For an icon selection request, give the recommended verified icon, source link, intended meaning, and a short rationale. For a larger set, use a compact mapping of UI purpose to icon, scale, and treatment. Offer alternatives only when they represent a useful choice. For implementation, summarize what changed and any unresolved asset or verification limitation; keep provenance and implementation notes out of user-facing product copy.
