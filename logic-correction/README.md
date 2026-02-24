# Logic Correction (逻辑纠偏)



简体中文 | [English](#english-version)



这个目录下的 Prompt 旨在为大模型添加一层“前置逻辑审计”机制。主要用于应对在严谨话题探讨中，由于用户输入的 Typo（拼写/文字错误）导致上下文逻辑矛盾，进而引发模型“顺着错误一本正经胡说八道”的问题。

## 📖 产生背景与示例

关于这个 Prompt 的起源，是因为我们在使用大模型时发现，当遇到中文 Typo 时，由于中文错别字的特殊性，大模型往往**不具备任何自动纠错的能力**。相反，它会“顺着”这个错别字继续发散推演，哪怕导致整个上下文逻辑完全崩盘。模型不会觉得哪里有问题，而是会一本正经地胡来。

**典型示例：**

- **用户意图输入**：使用 LLM 进行校验
- **用户实际输入 (含Typo)**：使用 LLM 记性教研（拼音输入法导致的口误）
- **模型常规表现**：模型不会识别出此时讨论的上下文需要的是“校验（jiào yàn）”，而是提取字面意思“记性（jì xing）”与“教研（jiào yán）”，开始大谈特谈如何利用 LLM 来增强人类记忆力并赋能教育研究。这会导致接下来的探讨完全偏离原本严谨的系统设计意图。



## 🌟 核心功能



- **语境感知**：自动判断当前对话是否属于严谨话题（如数学、科学、编程、系统设计等）。

- **强制审计**：在回答前，强制模型先寻找并指出输入中可能存在的 Typo 或逻辑矛盾。

- **动态纠偏**：输出修正后的“逻辑基点”，确保后续回答建立在正确的假设之上。

- **弹性豁免**：对于文学创作或日常闲聊，不强制干预，保持正常的回复流畅度。



## 💡 适用场景



- **辅助编程与系统打样**：防止因为你在描述需求时打错了一个变量名或依赖关系，导致模型写出完全跑偏的代码。

- **数理逻辑探讨**：防止因输入中的一个符号笔误，导致模型顺着错误的推导继续演绎。



## 📝 包含的文件



- `prompt.zh-CN.md`: 逻辑纠偏提示词（中文版）

- `prompt.en.md`: 逻辑纠偏提示词（英文版）



---

---



<a id="english-version"></a>

# Logic Correction



[简体中文](#logic-correction-逻辑纠偏) | English



The prompts in this directory are designed to add a "pre-response logical audit" mechanism to Large Language Models. Their primary purpose is to address situations where a user's typo in a rigorous discussion creates a logical contradiction in the context, causing the model to confidently generate a flawed or nonsensical response based on that error.

## 📖 Background & Example

The origin of this Prompt stems from a common issue when using Large Language Models: when encountering Chinese typos (or similar errors in other languages), due to the unique nature of character-based typos, LLMs often **lack any automatic error-correction capability**. Instead of realizing the mistake based on the context, the model will "run with" the typo and wildly diverge from the intended topic, even if the resulting logic is completely flawed. It presents this nonsense confidently.

**A Typical Example:**

- **Intended Input**: 使用 LLM 进行校验 (Use LLM to perform *verification*)
- **Actual Input with Typo**: 使用 LLM 记性教研 (Use LLM for *rote memory teaching/research*)
- **Typical Model Behavior**: Instead of recognizing the typo for "verification" (校验 - jiàoyàn) based on a system design context, the model interprets "rote memory" (记性 - jìxing) and "teaching/research" (教研 - jiàoyán) literally. It will then confidently generate a lengthy response about how to use LLMs to improve human memory and empower educational research, completely derailing the original intent of the discussion.



## 🌟 Core Features



- **Context Awareness**: Automatically determines whether the current conversation falls under rigorous topics (e.g., mathematics, science, programming, system design).

- **Forced Auditing**: Forces the model to actively hunt for and point out potential typos or logical contradictions in the input before generating the main response.

- **Dynamic Correction**: Outputs a corrected "logical baseline" to ensure the subsequent answer is built upon sound assumptions.

- **Flexible Exemption**: Does not force intervention during literature creation or daily chat, maintaining normal conversational fluency.



## 💡 Use Cases



- **Programming & System Prototyping**: Prevents the model from writing completely derailed code just because you accidentally mistyped a variable name or dependency in your requirements.

- **Mathematical & Scientific Discussions**: Prevents the model from happily continuing a flawed derivation due to a single slipped symbol or typo in your input.



## 📝 Included Files



- `prompt.zh-CN.md`: Logic correction prompt (Chinese version)

- `prompt.en.md`: Logic correction prompt (English version)
