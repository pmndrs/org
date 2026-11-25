# Registry

**Status: Proposal**<br>
**Lead dev: Alvaro Saburido**

## Motivations

Every declarative framework in this space reimplements its own opinionated abstractions over three.js materials, helpers, and scene extensions. Each reimplementation is a real, ongoing maintenance burden for its authors, and the same job is done four times over. Counts are from each library's documentation:

| Library              | Framework          | Documented count            |
| -------------------- | ------------------ | --------------------------- |
| `@react-three/drei`  | React Three Fiber  | 126, across 12 categories   |
| `@tresjs/cientos`    | TresJS (Vue)       | 101, across 10 categories   |
| `@threlte/extras`    | Threlte (Svelte)   | Roughly 150                 |
| `angular-three-soba` | Angular Three      | 71, across 9 categories     |

These opinionated abstractions (hooks, components, composables) improve the DX, but they fall short outside basic demos. For enterprise-level complexity, users often replace them with a custom implementation. With the rise of AI, users also use agentic tools to build their own abstractions.

A registry addresses both problems. A registry is a hosted catalog of source files. A command copies an item (a component, material, or helper) from the registry into the user's project, instead of installing a package into `node_modules`. One implementation can serve every framework, and users own and edit the code they install.

A registry also lets us support vanilla three.js and gives users a way to contribute components.

## Goals

A successful completion of this initiative will deliver a pilot registry with three items, installable into React, Vue, Svelte, Angular, and vanilla three.js projects, and a written recommendation on whether to extend it ecosystem-wide.

- Each pilot item has one framework-agnostic implementation where practical, with a thin adapter (a small framework-specific wrapper) per framework. Adapters may be generated where possible, but generation is not a requirement.
- Users install a pilot item into their own project with one command.
- Users choose between a WebGL variant and a WebGPU/TSL variant, where the registry defines one.
- Installed code is readable, un-minified, and safe to hand-edit.
- Agents can discover and install pilot items through an MCP server and agent-optimized documentation.
- A documented process for users to contribute new items.

## Scope

The initiative covers a pmndrs registry (the items, their conventions, and how users install them) and the tooling to deliver three.js abstractions as source files into user projects.

Included:

- Tooling to discover and install items, including an MCP server for agents.
- Shared framework-agnostic implementations where practical.
- `MeshTransmissionMaterial`, to validate a mostly framework-independent abstraction.
- `OrbitControls`, to validate an abstraction that needs framework lifecycle and state integration.
- A WebGPU/TSL item, to validate WebGPU/TSL abstractions.
- Contribution guidelines for new items.
- Exploring interoperability with existing registry ecosystems and tooling.

Excluded:

- Replacing `@react-three/drei` or `@tresjs/cientos` as installable npm dependencies during this initiative. They stay the "batteries included" option.

## Resources

- Other devs / maintainers: open.
- One maintainer per framework adapter (React, Vue, Svelte, Angular). This is the likely bottleneck, because each adapter needs someone who knows that framework.
- Community feedback.
- Docs and outreach for the new install method.

## Drawbacks

- A second distribution channel to maintain (the npm-installed component and the registry item). The two can drift apart.
- A new install method for users to learn.

## Prior art

Delivering source files directly into a user's project, rather than only through packages in `node_modules`, is now a popular distribution model in the web ecosystem. This initiative explores applying that model to three.js abstractions. The specific registry implementation and tooling stay open to experimentation and feedback.

## Open questions

- Should the existing npm abstractions go into maintenance mode or deprecation once a registry item exists for them?
- Can an existing open registry protocol express what we need (framework adapters, renderer variants, shared implementations)? If not, do we extend one or build our own?
