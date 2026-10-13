# Code Sandbox

**Status: Proposal**

## Motivation

We believe that code can be a craft, a creative medium, and a source of joy.

We want a way of exploring code that is interactive and playful. We want to be able to be independent of third party services and have our own sandbox that we can control and customize.

There are many existing offerings, but many are shifting their focus toward agentic coding and full production workflows. They depend on hosted infrastructure and evolving business models, which makes them less predictable for the simple act of writing and sharing code over the long term. We want something smaller and more dependable, that we own end to end, and that we can shape around showcases, demos, learning, and sharing.

## Goal

- Runs entirely in the browser with minimal pmndrs maintained infrastructure, so a sandbox is just static assets that can be hosted anywhere.
- Embeddable. Drops into docs, blog posts, examples, and playgrounds as a self-contained component with a small, stable surface.
- Dependable. Predictable behavior and a maintainable core we understand fully, so demos keep working years later without a service to keep alive.
- Playful. Fast feedback loops that make experimenting with code feel immediate and fun.
- A foundation for sharing. A common substrate for showcasing our work, teaching, and celebrating code across the ecosystem.

## Scope

The initiative covers a client-side, embeddable environment for authoring, running, and sharing self-contained code examples in the browser.

Included:

- In-browser editing and execution with fast feedback, initially targeting JavaScript/TypeScript and React/JSX, with possible expansion to other frameworks in future.
- An embeddable component with a small, stable API for docs, examples, and playgrounds.
- Live preview and console output.
- Theming and customization so sandboxes fit their host context.

We may lean on minimal external infrastructure we do not maintain, such as a public ESM CDN, for module resolution. We prefer to avoid infrastructure that we are responsible for running and keeping alive, but we may run our own if it proves the best path for longevity and maintainability.

Excluded:

- Server-side code execution, and Node.js emulation broadly (in-browser Node runtimes, filesystem, process, native modules).
- Production-grade IDE features and general-purpose app tooling.
- Accounts, collaboration, and multi-user features.
- Being a hosting or deployment platform for production apps.

## Resources

- Lead: Isaac Mason
- Embeddable examples across docs and showcases
- A playground to demonstrate and dogfood the sandbox
