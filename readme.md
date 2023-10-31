class: middle, center
# Plasma Engine
## Building a WebGL Engine for an Educational Platform
by Brian Chirls
3D Graphics Engineer, BioDigital

---
class: middle, center
# What is BioDigital?
"The BioDigital Human is an interactive 3D software platform for visualizing anatomy, disease, and treatment."

---

# Product Scope
- 1000+ library modules, plus client content
- Content types
  - Gross anatomy
  - Conditions & Procedures
  - Medical devices
  - Cellular and microscopic
- 6k+ objects, 3mil+ vertices, ~200 textures

---

# How is a platform different?

--
- Range of content, can't customize code

--
- Range of hardware

--
- Range of network conditions

--
- Lots of text (DOM) [accessibility]

---

# Unique content challenges

--
- So many objects

--
- So many vertices

--
- Nothing is repeated (more than once)

--
- Everything is visible

--
- Nothing is far away

---

# Content pipeline
- Authoring in Maya and Substance Painter
- Custom export via Maya plugin
- Compress textures on server
- Authoring in web app
- Load on demand in browser

---

# Starting Point
- Old engine: SceneJS abandoned and forked years ago
- Heavily optimized but inflexible and hard to understand
- Old coding conventions
- Old hardware/software support assumptions

---

# New Engine Goals:
- Improve architecture for upgrades and fixes
- Improve documentation in and outside code
- Match or exceed performance
- Maintain support for old WebGL 1 devices
- WebXR support

---

# Architecture
- Separation of concerns:
  - Anatomy Objects (application object)
  - Scene Graph (renderable objects)
  - Simulation (particles & animation)
  - Renderer
- Event-driven

---

# Why not Three.js?

--
- No semver, breaking changes on every release

--
- Kills features and support too often

--
- Custom particle systems & animation

--
- Would be too much use of low-level hooks like custom shaders

---

# Why not GLTF?

--
- Conditional loading of compressed textures, based on support

--
- Full representation of scene graph w/ application-specific info and references to shared resources

--
- Restrictions on texture maps:
  - cannot stack multiple layers
  - metallic/roughness must be same image, but no support for other texture packing

---
# Why not GLTF?...
- Custom particle systems

--
- Could address with custom extensions, but at that point may as well use our own format

---

exclude: true

# QA strategies

--
exclude: true
- Bugs
  - Unit tests with Jest (~46% coverage, ~1200 tests)
  - Screenshot diffing
  - Manual testing

--
exclude: true
- Performance
  - Frame rate, loading time, 
  - Define specific targets
  - Automated benchmarks with jest
  - Manual profiling with browser tools

---
# zSpace

- Lenticular display: 3D without glasses
- WebXR
- Scaling and placement
- Stylus input
