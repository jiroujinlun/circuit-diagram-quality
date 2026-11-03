# Review and Refinement

Use this reference when passing design guidance to another circuit generator or reviewing/refining its output.

## Make a compact visual brief

Describe the reader's task before prescribing coordinates:

- What should the reader notice first: energy path, signal path, repeated channels, feedback loop, timing sequence, or interfaces?
- What are the real functional blocks, and which important connections cross their boundaries?
- Which direction or convention already fits the topology, application, or user's existing drawing?
- Which labels, polarity marks, references, values, rails, or measurement-only branches are essential to understanding?
- What must remain unchanged electrically and visually?

Keep requested conventions consistent with the platform, discipline, user reference, and applicable symbol standards. Treat standards as symbol/notation guidance, not an automatic page-layout solution.

When handing the brief to another generator, adapt this compact template rather than forwarding every field mechanically:

```text
Purpose/readers:
Authoritative topology/source:
Primary reading path:
Functional groups and repeated channels:
Feedback, reset, return, and cross-group paths to keep traceable:
Required labels/polarities/units:
Visual conventions or reference to follow:
Must preserve:
Must avoid:
Output format and checks available:
```

## Review at two scales

At overview scale, check that the visual hierarchy explains the architecture: major power or signal paths, functional neighborhoods, interfaces, feedback routes, and repeated groups should be apparent without reading every value.

At detail scale, check that a reader can trace local paths without guessing: symbols face a useful direction, pin labels and polarities are visible, wires reach the intended terminals, junctions are distinct from crossings, text does not obscure wires or symbols, and repeated channels are comparable.

For feedback/control circuits, trace sensor -> processing/error path -> actuator -> controlled plant, including reference polarity and return. For stateful logic, trace set/trigger, used output polarity, delay and reset/discharge paths. Keep unused, measurement-only, auxiliary, or uncertain signals visibly distinct from active paths.

When adding control to an established power or signal diagram, preserve its useful layout structure. Reserve space for sensing taps, forward control, drive outputs, and return/reset paths before drawing. Explicitly identify comparator +/-, latch S/R and used Q/Q-bar outputs from the authoritative pins, not signal names. Repeated net labels or ports may replace long wires, but show both ends and their driver/device mapping; a list of output signal names alone does not close the depicted loop. A grouped driver must not imply validated non-overlap timing.

Keep abstraction deliberate. A compensation block may summarize verified internals in an architecture view, but comparator polarity, controlled variable, actuator destination, and state/reset connections that explain operation should remain traceable. Name the summarized device group and disclose omitted supplies, auxiliary outputs, or model details. Do not substitute a generic PI/PWM architecture for the source circuit or copy unimplemented functions from a reference paper.

Do not prescribe left-to-right flow, rectangular module boxes, mirrored symmetry, or explicit wiring in every case. Use those only when they improve this particular reader's task. Avoid excessive labels, annotations, and frames that add visual noise or imply electrical hierarchy where none exists.

## Refine with evidence

For layout-only edits:

- Keep an untouched source snapshot and use a separate working copy when feasible.
- List intended visual changes before editing. Do not rename nets, move pins in ways that change meaning, alter parameters, or modify analysis controls as incidental cleanup.
- Re-open or render the actual result with the native application when possible. A hand-redrawn illustration is not evidence that the native artifact remains readable or editable.
- Compare connectivity or export a netlist before and after if the platform supports it. Ignore harmless anonymous-node renumbering only after comparing terminal-to-net relationships.
- Fix a small set of visible defects per iteration, then review the edited region and affected connections. Stop when remaining choices are subjective or lack evidence; show the user the actual preview and the concrete decision.

When no documented native edit path is available, produce actionable feedback tied to visible locations and a targeted prompt or instruction for the existing generator. Do not silently switch to an unrelated format or claim the source artifact was modified.

Phrase findings as `location -> observed issue -> why it hurts traceability -> bounded correction -> check to repeat`. Separate a verified defect from a preference, and do not invent a numeric readability score.

## Learn from corrective feedback

After addressing a reported problem, distinguish the artifact correction from a possible skill correction:

- Identify the demonstrated root cause: for example, a poor topology-specific layout choice, an untraceable feedback endpoint, or a rendering defect that survived a text-only check.
- Generalize the decision that would prevent recurrence, not the case's coordinates, device values, project paths, or particular symmetry. Keep subjective preferences scoped to the relevant user/reference.
- If the user has authorized skill maintenance and the rule is genuinely missing, make a narrow update in the entrypoint or relevant reference; otherwise retain the lesson in the task report or propose it. Do not rewrite unrelated platform skills or automatically enlarge a gallery.
- Validate changed instructions and links, then rerender/recheck the artifact against the reported defect. State what the skill now changes, or why this feedback did not require a new rule.

Paper figures are layout references, not automatic electrical authorities. Newly revised examples remain candidates until the user accepts them; source-device assertions, native connectivity checks, and simulation evidence retain their separate scopes.

## Handoff matrix

| Output | Generator/implementation owner | Quality-layer role | Appropriate evidence |
|---|---|---|---|
| Editable SIMPLIS schematic | SIMPLIS native workflow | Visual brief, rendered review, bounded layout refinement | Native preview plus netlist/connectivity comparison scoped to the edit |
| Editable Virtuoso schematic | Virtuoso bridge/API workflow | Visual brief, rendered review, bounded layout refinement | Native cellview preview plus schematic/netlist/DRC checks available in that environment |
| Other native EDA schematic | That platform's installed skill or documented API | Guidance and review; edit only through a supported interface | Its native export, connectivity checker, ERC/DRC, and render |
| Raster/illustrative circuit image | Image-generation capability | Prompt shaping and visual critique/iteration | Render inspection and exact visible-text review; no electrical-equivalence claim |

