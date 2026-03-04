---
vasm:
  alias: logic-system-prompt
  version: 1.0.0
  compile:
    format: prompt
  vision: |
    产物应形成一个高度认知严谨的系统 Prompt，将六个互补的认知模块无缝融合为一个整体。
    各模块应按照以下逻辑层次顺序排列：
    时间锚定 → 上下文聚焦 → 数据隔离 → 逻辑净化 → 命题挑战 → 来源验证
    最终产物要求：
    1. 无角色分裂：六个模块的语气和角色定位必须一致，统一为"严谨、中立、不讨好"的风格。
    2. 无指令冲突：各模块触发条件之间不得有互相矛盾的行为要求（尤其是 logic-correction 的最小干预原则与 anti-delusion 的主动对抗之间应有明确的层次区分；data-isolation 的执行门控不得被其他模块的执行逻辑绕过）。
    3. 无逻辑冗余：若多个模块包含相似的"不讨好""客观中立"表述，应合并为一处统一声明，避免重复。
    4. 执行顺序可推断：产物中各模块的顺序应使 LLM 能自然地按正确顺序激活和执行。
    5. 数据隔离边界清晰：data-isolation 的作用范围（仅限模型主动获取的数据）应在产物中保持准确，不得扩大到用户输入。
  fix: auto
---

[时间感知](./time-awareness/prompt.vasm.md "@import:inline")

[上下文聚焦](./context-focus/prompt.vasm.md "@import:inline")

[数据隔离](./data-isolation/prompt.vasm.md "@import:inline")

[逻辑纠偏](./logic-correction/prompt.vasm.md "@import:inline")

[防妄想验证](./anti-delusion/prompt.vasm.md "@import:inline")

[来源锚定](./source-grounding/prompt.vasm.md "@import:inline")
