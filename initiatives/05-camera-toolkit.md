# Camera Toolkit

**Status: Draft**

## Motivations

Cameras are a core part of 3D, with years of development and refinement that have largely been out of reach on the web. A low-level, composable toolkit lets developers build their own abstractions without reinventing basic components. Opinionated abstractions make it easy to get started, drawing on familiar camera systems from Unity, Unreal, Godot, and other engines.

Following an onion-layer model lets us support a JavaScript camera ecosystem that takes both foundational tools and opinionated abstractions seriously.

## Goals

- Data-oriented toolkit. Low-level camera operations that developers can combine to build their own abstractions.
- Useful abstractions. Built-in abstractions for common camera patterns, built from the same core.
- Framework independent. A standalone core with integrations such as React Three Fiber for authoring.
- Virtual camera systems. Full virtual camera support such as rigs, blending, tracking, switching, etc.
- Inspectable. Practical tools to compose, preview, and debug camera work.
- Predictable performance. Documented APIs and examples designed for real-time camera systems.

## Scope

The initiative covers the camera systems needed to turn scene state, user input, and authored direction into a final camera view. It spans a low-level core, built-in abstractions, and framework integrations, so developers can use the provided patterns or compose their own.

Included:

- Virtual cameras, rigs, and behaviors.
- Camera director for shot selection and camera management.
- Camera controls such as orbit, first person, etc.
- Shot composition, framing, and lens control.
- Camera transitions, blending, sequencing, and choreography.
- Camera effects like shake.
- Camera debugging and visualization.
- Data-oriented core APIs, built-in abstractions, and framework integrations such as React Three Fiber.

Excluded:

- Physics based collision solvers beyond raycast-based occlusion avoidance.
- General purpose animation and timeline tooling beyond camera sequencing and choreography.
- Implementing postprocessing effects such as depth of field, motion blur, or lens distortion.

## Resources

- Lead: Łukasz Kwas
- Reviewers and users with concrete camera use cases.
- Docs writing and review support.
- Examples and a playground for exploring camera behaviors and visualizing shots.
- Tests and performance benchmarks for camera behavior, transitions, and control handoffs.
- Previous art: Klipp, `camera-controls`.
