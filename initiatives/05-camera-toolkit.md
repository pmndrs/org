# Camera Toolkit

**Status: Draft**

## Motivations

Camera is one of the core parts to 3D.
Everyone ends up reinventing the saem abstractions that are slightly different.
There is not a good toolkit to pull from with optimized operations to build our own abstractions.
In the AI world it is more important than ever to have a low level kit, but we also want opinionated abstractions for getting going.
There is also just years of great tech out there from Unity to Unreal that has not made it properly to JS.

## Goals

- Data-oriented toolkit. Low level camera operations that developers can combine to build their own abstractions.
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
