# Implementation guidance

## Figma: scale the artwork, lay out the container

- Inspect the source component or vector's actual dimensions and stroke treatment.
- Use Figma's Scale operation (K in the editor) or the available API's documented uniform rescale operation. For a square source with side B and intended side T, use scale factor T / B. For a non-square source, fit proportionally within the intended slot with a single factor for both axes.
- Scale the icon itself, not the whole button or its label. Confirm strokes, corners, and any icon effects scale with it.
- Preserve component instances and shared tokens where possible. Avoid detaching just to change the displayed scale.
- Set the parent frame's layout size and padding separately. Check clipping and optical centering after scaling.
- Do not use bounding-box resize as a shortcut for scaling. If available automation cannot preserve stroke-and-geometry scaling, report the limitation instead of silently approximating it.
- Keep iteration descriptions in frame names. Never create canvas captions for iteration frames.

## Web: an explicit scale pattern

When a verified source SVG is natively 24 by 24 and the desired visual slot is 20 by 20, its uniform scale is 20 / 24. Keep the SVG at its native dimensions and scale it inside a slot. Do not copy this native size assumption to a differently sized asset.

```css
.icon-slot {
  /* Layout footprint, distinct from the source artwork dimensions. */
  position: relative;
  display: inline-block;
  inline-size: 20px;
  block-size: 20px;
  flex: none;
}

.icon-slot > svg {
  /* Original verified SVG dimensions, not the target scale. */
  width: 24px;
  height: 24px;
  position: absolute;
  top: 0;
  left: 0;
  display: block;
  transform-origin: top left;
  transform: scale(0.8333333333);
}
```

Use the real source SVG inside the wrapper. This example intentionally supplies no fabricated icon paths. For other scales, derive the factor and wrapper footprint from the source. Keep scale values centralized in the existing component or design tokens instead of scattering one-off values.

Transforms do not reserve a new layout footprint, which is why the wrapper matters. A non-square source may need centering inside the slot. Test for inherited global SVG sizing rules, shrink behavior, overflow clipping, and transform overrides. If a framework's size prop changes artwork width and height, use the native size and wrap it with a uniform scale instead.

Avoid `vector-effect="non-scaling-stroke"`: it prevents the stroke from scaling with the geometry. Check imported assets for this behavior. Do not alter the viewBox to crop or enlarge a symbol artificially. Retain native path, cap, join, and fill semantics; when making color themeable, replace only intended monochrome paint values with `currentColor` and preserve `fill="none"` where present.

Prefer a reusable local SVG component or an existing verified Untitled UI integration. Verify real package exports before using them. Avoid adding a full library for one icon or hotlinking an external asset at runtime when the project's local asset conventions can be followed. Preserve any required license information.

## Accessible controls

For an icon-only action, give the surrounding native button a meaningful accessible name (for example, `aria-label="Download report"`) and give the decorative SVG `aria-hidden="true"` and `focusable="false"`. For a labeled button, visible text normally supplies the name; hide the redundant icon. Do not announce the same label twice.

For a standalone informative SVG, supply an accessible name using the platform's supported mechanism, such as `role="img"` with a unique title reference. Prefer visible text for important status information. A tooltip is supplementary and should work for keyboard users when implemented.

Use padding on the button to create a comfortable target. When no established target guidance exists, aim for roughly 44 by 44 CSS pixels for touch controls where practical; this is a usability starting point, not a claim of standards compliance. Dense desktop layouts still need adequate spacing and keyboard access.

Check whether a control represents an action or state. A toggle may need `aria-pressed`; disclosure may need `aria-expanded`. Use these only when they match the actual interaction. Loading treatment should preserve the control's footprint and a meaningful accessible status.

## Focused inspection

Check the affected component in context rather than generating a new icon gallery for every small change:

- Correct action/metaphor and verified source asset.
- Uniform geometry and stroke scaling at the final visual scale.
- Balanced weight beside the actual type and neighboring controls.
- Optical centering, consistent spacing, and no clipping.
- Stable footprint across relevant states and responsive layouts.
- Readable relevant light/dark treatments and non-color status cues.
- Meaningful accessible names, keyboard behavior, and comfortable targets.

When selection involves a whole system, maintain its existing icon mapping or add a small mapping where useful: UI purpose, verified source name/URL, implementation identifier, native dimensions, intended scale, and any deliberate weight adjustment. Avoid introducing a new registry for a single isolated icon.
