# Procedural Aquarium — WebGPU Real-Time Aquatic Ecosystem

An interactive WebGPU demo that procedurally generates and simulates a living 3D **glass aquarium ecosystem** in a **single HTML file** with **zero external 3D assets, textures, or libraries**.

**Live Demo:** https://sorakumo001.github.io/procedural-generation/

https://github.com/user-attachments/assets/67c0a3d9-c491-4773-a8d7-31e21059d126

Inspired by the zero-dependency, single-file WebGPU architecture of [Noniv/abyssal-garden](https://github.com/Noniv/abyssal-garden), this project builds a sunlit glass fish tank filled with animated caustics, rippling water, rising air bubbles, river rocks, driftwood, swaying aquatic plants, and swimming marine creatures.

---

## Features

### 1. Realistic 3D Glass Aquarium Environment
* **Glass Tank & Aquascape Hardscape**: Framed glass tank with cabinet plinth, suspended overhead daylight LED bar, contoured quartz sand bed, smooth river stones, sunken driftwood, and an air-stone diffuser.
* **Animated Underwater Optics**: Real-time projected caustics on sand, rocks, plants, and creatures; undulating water surface ripples with Fresnel reflections; and continuously rising air bubbles.
* **3D Aquarium Steering Physics**: Swimming species weave, dive, turn smoothly toward their velocity vector, avoid each other, and stay naturally contained within the glass panes and above the sand bed.

### 2. 10 Procedural Aquatic Creatures & Plants
Every specimen is generated in real time from a seeded PRNG (`mulberry32`) and procedural geometry algorithms (lofted surfaces, tube sweeps, leaf blades, and ellipsoids).

* **Swimming Aquatic Creatures (with WGSL Motion)**
  * **Tropical Fish** (`tropical_fish`): Clownfish, Regal Tang, Butterflyfish, and Cardinal Tetra variants with realistic fins, glossy eyes, and lateral tail-beat swimming
  * **Koi / Goldfish** (`koi`): Marbled *Nishikigoi* patterns, barbels, and flowing veil tails
  * **Sea Turtle** (`turtle`): Scuted carapace, plastron, and sweeping front flipper strokes
  * **Manta Ray** (`manta`): Oceanic manta with cephalic lobes, pale belly, and graceful wing-flapping motion
  * **Jellyfish** (`jellyfish`): Translucent pulsing bell, oral arms, and trailing tentacles
  * **Seahorse** (`seahorse`): S-curved bony-ringed body, tubular snout, and coiled tail
  * **Reef Squid** (`squid`): Streamlined mantle with lateral fins and 10 trailing tentacles
* **Rooted Aquatic Plants & Reef Coral (with Water-Current Sway)**
  * **Ribbon Plant** (`vallisneria`): Clusters of gently curved emerald ribbon blades rooted in the sand bed
  * **Stem Plant** (`stem_plant`): Leaf-whorled *Rotala* and *Ludwigia* stems swaying in the current
  * **Anubias / Coral** (`broadleaf_coral`): Glossy broadleaf rosettes and natural branching reef coral

### 3. Real-Time WebGPU PBR & Post-Processing
* **Cook-Torrance GGX PBR & 3D Procedural Bump**: Physically based shading with real-time 3D FBM surface micro-detail
* **Subsurface Scattering (SSS) Approximation**: Backlit translucency on aquatic leaves, corals, and jellyfish
* **4x MSAA + Tuned HDR Bloom**: Renders into an `rgba16float` 4x MSAA target, blends transparent glass/water/bubbles, and finishes with subtle optical bloom, ACES Filmic tone mapping, and vignetting

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
* **Mouse Drag**: Orbit camera around the aquarium
* **Mouse Wheel**: Zoom in / out
* **`Space` / `🐠 Spawn Now`**: Spawn a new creature or aquatic plant immediately
* **`🌊 Mode: Aquarium` / `🔍 Mode: Inspect`**: Switch between the live glass aquarium and single-species close-up inspection
* **`⏸ Auto` Button**: Toggle automatic spawning (every 3 seconds in Aquarium mode)
* **`🌀 Orbit` Button**: Toggle slow camera orbit
* **`🗑 Reset Tank`**: Reset and repopulate the aquarium
* **Top Category Pills**: Choose `All Random` or filter spawns to a specific species/plant
* **`H` Key**: Toggle HUD visibility

---

## Project Structure
* `index.html`: Single-file implementation containing all procedural generators, aquarium environment meshes, WebGPU pipelines, WGSL shaders, physics, and UI
* `README.md`: Project documentation
