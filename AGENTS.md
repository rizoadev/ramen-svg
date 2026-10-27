# AGENTS.md — ramen-svg

## Project

This repo holds hand-drawn, flat-style stock illustrations as lightweight,
editable SVG files. It is not a traced-image collection.

## How the artwork is made

- Write SVG by hand as XML text. Do not use desktop automation, browser
  automation, or an image-tracing tool (Potrace, Inkscape Trace Bitmap,
  Illustrator Image Trace, VTracer) unless the user explicitly asks for an
  auto-trace. Those tools produce many nodes and rougher lines.
- Keep the drawing stylised and simplified: drop tiny details, round the
  shapes, and use flat colours with a small number of gradients for shading.
- Use a `1000 x 1000` viewBox for new illustrations, unless a poster layout
  needs a different canvas.

## SVG techniques to reuse

- Smooth curves with `<path>` Bezier commands: `C` (cubic), `Q`
  (quadratic), and `T` to continue a curve smoothly.
- Basic shapes for the rest: `<ellipse>`, `<circle>`, and `<rect rx>` for
  rounded rectangles.
- `stroke-linecap="round"` so noodle and chopstick ends look soft.
- `<clipPath>` to cut bowl contents to the bowl's ellipse, instead of
  drawing every edge precisely.
- `<pattern>` for repeating backgrounds (for example the seigaiha waves in
  `ramen-poster.svg`): draw the tile once and let it repeat.
- `<linearGradient>` / `<radialGradient>` for bowl, broth, and egg-yolk
  shading, instead of stacking many colour layers.
- Group shared styles with `<g>` so one fill/stroke serves many paths.

## Style rules

- Keep files small and node counts low. Prefer one wavy path over many
  short line segments.
- Keep the background transparent for standalone illustrations. The poster
  is the exception: it has a cream seigaiha background by design.
- Dark outlines are `#16233A` in `ramen-bowl.svg` and `#101828` in
  `ramen-poster.svg`. Keep outlines consistent inside a single file.
- To change a colour, edit the gradient stops or the `fill` / `stroke`
  values. Do not redraw the shapes.

## Adding or editing a file

1. Copy the structure of the closest existing file.
2. Edit the SVG text directly.
3. Check that the file is still valid, UTF-8 XML and opens cleanly in a
   browser at large sizes without pixelation.
4. Update `README.md` if a file is added, renamed, or removed.
