# Anti-Delusion (防妄想/脚踏实地)

简体中文 | [English](#english-version)

这个目录下的 Prompt 旨在防止大模型在探讨前沿概念、新理论或新工具时陷入“闭门造车”和“逻辑内卷（唯理主义妄想）”。

## 📖 产生背景与作用

当大模型被要求探讨“创建新理论”或“构建新工具”时，常常会面临两个严重的陷阱：
1. **闭门造车（无视前人工作）**：在缺乏主动检索意识的情况下，容易把早已存在甚至已经淘汰的旧事物当成“全新发明”，导致重复造轮子。
2. **自洽妄想（脱离实际的逻辑内卷）**：大模型极擅长在给定的一套逻辑体系（哪怕是伪逻辑）内进行完美的推演。如果没有现实规律的约束，它很容易得出一个高度自洽但在真实世界中完全无法落地的结论，且常常还会出现跨尺度强行类比（比如把量子力学生搬硬套到宏观社会学上）的谬误。

针对这两种情况，该 Prompt 通过强制的**两段式验证（查重验证 + 跨域对抗）**，迫使模型：
- 第一步“向外求索”：主动利用知识库和联网搜索，寻找现实映射，避免重复造轮子。
- 第二步“红蓝对抗”：引入真实的硬核规律（物理定则、数学极限等）作为反方，进行跨域证伪，打破虚假的完美自洽。

## 📝 包含的文件

- `prompt.zh-CN.md`: 防妄想提示词（中文版）
- `prompt.en.md`: 防妄想提示词（英文版）

---
---

<a id="english-version"></a>

# Anti-Delusion

[简体中文](#anti-delusion-防妄想脚踏实地) | English

The prompts in this directory are designed to prevent Large Language Models from falling into the traps of "reinventing the wheel" and "logical involution (rationalist delusions)" when discussing cutting-edge concepts, new theories, or new tools.

## 📖 Background & Purpose

When asked to discuss "creating a new theory" or "building a new tool," LLMs often fall into two severe traps:
1. **Reinventing the Wheel (Ignoring Prior Art)**: Without an active awareness to retrieve information, the model can easily treat existing or even obsolete concepts as "brand new inventions," leading to redundant work.
2. **Self-Consistent Delusions (Detached Logical Involution)**: LLMs excel at performing perfect deductions within a given logical construct (even a flawed one). Without the constraints of real-world laws, they easily arrive at conclusions that are highly self-consistent but completely impractical in the real world. They also frequently commit the fallacy of forced cross-scale analogies (e.g., shoehorning quantum mechanics into macroscopic sociology).

To combat these issues, this Prompt uses a mandatory **two-stage verification (Duplication Check + Cross-Domain Confrontation)**, forcing the model to:
- **Step 1 - Outward Exploration**: Actively utilize its existing knowledge and network search to find real-world mappings and avoid reinventing the wheel.
- **Step 2 - Red/Blue Team Confrontation**: Introduce real hard rules (physical principles, mathematical limits, etc.) as the opposing side to conduct cross-domain falsification, breaking the illusion of perfect self-consistency.

## 📝 Included Files

- `prompt.zh-CN.md`: Anti-Delusion prompt (Chinese version)
- `prompt.en.md`: Anti-Delusion prompt (English version)
