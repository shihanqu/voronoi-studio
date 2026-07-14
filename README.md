# Voronoi Studio

A single-file, browser-based **Voronoi organoid generator** for 3D printing.
Pick a shape (or drop in any watertight STL), and it wraps the surface in an
organic Voronoi web — bulging struts, rounded holes, a printable shell — then
exports a watertight binary STL.

![Voronoi Studio](https://img.shields.io/badge/single%20file-HTML%2FJS-blue)

## Run it

Open `voronoi-studio.html` in any modern browser. That's it — no build step,
no server. (three.js is loaded from a CDN, so the first load needs internet.)

## Features

- **Input shapes**: sphere, cube, to-scale soda can, 3DBenchy, or **any imported
  STL** (drag & drop onto the viewport).
- **Voxel engine**: samples a 3D distance field around the input (marching
  tetrahedra), so it is robust on thin walls, fine detail, and messy meshes.
- **Organic pattern controls**: cell size, strut thickness, shell thickness,
  organic bulge, hole rounding, cell-size variance, random seed.
- **Solid-surface painting**: mark regions of the input surface (smart select
  for whole flat/spherical/cylindrical surfaces, or a sphere brush for
  free-form patches) that stay a solid thin shell — no holes there.
- **Print helpers**: overhang bias (stretches cells vertically so struts run
  steeper relative to the build plate), containment mode (shell inset so
  nothing pokes outside the input bounds), automatic floating-debris removal.
- **Quality/verify**: voxel size presets, Taubin smoothing, watertightness and
  piece-count checks on every generation.
- **Save/load settings** as JSON (including painted selections), and **export
  binary STL** ready to slice.

## Notes

- Units are millimetres throughout.
- The 3DBenchy preset needs `3DBenchy.stl` next to the HTML file (or it will
  ask you to pick it). Get it from [3dbenchy.com](https://www.3dbenchy.com/) —
  it is not bundled here for licensing reasons.
- Everything runs client-side; large models at fine voxel sizes are CPU- and
  RAM-hungry.

## Provenance

Voronoi Studio is the simplified, voxel-only distillation of a larger
dual-engine experiment (Organic Shell Studio). This version intentionally
omits the parametric mesh engine, shape modifiers, and slice/pierce
post-processing in favor of one robust pipeline.
