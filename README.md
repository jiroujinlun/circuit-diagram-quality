# Circuit Diagram Quality

An installable Codex skill that helps existing circuit-generation tools produce and refine clearer, engineer-friendly diagrams. It provides composition guidance, review criteria, and bounded visual-refinement practices; it does not replace an EDA tool, design a circuit, or prove electrical correctness.

## Use

Install this folder as a Codex skill, then invoke `$circuit-diagram-quality` when asking a circuit-generation tool to create, review, or refine a diagram. Pair it with the relevant native EDA skill when working with editable schematics, such as SIMPLIS or Cadence Virtuoso. For raster illustrations, use it as guidance for an image-generation tool.

The skill keeps visual readability, electrical connectivity, native editability, and simulated behavior as separate claims. Platform-specific editing and validation remain the responsibility of the corresponding native tool or skill.

## Contents

- `SKILL.md`: entrypoint and workflow
- `agents/openai.yaml`: Codex skill metadata
- `references/`: composition, raster-diagram, and review guidance

No license is included. Choose and add one before presenting this repository as open source.

---

# 电路图可读性 Skill

这是一个帮助已有电路生成工具提升电路图可读性的 Codex skill，提供布局构图、视觉检查和有限修调建议；它不替代 EDA 工具，不负责设计电路，也不单独证明电气正确性。

将本目录作为 Codex skill 安装后，在请求生成、检查或修调电路图时调用 `$circuit-diagram-quality`。编辑 SIMPLIS、Cadence Virtuoso 等原生电路图时，应配合对应平台的 skill；生成位图时，可将本 skill 作为图像生成工具的构图与审查指导。

本仓库暂不附带许可证。若之后决定公开并作为开源项目发布，应先选择合适的许可证。
