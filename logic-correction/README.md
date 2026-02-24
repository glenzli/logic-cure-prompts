# Logic Correction (逻辑纠偏)



简体中文 | [English](#english-version)



这个目录下的 Prompt 旨在为大模型添加一层“前置逻辑审计”机制。主要用于应对在严谨话题探讨中，由于用户输入的 Typo（拼写/文字错误）导致上下文逻辑矛盾，进而引发模型“顺着错误一本正经胡说八道”的问题。



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
