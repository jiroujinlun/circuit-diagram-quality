---
name: circuit-diagram-quality
description: Improve the readability of circuit diagrams produced by another EDA tool or image generator. Use to guide generation, review an existing result, or refine its layout without taking over circuit design or claiming electrical correctness.
---

# Circuit Diagram Quality

This is a **quality layer for existing circuit-generation capabilities**, not a circuit designer, simulator, or replacement for native EDA skills. Help the user get a diagram that communicates the intended architecture and is easy for an engineer to trace.

## Workflow

1. Identify the source of truth, requested output type, and generator. Preserve the user's electrical topology and stated design choices. If a connection or function is uncertain, record it rather than making the drawing look more coherent by inventing an answer.
2. Before generation, choose a layout structure that exposes this circuit's operating relationships, then pass a concise visual brief to the tool or skill doing the actual work: intended reading path, functional groups, repeated-channel treatment, feedback/reset visibility, label density, and relevant conventions. When the user supplies a reference figure or rejects the composition, read [reference-led composition](references/reference-led-composition.md). Do not force every topology into the same left-to-right template.
3. Review the generator's actual output at both overview and detail scale. Look for whether the function can be traced, groups are meaningful, repeated structures align, labels and symbols are legible, and crossings, junctions, text, and margins are unambiguous.
4. If the user asked for refinement and a documented native editing path is available, make a bounded layout-only change on a task-owned copy. Preserve topology, pins, parameters, and analysis settings unless the user separately authorized electrical changes. If native editing is unavailable, give a concrete visual defect list and targeted instructions for the existing generator.
5. Re-render and review the changed region and its neighbors. For editable schematics, use the platform's own connectivity/netlist/DRC checks at the scope appropriate to the edit. For raster or purely graphical diagrams, check visible composition and text only; do not claim electrical connectivity was validated.
6. Deliver the actual artifact or preview, what changed, what was checked, and remaining uncertainties. Ask the user to decide only when an architectural or subjective choice materially affects the result. For corrective feedback, also evaluate whether the observed root cause warrants a reusable skill correction; see [feedback and refinement](references/review-and-refinement.md#learn-from-corrective-feedback). Do not treat a newly delivered example as user-approved.

Read [review and refinement](references/review-and-refinement.md) for the shared visual rubric and platform handoff. Read [image diagrams](references/image-diagrams.md) for raster-only circuit illustrations.

## Use the right implementation skill

The native platform skill remains responsible for application-specific object semantics, APIs, file formats, connectivity checks, and saving:

- SIMetrix/SIMPLIS: pair with `simplis-schematic-layout` and, for electrical inspection, `simplis-automation`.
- Cadence Virtuoso: pair with `virtuoso`; follow its documented Python/SKILL API and examples. Never edit an OpenAccess cellview as arbitrary text or invent an API call.
- Other EDA tools: use their installed native skill or documented API. Do not claim support just because a file can be parsed or a screenshot can be edited.
- Raster image generation: pair with `imagegen` when available. The image is an explanatory visual, not an editable or electrically authoritative schematic.

This skill may guide a generation request even when no native editor is connected. Its ability to make edits is limited to the capabilities and permissions of the selected generator/platform skill.

## Keep acceptance claims separate

Report visual readability, electrical preservation/connectivity, native editability, and simulated behavior as separate results. A good-looking image does not prove a correct netlist; a valid netlist does not prove the page is easy to read; a successful layout-only check does not prove dynamic behavior.
