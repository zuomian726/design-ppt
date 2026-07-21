# Production and QA

## Choose the production path

### Native editable PPTX

Use the agent's presentation tool or a PowerPoint library when collaborators need to edit copy, charts, or layout. Keep text, shapes, charts, and images as native objects where practical. Expect minor differences across PowerPoint, Keynote, and web viewers.

### Image-backed PPTX

Use only when exact visual fidelity matters more than editability. Render each slide at high resolution and place it full-bleed on a correctly sized slide. Tell the user that slide contents are flattened.

### HTML deck

Use when no native PPTX path exists or the user wants browser delivery. Keep the deck self-contained when possible. Use fixed 16:9 slide canvases and print rules that emit one page per slide. Do not present HTML as an editable PPTX.

## Native authoring checks

- Set slide size explicitly, normally 16:9 widescreen.
- Use theme-level fonts and colors when the library supports them.
- Keep elements inside safe margins.
- Avoid unsupported effects that disappear during export.
- Check font availability; embed fonts only when licensing and tooling permit.
- Use vector shapes and native charts for editability, but verify their rendered appearance.

## HTML authoring checks

- Give every slide a fixed logical canvas such as 1280×720 or 1920×1080.
- Scale the whole canvas for browser viewing instead of making the slide responsively reflow.
- Include `@page { size: 13.333in 7.5in; margin: 0; }` and print one slide per page.
- Avoid network-dependent fonts and images in a supposedly self-contained deliverable.
- Wait for fonts and images before capture.
- Use real chart data and deterministic dimensions.

## Visual QA loop

1. Render every slide.
2. Create a montage/contact sheet when possible to evaluate rhythm and consistency.
3. Inspect dense slides at full size.
4. Fix problems in the source, never in a screenshot of the source.
5. Render again and compare.

## Per-slide checklist

- Title expresses a conclusion.
- Focal point is obvious.
- Body copy is readable at presentation distance.
- No text or image is clipped, stretched, or off-canvas.
- Alignment follows the deck grid.
- Contrast is sufficient.
- Data encoding matches the values.
- Sources and units are present where needed.
- Page number, footer, and logo are consistent if used.
- The slide remains understandable without animation.

## Full-deck checklist

- Opening establishes stakes and direction quickly.
- Narrative has no duplicate or missing step.
- Layout rhythm varies without losing design-system consistency.
- Colors, fonts, radii, dividers, and source styles remain consistent.
- Image quality and treatment are coherent.
- Appendix material does not interrupt the main story.
- Final slide resolves the deck with an action, decision, synthesis, or memorable close.

## Delivery checks

- Open the final file, not merely the source project.
- Confirm slide count and order.
- Confirm export dimensions and orientation.
- Confirm external links and media behavior.
- State whether the PPTX is editable or flattened.
- Include required fonts or give safe substitution guidance.
- Remove temporary images, debug files, and test exports from the delivery folder.
