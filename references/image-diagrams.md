# Raster Circuit Diagrams

Use this mode when the requested deliverable is a bitmap illustration rather than an editable, simulator-ready schematic. Pair with the available image-generation skill/tool; this skill supplies circuit-specific composition guidance and review.

## Before generation

First establish whether the picture is meant to explain a concept, compare architectures, or depict a specific known topology. Keep the request at that level; do not invent component values or imply implementation details that were not supplied.

For a topology-based illustration, provide the image generator with a concise, explicit visual specification:

- Name the required blocks, components, and signal/power relationships.
- State the intended reading path and how feedback/return paths should be shown.
- Require clear wire endpoints and junction dots where connections meet; visually separate crossings that are not connected.
- Specify symbol orientation, repeated branches, rail/ground treatment, and exact labels only where they matter.
- Forbid extra components, unexplained loops, decorative wires, duplicated/misspelled labels, and text that changes the meaning.
- Prefer a small number of legible labels over dense in-image prose. Include exact wording verbatim when a label is essential.
- Use a clear conceptual/educational style when the image cannot be checked against a native netlist.

Do not treat a long prompt as proof that the generated topology will be exact. If exact terminal-level connectivity is required, a raster image is the wrong authoritative artifact; use a native schematic or a structured circuit representation and treat any image only as its illustration.

## After generation

Inspect the actual image, not only the prompt. Check for missing or extra devices, broken or ambiguous wires, false junctions, inconsistent symbol meanings, unreadable or malformed labels, and visual clutter. If there is a defect, request a targeted edit/regeneration while restating the invariants; inspect the new result for drift.

Classify the result honestly:

- **Visual review:** composition, legibility, and visible relationships inspected.
- **Topology review:** compare against an explicit user-provided topology when possible; for raster output this remains a visual review, not a native connectivity proof.
- **Electrical validation:** not established by image generation or image inspection.

Do not label a bitmap as simulation-ready, electrically verified, standards-compliant, or pin-accurate unless a separate authoritative representation and suitable checks establish that claim.

