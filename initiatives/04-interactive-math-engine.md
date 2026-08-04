# Interactive Math Engine

**Status: Active**

## Motivation

Math is core to everything interactive from geometry to collision to color, yet JavaScript lacks a high-performance kernel. Instead libraries reinvent math structures and transformations, with varying success, and now LLMs generate bespoke functions on a case by case basis. The problem is that there are no principled guarantees for correctness or performance leading to degraded apps or difficult to read code.

A modern interactive math kernel needs to excel in real-time environments meaning it is lean, performant and portable. Readability of code is also a premium. With a common convention both agents and people can be more consistent writing the math that powers inspiring apps on the web.

## Goal

- Predictable performance. Allocation-free operations and a documented usage contract designed to preserve monomorphic, optimizable call sites, validated through reproducible benchmarks.
- Portable. Efficiently interoperates with WebGL, WebGPU, Wasm, Three.js, etc., so that the handoff between math kernel and framework is simple.
- Minimal. A lean, tree-shakable kernel containing only the primitives needed to build interactive algorithms.
- Data-oriented. Operates on caller-owned data through data-in, data-out functions without owning the data lifecycle.
- Readable. It is important the core math operations readable such that even if the code is not written by a person they can reasonably review it.
- Foundations for an interactive math ecosystem.

## Scope

Included:

- Core: Vectors, rotations, matrices and related manifolds.
- Computational geometry: bounding boxes, geometry, etc.
- Noise: simplex, perlin, etc.
- Color
- Random
- Timing: Easing functions, bezier, spring, etc.
- Visualizations for math parameters and examples.

Excluded:

- Anything that cannot be made general enough like integration.
- Math or computational structures that are not specifically about spatial, 2D/3D, or real-time app problems.
- Computational structures for traversing space like spatial hash maps, BVH, etc.
- Data management for math structures.

## Resources

- Lead: Isaac Mason
- Outreach with examples
- A nice playground for the math visualizations
- Previous art:
    - [https://github.com/isaac-mason/mathcat](https://github.com/isaac-mason/mathcat)
    - [https://github.com/toji/gl-matrix](https://github.com/toji/gl-matrix)
    - https://github.com/toji/gl-matrixhttps://github.com/greggman/wgpu-matrix