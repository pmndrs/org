# Text Rendering

**Status: Active**

## Motivations

React Three Fiber and React Three XR have enabled scalable apps to be entirely rendered with web 3D and pushing the limits of what is possible. However, there still are day to day gaps that require workarounds from the community. Sometimes this is out of necessity, for example with XR apps where there is no HTML option, sometimes this is for the unique performance or visual benefits from controlling the entire rendering pipeline, but in all cases **text rendering becomes a bottleneck**. 

Adequate solutions have existed for WebGL, but so far tthere are no WebGPU solutions that are built for mass distribution. On top of this, text rendering technology has evolved, including Slug going open source. All of this motivates us to create a text rendering solution that other libraries, such as UIKit, can build off of.

## Goals

- Enable the creation of high-quality, text-heavy interfaces entirely within a canvas.
- Provide text that remains legible and visually consistent across desktop, mobile, and XR.
- Give developers a practical path from a font or icon asset to GPU rendering.
- Support different rendering strategies for different quality and performance needs.
- Offer a standard set of paragraph formatting and styling for layout in downstream packages.
- Provide a foundation that higher-level layout and interface systems can integrate with.

## Scope

The initiative covers GPU-based rendering of text, glyphs, and font-like icon assets.

Included:

- WebGL and WebGPU rendering backends.
- Multiple rendering techniques, including MSDF, MTSDF, and Slug-like approaches.
- Font and asset preprocessing and baking tools.
- Runtime glyph rendering and atlas management.
- Font-level properties like kerning and text measuring.
- Paragraph layout, line breaking, wrapping, and text-flow systems.
- Integration points for UIKit and other layout systems.
- Guidance for selecting a rendering strategy for a given use case.

Excluded:

- General-purpose UI layout.
- Accessibility semantics such as ARIA.
- Text editing, selection, cursor behavior, and input methods.
- Rich text rendering with markdown. Lists, quotes, headings, etc.

## Resources

- Lead dev: Justin Walsh
- Reviewers and users with concrete product use cases
- Documentation written.
- Examples and benchmarks.