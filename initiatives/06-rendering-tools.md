# Rendering Tools

**Status: Proposal**<br>
**Lead dev: Dennis Smolek**

## Motivations

WebGPU has closed much of the gap between what the browser and native engines can do on the GPU. Compute shaders, storage buffers, and modern pipelines are now possible on the web. Many techniques native engines take for granted have not followed: ML denoising, upscaling, virtual shadow maps, reflection probes, and runtime texture compression for example. On the web these are missing, or they exist as one-off demos tied to a single app.

Teams that need these features today, such as product configurators, visualization, and games, end up reimplementing them for each project. Each team re-solves the same hard problems, and the results rarely get maintained or shared.

Poimandres can be the home of the bleeding edge of what is possible on the web. That means turning these techniques into maintained, composable libraries rather than demos. Several already exist and are in active use.

Most web 3D users are on three.js, so that is where we start. But tying a rendering technique to one engine limits who can use it and how long it lives. Each library should keep its core independent of any one renderer, as the denoiser already does with its core + engine package split.

## Goals

A successful completion of this initiative will give the web a set of native-level rendering tools that are maintained under pmndrs, and that work with three.js today and are not locked to it.

- Each library in scope ships a stable release with docs and at least one example.
- Each library has a renderer-agnostic core with a thin engine integration, starting with three.js (WebGPURenderer).
- The libraries share conventions: package structure (core + engine), naming, examples, and benchmarks.
- Demos and benchmarks show quality and performance clearly, compared against native reference implementations where one exists.
- New rendering techniques have an obvious place to land in pmndrs.

## Scope

The initiative covers standalone GPU rendering features and tools that sit beneath an application's scene, not world content or a full renderer.

Included:

- **Denoiser.** OIDN-based, split into core + engine packages. Track OIDN 3 once it is released.
- **Upscaler.** Made vendor-agnostic in the same way as the denoiser.
- **VSM.** Virtual shadow maps: high-resolution shadows across large scenes, allocating shadow map pages only where they are needed.
- **GPUTex.** Runtime texture compression on the GPU, in the vein of spark.js: encode textures into GPU-compressed formats at load time instead of shipping pre-baked files.
- **Probe based elements such as Reflection probes.**
- Shared conventions and a three.js integration layer for each library.
- Documentation, examples, and benchmarks for each library.

Excluded:

- **Global illumination.** GI belongs with this work but is further out. It will likely become its own initiative that builds on these tools.
- **Environment and world tools** (sky, clouds, terrain, foliage, impostors, world management). These are covered by the [Environment Tools](./07-environment-tools.md) initiative.
- A full renderer or engine.

## Resources

The bottleneck is less dev time than review, testing, and documentation.

- Contributors per library: open
- Reviewers with graphics/GPU background
- Testing across GPU vendors, browsers, and mobile
- Docs, demos, and benchmarks

## Open questions

- Which second renderer, if any, do we target to prove the renderer-agnostic cores?
- Where should framework bindings (for example, R3F components) live: in each library, in drei, or in a separate package?
