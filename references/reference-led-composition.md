# Reference-Led Composition

Use when a user supplies a figure to emulate or says a previous drawing does not communicate the topology.

## Extract structure, not decoration

Actually inspect the reference at overview and readable detail scale. Identify what the arrangement reveals:

- Which repeated branches are aligned, mirrored, stacked, or cascaded?
- Which intermediate nodes, flying elements, return paths, and common outputs anchor the composition?
- Which crossings are meaningful to understanding, and which can be removed by placement?
- How do the figure's device, control, annotation, and value densities fit its intended audience?

For example, a mirrored interleaved converter can benefit from inward-facing switch chains, inner/outer flying capacitors, a compact crossed network, and inductors meeting at a common output. This is a circuit-specific example, not a default layout for other converters. A differential analog stage, an RF chain, or a hierarchical digital interface may need a different structure.

Map the source circuit onto the selected structure before assigning coordinates. Keep the source netlist/native drawing as the authority for connections, distinct supplies, actual implementations, and device identifiers. A shared input rail, light-load detector, dead-time circuit, or MOSFET implementation in the reference is not permission to add it.

## Choose the fidelity boundary

Distinguish a functional block diagram, a paper-style topology/architecture figure, and a native simulator schematic. A paper-style figure usually exposes the characteristic device network and may summarize control internals. More boxes, longer wires, or every simulation parameter do not inherently make it clearer.

For a combined power/control view:

- Keep the useful power topology intact and put the controllers near the nodes they sense and actuate.
- Show distinct controlled variables as distinct sensing paths. Do not visually collapse coupled loops into independent regulators.
- Keep comparison polarity, state storage, timing/reset and the resulting drive destinations readable.
- Use matched labeled ports where explicit gate wires would obscure the topology. Define the matching signal-to-device association, including polarity where relevant.
- Separate device references from functional module names; do not imply that a historical net name establishes its pin function.

Do not hide an uncertain connection with a neat block or net label. Record the uncertainty and keep it out of unsupported claims.

## Recheck the actual result

Compare the revised diagram with the reference's structural advantages, not its exact colors or coordinates. Verify that the characteristic relationships are visible at overview scale and that local terminals, crossings and labels are unambiguous when enlarged.

An automated text-overlap check is only an aid: it can miss text on wires, confusing symbol shapes, unclosed loops, white-mask gaps and poor grouping. Review the rendered image as well. Keep source graph checks separate from native EDA equivalence and dynamic validation.
