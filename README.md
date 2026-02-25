# Logic Cure Prompts (逻辑治愈提示词)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

简体中文 | [English](#english-version)

欢迎来到 **Logic Cure Prompts**（逻辑治愈提示词）仓库！这是一个专门收集、提炼和分享**用于辅助大语言模型（LLM）实现认知校准、减少幻觉并达到逻辑闭环**的精选 Prompt 集合。

---

## 🎯 为什么建立这个仓库？

在大模型（LLM）的日常交互中，我们经常发现模型在处理严谨逻辑时存在一些典型的“先天缺陷”（以下仅为几个核心示例，本仓库会持续补充）：

1.  **逻辑审计缺失（Typo 陷阱）**：由于中文错别字的特殊性，模型往往缺乏自动纠错甚至识别错误的能力。它不仅不会停下来确认，反而会“顺着”错误的输入进行天马行空的推演，导致逻辑全盘崩溃。
2.  **时间感知模糊（时空错乱）**：模型往往不知道当前时间，导致它在处理具有时序性的任务时（如事件追踪、最新动态分析），会将过去和现在混为一谈，优先级难分。
3.  **认知妄想（闭门造车）**：大模型极擅长在给定的一套逻辑体系内进行“完美自洽”的推演。如果没有现实规律（如物理定则、已有发明）的硬性约束，它很容易陷入重复造轮子或得出高度自洽但在现实中完全无法落地的“逻辑幻象”。

**Logic Cure Prompts** 的愿景是通过在输入层植入“预响应审计层”，对模型的认知模式进行干预和“治愈”。我们不仅希望模型能应对人类的错误输入，更希望模型能具备**时间主轴意识**和**现实世界锚点**，从而在复杂、严谨的工程与科研场景下表现出职业级的鲁棒性。

## 📂 仓库结构

目前的目录结构分类：

```text
logic-cure-prompts/
├── logic-correction/       # 逻辑与拼写审计纠偏
│   ├── prompt.zh-CN.md     # 防止因输入 Typo 导致的逻辑崩溃
│   └── prompt.en.md
├── time-awareness/         # 时间感知与时序对齐
│   ├── prompt.zh-CN.md     # 引入时间锚点，解决时空错乱与信息落后
│   └── prompt.en.md
├── anti-delusion/          # 防妄想与脚踏实地
│   ├── prompt.zh-CN.md     # 强制查重验证与跨域对抗，防止闭门造车
│   └── prompt.en.md
└── xxx-feature/            # 未来添加的其他逻辑增强类 Prompt
```

## 🚀 如何使用

1.  **寻找场景**：根据你的任务需求（如需要纠错、需要时间参考、或需要严谨验证）进入对应文件夹。
2.  **复制建议**：打开 `.zh-CN.md` 或 `.en.md` 并复制内容。
3.  **植入对话**：
    *   **System Prompt**：作为全局设定，适合 API 调用。
    *   **对话前缀**：在正式提问前，先让模型学习该 Prompt 进入对应工作状态。



---

<a id="english-version"></a>

# Logic Cure Prompts

[简体中文](#logic-cure-prompts-逻辑治愈提示词) | English

Welcome to the **Logic Cure Prompts** repository! Dedicated to collecting and refining **curated prompts that help LLMs achieve cognitive calibration, reduce hallucinations, and attain logical closure.**

---

## 🎯 Why this repository?

In interactions with LLMs, we frequently encounter several typical "innate deficiencies" in rigorous reasoning (the following are just a few core examples; this repository will continually add more):

1.  **Lack of Logical Auditing (Typo Trap)**: LLMs often struggle with unrecognized typos. Instead of pausing to clarify, they follow the error into elaborate hallucinations, causing the entire logical chain to collapse.
2.  **Blurred Time Perception (Temporal Confusion)**: Without knowing the current time, models can confuse past and present events, failing to prioritize recent information or track events chronologically.
3.  **Cognitive Delusions (Reinventing the Wheel)**: LLMs excel at perfect deductions within a given logical construct. Without the constraints of real-world laws or existing prior art, they easily fall into the trap of reinventing the wheel or generating "logical illusions" that are internally consistent but physically impossible.

**Logic Cure Prompts** aims to intervene and "cure" the model's cognitive patterns by embedding a "Pre-response Audit Layer" at the input level. Our goal is to empower models not just to handle human errors but to develop an **awareness of the temporal axis** and **real-world anchors**, ensuring professional-grade robustness in complex engineering and scientific scenarios.

## 📂 Project Structure

Current directory categories:

```text
logic-cure-prompts/
├── logic-correction/       # Logic / Typo Audit & Correction
│   ├── prompt.zh-CN.md     # Prevents logic collapse due to input typos
│   └── prompt.en.md
├── time-awareness/         # Time Awareness & Temporal Alignment
│   ├── prompt.zh-CN.md     # Introduces time anchors to resolve temporal confusion
│   └── prompt.en.md
├── anti-delusion/          # Anti-Delusion & Grounded Reasoning
│   ├── prompt.zh-CN.md     # Forces duplication checks and cross-domain confrontation
│   └── prompt.en.md
└── xxx-feature/            # Future additions for specific logic-enhancing Prompts
```

## 🚀 How to Use

1.  **Find the Scenario**: Navigate to the category matching your needs (e.g., error correction, temporal reference, or rigorous validation).
2.  **Copy the Prompt**: Open the corresponding `.zh-CN.md` or `.en.md` file and copy the contents.
3.  **Inject into Conversation**:
    *   **As a System Prompt**: Best for API usage as a global setting.
    *   **As a Conversational Prefix**: Send the prompt before your main query to initialize the model's state.


