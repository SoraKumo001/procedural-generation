# Procedural Genesis — WebGPU Infinite Model Forge

An interactive WebGPU demo that continuously generates and renders diverse 3D procedural models in a **single HTML file** with **zero external 3D assets, textures, or libraries**.



**Live Demo:** https://sorakumo001.github.io/procedural-generation/


https://github.com/user-attachments/assets/67c0a3d9-c491-4773-a8d7-31e21059d126

Inspired by the zero-dependency, single-file WebGPU architecture of [Noniv/abyssal-garden](https://github.com/Noniv/abyssal-garden), this project showcases an infinite procedural model forge that generates one unique creation after another.

---

## Features

### 1. 14 Procedural 3D Model Categories
Every model is synthesized in real time from a seeded PRNG (`mulberry32`) and procedural geometry algorithms (lofted surfaces, 3D tube sweeps, logarithmic spirals, recursive branching, and polyhedral subdivisions).

* **Creatures & Marine Life (with WGSL Vertex Animation)**
  * **Abyssal Jelly** (`jellyfish`): Ribbed dome bell, oral arms, and undulating bioluminescent tentacles
  * **Leviathan** (`leviathan`): Swept-wing manta ray with graceful wing-flapping motion
  * **Sea Serpent** (`serpent`): Segmented sea dragon with dorsal crest and S-wave swimming motion
  * **Luminous Moth** (`butterfly`): Sculpted wings with glowing veins, antennae, and wingbeat animation
  * **Abyssal Squid** (`squid`): Streamlined mantle with side fins and 12 flowing tentacles
  * **Nautilus** (`shell`): Logarithmic spiral shell with ribbed ridges and glowing tentacles
  * **Coral / Flora** (`flora`): Recursive 3D branching coral/trees tipped with glowing polyps
* **Minerals, Geometry, Architecture & Sci-Fi**
  * **Crystals** (`crystal`): Faceted crystal spires radiating from a dark rocky base
  * **Starship** (`spaceship`): Symmetrical fuselage, swept wings, and glowing engine thrusters
  * **Toroid Relic** (`relic`): Parametric $(p, q)$ torus knot with a floating energy core
  * **Citadel** (`architecture`): Multi-tiered spire with buttresses and glowing rings
  * **Orbital Ring** (`station`): Counter-tilted structural rings surrounding a fusion core
  * **Sky Island** (`island`): Floating inverted rocky spire topped with trees, a waterfall, and an obelisk
  * **Fractal** (`fractal`): Recursive 3D cubic lattice with an emissive core

### 2. Real-Time WebGPU PBR & Post-Processing
* **Cook-Torrance GGX PBR**: Physically based lighting with metallic/roughness response and Fresnel rim lighting
* **3D Procedural Bump Mapping**: Real-time 3D FBM noise in WGSL perturbs surface normals and modulates roughness/albedo micro-detail
* **Subsurface Scattering (SSS) Approximation**: Translucent light-wrap shading for organic creatures and flora
* **Smooth & Hard-Surface Normals**: Welded smooth vertex normals for organic forms; crisp faceted normals for crystals, ships, and architecture
* **4x MSAA + HDR Bloom**: Renders into a `rgba16float` MSAA target, extracts bright emissive regions for soft optical bloom, and finishes with ACES Filmic tone mapping and subtle vignetting

---

## Getting Started

### Requirements
* A **WebGPU-enabled browser** (latest Google Chrome or Microsoft Edge)

### Running the Demo
Open [index.html](index.html) directly in your browser, or serve the directory with `npx`:

```bash
npx serve .
```

Then open the local URL shown in the terminal (e.g., `http://localhost:3000`) in your browser.

### Controls
* **Mouse Drag**: Orbit camera
* **Mouse Wheel**: Zoom in / out
* **`Space` / `⚡ Next Model`**: Forge a new model immediately
* **`⏸ Auto` Button**: Toggle automatic generation (every 6 seconds)
* **`🌀 Spin` Button**: Toggle automatic turntable rotation
* **Top Category Pills**: Choose `All Random` or lock generation to a specific archetype
* **`H` Key**: Toggle HUD visibility

---

## Project Structure
* `index.html`: Single-file implementation containing all procedural mesh generators, WebGPU pipelines, WGSL shaders, and UI
* `README.md`: Project documentation
