# Environment Tools

**Status: Proposal**<br>
**Lead dev: Dennis Smolek**

## Motivations

Outdoor and large-scale scenes need a sky, atmosphere, clouds, terrain, and vegetation. These are some of the weakest areas of web 3D. Each one is a hard problem on its own, and they also have to work together. The sky drives the lighting that clouds, terrain, and foliage all respond to, and they all compete for the same frame budget.

Today developers either stitch together pieces that were never designed to fit, or they skip outdoor environments entirely. Native engines ship these systems as a matched set.

Poimandres already has pieces of this: pmndrs/sky is released and pmndrs/clouds exists. Terrain and foliage systems are in progress, along with an octahedral impostor library for distant objects. This initiative brings them together under shared conventions and allows for a world manager that composes them, so a developer can go from an empty scene to a believable world.

## Goals

The work is in two phases.

**Phase 1 (current).** A successful completion of this phase will give developers a complete, composable set of standalone environment tools. All of them are in progress now.

- Sky, clouds, terrain, foliage, and impostors each ship stable releases, usable on their own.
- The tools share inputs and conventions, such as sun position, lighting, and scale, so they work together without glue code.
- Each library has a renderer-agnostic core where practical, starting with three.js.
- Docs and examples cover each tool on its own and the tools used together.

**Phase 2 (down the road).** Tombo (World Engine) composes the tools into a single world setup, with a reference example. Phase 2 may become its own follow-up initiative once Phase 1 lands.

## Scope

The initiative covers the systems that make up an outdoor environment, and the world manager that combines them.

Included:

- **pmndrs/sky.** Sky and atmosphere.
- **pmndrs/clouds.** Clouds.
- **Terrain system.** In development.
- **sushi-grass.** Foliage system.
- **Impostors.** Octahedral impostor library: renders distant objects as baked views captured from many angles, so large scenes stay within budget.
- **Tombo (Phase 2).** World manager that uses all of the above.
- Shared conventions across the tools, and docs, examples, and benchmarks.

Excluded:

- **Core rendering techniques** (denoising, upscaling, shadows, reflection probes, GI). These are covered by the [Rendering Tools](./06-rendering-tools.md) initiative. Environment tools may depend on them.
- Physics and collision.
- Editors and authoring tools.
- Asset libraries (models, textures).

## Resources

- Contributors per library: open
- Reviewers with graphics/GPU background
- Testing across devices, especially mobile, since environments are frame-budget heavy
- Docs, demos, and showcase scenes

## Open questions

- Which shared conventions (time of day, units, lighting inputs) need to be agreed on before terrain and foliage ship?
- Where do framework bindings (for example, R3F components) live?
