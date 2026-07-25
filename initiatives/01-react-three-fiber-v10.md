# React Three Fiber v10

**Status: Active**

## Motivations

R3F has remained stable for years, but two major changes have happened since v9 was released.

1. WebGPU was released and along with it the new WebGPURenderer and TSL for Three. 
2. AI agents have been widely adopted for coding.

This has changed the landscape of the 3D web drastically. R3F v9 remains lean enough to accommodate a basic WebGPURenderer workflow but the limits of this are clear. In addition R3F and its ecosystem, including Drei, was built as first movers making decisions that aren’t as ergonomic in the contemporary dev world. We now have the benefit of seeing common user patterns.

R3F v10 is an opportunity to make breaking changes to an otherwise stable API and ecosystem all at once so we can be once again on the cutting edge of web 3D.

## Goals

A successful completion of this initiative will modernize R3F and its ecosystem.

- Ergonomically support WebGPU solutions in Three.
- Modernize the DX.
- Modernize the React 3D ecosystem.
- Design internals for real-time performance.

## Scope

R3F and its APIs are core to a lot of pmndrs causing the scope to reach wider than just R3F itself. To successfully launch R3F v10, there needs to be a complete upgrade path for people’s existing R3F v9 apps.

- The R3F monorepo. This includes, core, testing, docs and examples.
- Drei. This is a combination of standard library and experiments of various kinds. A proper upgrade plan needs to include Drei in the least.
- Postprocessing. WebGPURenderer and TSL has moved a lot of postprocessing into its core concepts.
- An AI tool plan. How do agents learn how to use the new API? What integrations do we provide for agentic coding?
- A scheduler. This was previously a small part of R3F but it has become increasingly clear scaling a real-time app requires a robust scheduler.

## Resources

The bottleneck is not dev time but actually everything around it: reviewers, demos, docs, outreach, etc. 

- Lead dev is Dennis.
- Reviewers for alpha, beta, RC.
- Demos to show new features.
- People to write and review docs.
- Outreach for the community and stakeholders.