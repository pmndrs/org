# Rendering Tools

**Status: Proposal**<br>
**Lead dev: Dennis Smolek**

## Motivations

WebGPU has closed much of the gap between what the browser and native engines can do on the GPU. Compute shaders, storage buffers, and modern pipelines are now possible on the web. Many techniques native engines take for granted have not followed: global illumination, ray-tracing, denoising, upscaling, and runtime texture compression for example. On the web these are missing, or they exist as one-off demos tied to a single app.

Pushing that edge needs strong foundations. Adding global illumination meant building a path-tracer, which in turn needed a BVH, a denoiser, and more. Reflections and shadows utilize them too, and each library improves as the others depend on it. When every project builds its own copy of these pieces instead, each copy stays half-finished and never gets the testing that would make it trustworthy. Teams that need these features today, such as product configurators, visualization, and games, end up re-solving the same hard problems, and the results rarely get maintained or shared.

Poimandres can be the home of the bleeding edge of what is possible on the web, built on foundations people can trust. That means an ecosystem of maintained, composable libraries rather than demos: use the whole stack, or take only the piece you need, and help make it better.

Most web 3D users are on three.js, so that is where we start. But tying a rendering technique to one engine limits who can use it and how long it lives. Each library should keep its core independent of any one renderer, as the denoiser and upscaler already does with their core + engine package split.

## Goals

A family of native-level rendering tools, maintained under pmndrs, that support each other and that people can trust, whether they use the whole stack or a single piece.

- Each library in scope ships a stable release with docs and at least one example.
- Each library is usable on its own. Libraries depend on each other only through published packages and public APIs.
- The libraries compose: a reference example uses the full stack (BVH, ray tracer, path tracer and GI, denoiser, upscaler) and shows how to swap or drop each piece.
- Each library has a renderer-agnostic core with a thin engine integration, starting with three.js (WebGPURenderer).
- The libraries share conventions: package structure (core + engine), naming, units and coordinate conventions, image interchange formats, examples, and benchmarks.
- Results are checkable. Correctness is tested against a reference where one exists (native renderers such as pbrt and Mitsuba, native OIDN), and benchmarks are reproducible and name the device and browser they ran on.
- New rendering tools have an obvious place to land in pmndrs, and a documented way to join.

## Scope

The initiative covers the GPU rendering building blocks that sit beneath an application's scene: the foundations other tools build on, and the techniques built on those foundations. It does not cover world content or a full renderer.

Included:

Foundations

- **BVH** (`@pmndrs/bvh`). Bounding volume hierarchies for the GPU: build and traversal. Every ray-traced tool here builds on it.
- **Downsampler** (`@pmndrs/downsampler`). Mip chains and reductions on the GPU, such as texture mips and average luminance.
- **Ray tracer** (`@pmndrs/raytracer`). Trace core: closest-hit, any-hit, and interval queries against the BVH from your own WGSL, with surface, material, and light data. The shared ray provider for path tracing, GI, reflections, and shadows.
-  **Upscaler.** `@pmndrs/upscaler` Vendor agnostic world class frame upscaler built upon FSR3. 

Techniques

- **Path tracer** (`@pmndrs/pathtracer`). Physically based path tracing with OpenPBR materials, from converged reference images to real time. It is also the ground truth the real-time techniques are measured against.
- **Global illumination** (`@pmndrs/gi`). Real-time GI, DDGI first, with world-space radiance caches.
- **Reflections.** `@pmndrs/reflections ` Ray-traced reflections on the ray tracer core.
- **Denoiser.** `denoiser`OIDN-based, split into core + engine packages. Track OIDN 3 once it is released.
- **VSM.**  `@pmndrs/vsm` Virtual shadow maps: high-resolution shadows across large scenes, allocating shadow map pages only where they are needed.
- **GPUTex.** `@pmndrs/GPUTex`Runtime texture compression on the GPU, in the vein of spark.js: encode textures into GPU-compressed formats at load time instead of shipping pre-baked files.
- **VDB** `@pmndrs/vdb` Runtime handling and rendering of volumetric data on the CPU and GPU. Build, edit, and render VDBs in realtime. 
- **Probe-based lighting,** such as reflection probes, sharing probe layouts with GI where that fits.

And more

- **Other core rendering tools.** Small building blocks come up as the work goes on, for example blue-noise textures or GPU image metrics. A new tool joins by a pull request that adds it to this list.
- Shared conventions and a three.js integration layer for each library.
- Documentation, examples, and benchmarks for each library and for the stack used together.

Excluded:

- **Environment and world tools** (sky, clouds, terrain, foliage, impostors, world management). These are covered by the [Environment Tools](./07-environment-tools.md) initiative, and may depend on the tools here.
- A full renderer or engine. The tools can be assembled into one, but this initiative ships the parts.

## Resources

The bottleneck is less dev time than review, testing, and documentation.

- Contributors per library: open
- Reviewers with graphics/GPU background
- Testing across GPU vendors, browsers, and mobile
- Reference renders and test scenes shared across the libraries
- Docs, demos, and benchmarks

## Open questions

- Where should framework bindings (for example, R3F components) live: in each library, in drei, or in a separate package?
- How do the libraries version against each other: independent releases with a tested-together set, or coordinated releases? (Now each its own)
- What does a new tool need before it joins: a stable release, a reference test, a second consumer?
- Where do the shared conventions live: a document in this repo, or a small shared package?
