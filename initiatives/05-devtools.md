# Devtools

**Status: Draft**

## Motivations

Devtooling is getting built at a faster rate than ever with agents. These tools conflict, competing for screen real estate and compute resources while trying to measure the same things. Pmndrs itself has this problem where its various controls and profiling tools do not share the same design language. 

Controls are equally important in the devtool stack, allowing devs to debug, tune and demo. A standard control system brings the whole package together.

## Goals

- Create a new package that provides a framework for surfaces, panels, shared resources, and other devtools infrastructure.
- Support profiling in a separate process, in another window or even over the network for devices like a phone.
- Support docked or floating tools with a compact design, as well as a separate window with an expanded design.
- Provide a robust tweak and control layer via Leva that is simple for the end user. It just works.
- Make controls easy to extend with new components.
- Separate logic from the view. Prioritize a headless core with themes layered on top.
- Provide a state machine with undo, redo, and saved state. Consider migrations for future releases.
- Support a JSON schema so AI can build reliably, and configuration and state can be saved and shared.

## Scope

Included:

- Surfaces, panels, rendering, and the devtools framework.
- Leva and controls.

Excluded:

- Design system.
- A way to share control extensions.
- Specific tools beyond controls.

## Resources

- Lead devs: Kris?
- Design!
- Community feedback
