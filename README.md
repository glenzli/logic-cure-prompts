# Logic Cure Prompts (逻辑治愈提示词)



[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)



简体中文 | [English](#english-version)



欢迎来到 **Logic Cure Prompts**（逻辑治愈提示词）仓库！这是一个专门收集、提炼和分享**用于辅助大语言模型（LLM）提升逻辑能力、减少幻觉并达到更好模型效果**的精选 Prompt 集合。



---



## 🎯 为什么建立这个仓库？



在使用大模型的过程中，我们经常会遇到模型在处理严谨的数学、物理、系统设计或长逻辑链条任务时，出现“一本正经地胡说八道”的情况。

比如，一种情况是当我们在输入中出现 Typo（拼写或输入法导致的文本错误）时，大模型往往**缺乏自动纠错甚至识别错误的能力**。它不仅不会停下来确认，反而会“顺着”这个错误的词组进行天马行空的发散推演，把错误当成你的真实意图，哪怕这会导致后面的逻辑全盘崩溃。



**Logic Cure Prompts** 的愿景与目标是通过特定结构的 Prompt（系统提示或对话前缀），在输入层面对模型的认知模式进行干预和“治愈”。我们希望强制模型在输出前进行逻辑自洽审计、思维链构建或常识校验，使其具备应对人类错误输入的鲁棒性，从而大幅提升模型在复杂、严谨场景下的表现与可靠性。



## 📂 仓库结构



为了方便查找和组合，本仓库中的所有 Prompt 都按“功能场景”在独立的文件夹中进行管理。每个文件夹通常包含中英双语的 Prompt 文件。



目前的目录结构示例：



```text

logic-cure-prompts/

├── logic-correction/       # 逻辑与拼写审计纠偏分类

│   ├── prompt.zh-CN.md     # 逻辑纠偏 Prompt (中文)

│   └── prompt.en.md        # 逻辑纠偏 Prompt (英文)

├── time-awareness/         # 时间感知增强分类

│   ├── prompt.zh-CN.md     # 时间感知 Prompt (中文)

│   └── prompt.en.md        # 时间感知 Prompt (英文)

├── xxx-feature/            # 未来添加的其他特定逻辑增强类 Prompt

└── README.md               # 本文件

```



## 🚀 如何使用



1. **浏览目录**：找到你当前需要的逻辑增强场景（例如：你需要模型在回答严谨问题前自我审查，就可以进入 `logic-correction/`）。

2. **复制 Prompt**：打开对应的 `.zh-CN.md` 或 `.en.md` 文件，复制其中的内容。

3. **植入对话**：

   - **作为 System Prompt**：如果你在使用 API 或支持自定义系统提示的客户端，将复制的内容粘贴到 System Prompt 区域，以此作为全局设定。

   - **作为 对话 Prompt**：如果你在网页端使用聊天机器人，可以在正式提问前，将这段指令发给模型，让其进入对应的状态。



## 🤝 参与贡献



如果你在日常使用中发现了能够显著提升 LLM 逻辑判断、推理能力或特定领域表现的 Prompt，非常欢迎提交 PR 加入本仓库！



**贡献指南：**



1. Fork 本仓库。

2. 创建一个描述清晰的功能文件夹（建议使用小写字母和连字符，如 `step-by-step-reasoning`）。

3. 在该文件夹中添加 `prompt.zh-CN.md` 和 `prompt.en.md`。

4. 提交 Pull Request，并在描述中简单说明该 Prompt 的作用和适用场景。



## 📄 协议



本项目采用 [MIT License](LICENSE) 协议开源。你可以自由地使用、修改和分发这些提示词。



---

---



<a id="english-version"></a>

# Logic Cure Prompts



[简体中文](#logic-cure-prompts-逻辑治愈提示词) | English



Welcome to the **Logic Cure Prompts** repository! This is a curated collection of prompt engineering strategies designed specifically to **help Large Language Models (LLMs) enhance their logical reasoning capabilities, reduce hallucinations, and achieve overall better model performance**.



---



## 🎯 Why this repository?



When interacting with LLMs, we often encounter situations where the model "hallucinates confidently" when handling rigorous topics like mathematics, physics, system design, or long-chain logical tasks. 

For instance, one such situation is when our input contains a Typo. LLMs frequently **lack the ability to auto-correct or even recognize these typos contextually**. Instead of pausing to clarify, they will wildly diverge and build complex, logically flawed derivations exactly based on that single mistake, treating your typo as your actual intent, even if the entire logical chain collapses as a result.



The vision and goal of **Logic Cure Prompts** is to intervene and "cure" the model's cognitive patterns at the input level through precisely structured Prompts (System Prompts or conversational prefixes). By forcing the model to perform logical self-auditing, construct chain-of-thought, or validate common sense before generating output, we aim to make LLMs more robust against human input errors, thereby significantly improving their reliability and performance in complex, rigorous scenarios.



## 📂 Project Structure



To make finding and combining prompts easier, all prompts in this repository are organized into standalone folders based on their "functional scenario." Each folder typically contains dual-language (Chinese & English) prompt files.



Current directory structure example:



```text

logic-cure-prompts/

├── logic-correction/       # Logic / Typo Audit & Correction

│   ├── prompt.zh-CN.md     # Logic Correction Prompt (Chinese)

│   └── prompt.en.md        # Logic Correction Prompt (English)

├── time-awareness/         # Time Awareness Enhancement

│   ├── prompt.zh-CN.md     # Time Awareness Prompt (Chinese)

│   └── prompt.en.md        # Time Awareness Prompt (English)

├── xxx-feature/            # Future additions for specific logic-enhancing Prompts

└── README.md               # This file

```



## 🚀 How to Use



1. **Browse Categories**: Find the logic enhancement scenario you need right now (e.g., if you need the model to self-audit before answering rigorous questions, check out `logic-correction/`).

2. **Copy the Prompt**: Open the corresponding `.zh-CN.md` or `.en.md` file and copy the contents.

3. **Inject into Conversation**:

   - **As a System Prompt**: If you are using APIs or clients that support custom system instructions, paste the copied content into the System Prompt area to set the global context.

   - **As a Chat Prompt**: If you are using web-based chatbots, simply send this instruction to the model before asking your main question to initialize the desired state.



## 🤝 Contributing



If you discover any prompts in your daily usage that significantly improve an LLM's logical judgment, reasoning abilities, or performance in specific domains, your PRs are highly welcome!



**Contribution Guidelines:**



1. Fork this repository.

2. Create a clearly named feature folder (use lowercase and hyphens, e.g., `step-by-step-reasoning`).

3. Add `prompt.zh-CN.md` and `prompt.en.md` within the folder.

4. Submit a Pull Request, explaining the prompt's purpose and applicable scenarios in the description.



## 📄 License



This project is licensed under the [MIT License](LICENSE). You are free to use, modify, and distribute these prompts.
