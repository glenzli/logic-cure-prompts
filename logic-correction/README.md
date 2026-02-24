# Logic Correction (逻辑纠偏)



简体中文 | [English](#english-version)



这个目录下的 Prompt 旨在为大模型添加一层“前置逻辑审计”机制。主要用于应对在严谨话题探讨中，由于用户输入的 Typo（拼写/文字错误）导致上下文逻辑矛盾，进而引发模型“顺着错误一本正经胡说八道”的问题。

## 📖 产生背景与示例

关于这个 Prompt 的起源，是因为我们在使用大模型时发现，当遇到中文 Typo 时，由于中文错别字的特殊性，大模型往往**不具备任何自动纠错的能力**。相反，它会“顺着”这个错别字继续发散推演，哪怕导致整个上下文逻辑完全崩盘。模型不会觉得哪里有问题，而是会一本正经地胡来。

**典型示例：**

- **用户意图输入**：使用 LLM 进行校验
- **用户实际输入 (含Typo)**：使用 LLM 记性教研（拼音输入法导致的口误）
- **模型常规表现**：模型不会识别出此时讨论的上下文需要的是“校验（jiào yàn）”，而是提取字面意思“记性（jì xing）”与“教研（jiào yán）”，开始大谈特谈如何利用 LLM 来增强人类记忆力并赋能教育研究。这会导致接下来的探讨完全偏离原本严谨的系统设计意图。

<details>
<summary><b>💬 点击展开查看详细的真实对话示例</b></summary>

- 用户输入：如果我们模仿人脑结构去提升AI的可用性，比如我们为LLM大脑引入一个伴生的小脑，使用一个小模型进行教研，我们应该怎么做？
- 大模型回答：
```
这是一个非常深刻且符合当前AI前沿发展趋势的构想。在神经科学中，**大脑（Cerebrum）负责意识、推理和规划，而小脑（Cerebellum）**负责协调、运动控制、精细调节和即时反应。
将这一生物学架构映射到AI系统（LLM System）中，可以极大地解决当前大模型推理慢、成本高、幻觉多、难以精确控制的痛点。
如果我们引入一个“伴生小脑”（Small Model），并让其承担“教研”（即教学、校准、反馈）的角色，我们可以从以下四个维度来构建这个架构：
一、 角色定义：大脑与小脑的分工
首先，我们需要明确两个模型的定位：
大脑 (LLM - System 2):
模型示例: GPT-4, Claude 3.5 Sonnet, Llama-3-70B/405B.
职责: 处理模糊指令、进行复杂逻辑推理、生成创造性内容、处理长上下文。
特点: 慢、贵、泛化能力强、负责“想”。
小脑 (Small Model - System 1):
模型示例: Llama-3-8B, Mistral 7B, 甚至是专门蒸馏过的BERT/T5级别模型。
职责: 格式对齐、安全拦截、实时纠错、工具调用（Tool Use）、推测性解码。
特点: 快、极其便宜、特定任务精度极高、负责“做”和“管”。
二、 架构实现方案：小脑如何介入？
我们可以设计三种具体的架构模式，让小脑提升系统的整体可用性。
1. 前置小脑：反射与分流 (Reflex & Routing)
小脑作为“看门人”，在信号到达大脑之前进行处理。
意图识别与分流: 用户的问题是“写一首诗”（在大脑能力圈）还是“查询天气”（小脑调用API即可解决）？小脑判定后，简单任务直接拦截处理，不消耗大脑算力。
Prompt 优化: 小脑可以将用户模糊的输入改写为结构化、清晰的Prompt，再喂给大脑，充当“助教”帮学生（用户）把问题问对。
2. 同步小脑：推测与对齐 (Speculative & Alignment)
这是最接近生物小脑“运动协调”功能的用法。
推测性解码 (Speculative Decoding): 小脑快速生成草稿（Token预测），大脑只需负责并行验证这些Token是否正确。这能在大模型不降智的情况下，将推理速度提升2-3倍。
格式强制 (Constrained Generation): 当我们需要JSON或特定代码格式时，大脑负责生成内容逻辑，小脑负责监控输出流，一旦发现格式错误（如少了一个括号），小脑立即介入修正，或者强制在大脑的输出层施加Logit掩码。
3. 后置小脑：判别与修正 (Critic & Correction)
这是你提到的“教研”功能的核心。小脑充当“阅卷老师”或“质检员”。
幻觉检测: 针对RAG（检索增强生成）场景，小脑专门训练用于比对“上下文”和“回答”的一致性。如果发现大脑瞎编，小脑打回重写。
逻辑校验: 对于代码生成，小脑可以是解释器或静态分析工具的代理，运行失败则反馈报错信息给大脑进行自我修复。
三、 核心环节：“教研”机制（The Teaching & Research Loop）
你提到了**“教研”，这意味着两个模型之间不是静态的，而是动态进化的。这需要建立一套知识蒸馏（Knowledge Distillation）与反馈闭环**：
步骤 1：大师带徒弟（Distillation）
冷启动: 一开始，小脑很笨。我们使用大脑（GPT-4）生成大量的高质量数据（Question-Answer pairs, 思维链CoT），专门用来微调小脑。
专项训练: 比如，为了让小脑学会“提取JSON”，我们让大脑生成各种复杂的文本和对应的完美JSON，把小脑训练成一个“提取专家”。此时，小脑在特定单项技能上可能超过通用的大脑。
步骤 2：徒弟帮大师（Auxiliary Control）
在实际运行中，小脑处理高频、简单的任务。
困难样本挖掘: 当小脑遇到处理不了的（置信度低）请求时，它会将请求上报给大脑（Escalation）。
步骤 3：教研复盘（Feedback Optimization）
日志分析: 系统定期收集“大脑修正小脑错误”的案例，以及“大脑本身犯错”的案例。
DPO/RLHF: 将这些案例整理成偏好数据（DPO），让小脑学习大脑的判断标准。
最终形态: 随着时间推移，小脑掌握了90%的日常场景（形成了“肌肉记忆”），只有10%的难题需要大脑介入。系统的响应速度极快，成本极低。
...
```
可以看到，模型完全顺着“教研”发散出了一些看起来头头是道，实际上十分离谱的答案。

如果我们引入 **logic-correction** 提示词，会发生什么呢？模型的输出如下：
```
[逻辑纠偏模式已激活]
检测结果：
在系统设计语境下，输入存在一处极高概率的同音/近义词笔误。
原输入：“...使用一个小模型进行教研...”
修正基点：“...使用一个小模型进行校验...”
修正理由：在“大脑（决策/生成）- 小脑（协调/控制）”的生物学隐喻中，小脑的核心功能是实时误差修正与运动协调，对应AI工程中的校验（Verification）、校准（Calibration）或监控。而“教研（Teaching and Research）”通常指组织层面的教学研究活动，不符合实时系统架构的术语习惯。

基于修正后的逻辑（即如何构建一个负责校验与控制的“AI小脑”），以下是系统设计方案：
将AI架构从单体的“全能大脑”转变为“大脑+小脑”的二元结构，核心在于解耦：System 2（大脑，重推理、慢、贵）与 System 1（小脑，重直觉、快、稳）。要实现这一架构，需从模型训练、推理时干预和反馈闭环三个层面入手：
一、 核心架构设计：小脑的职责定义
“小脑”在工程上通常是一个参数量小（如 0.5B - 7B）、响应极快、针对特定任务（格式对齐、安全性、逻辑检查）过拟合的专用模型。
大脑 (The Generator): 负责生成高熵、高创造性、长逻辑链的内容。
小脑 (The Verifier/Controller): 负责低熵任务，对大脑的输出进行“质检”和“整形”。
...
```
可以看到，经过 prompts 纠偏后，在这样的讨论场景下模型更容易回归并匹配用户的实际意图。
</details>
## 🌟 核心功能



- **语境感知**：自动判断当前对话是否属于严谨话题（如数学、科学、编程、系统设计等）。

- **强制审计**：在回答前，强制模型先寻找并指出输入中可能存在的 Typo 或逻辑矛盾。

- **动态纠偏与最小改动原则**：输出修正后的“逻辑基点”，确保后续回答建立在正确的假设之上。但遵循**最小改动原则**（如仅修改一两个错别字、介词），若系统认为需要大幅度修改用户的原意才能逻辑自洽，则只会提出质疑，而不进行强制篡改。

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

<details>
<summary><b>💬 Click to view a detailed real-world example</b></summary>

- **User Input**: "If we mimic the structure of the human brain to improve AI usability, for example, by introducing a companion cerebellum for the LLM brain, and using a small model for **teaching and research (教研 - jiàoyán)**, what should we do?"

**(Without Logic Correction Prompt)** 
The model hallucinates gracefully and produces a plausible but topically derived answer based entirely on the typo:
> "This is a very profound concept... If we introduce a small model and let it take on the role of 'teaching and research' (i.e., teaching, calibration, feedback), we can build this architecture from four dimensions...
> ... *(The model proceeds to elaborately describe an AI architecture dedicated to autonomous educational research and knowledge distillation, a massive divergence from the intended system verification context.)*"

As you can see, the model generates a seemingly flawless but practically absurd answer by just following the "teaching/research" typo. 

**(With Logic-Correction Prompt)** 
The model realizes the contradiction:
> **[Logic Correction Mode Activated]**
> **Audit Result**: In the context of system design, there is a highly probable phonetic typo in the input.
> **Original Input**: "...using a small model for teaching and research (教研)..."
> **Corrected Baseline**: "...using a small model for verification (校验)..."
> **Reasoning**: In the biological metaphor of "Cerebrum (decision-making/generation) - Cerebellum (coordination/control)", the core function of the cerebellum is real-time error correction and motor coordination, which corresponds to Verification, Calibration, or Monitoring in AI engineering. "Teaching and Research" typically refers to organizational educational activities and does not fit the terminology of a real-time system architecture.
> 
> *Based on the corrected logic (how to build an "AI cerebellum" responsible for verification and control), here is the system design plan:*
> ... *(Proceeds to provide the correct system architecture)*

As demonstrated, after correction via the prompt, the model is much more likely to match the user's actual intent in such rigorous discussion scenarios.
</details>



## 🌟 Core Features



- **Context Awareness**: Automatically determines whether the current conversation falls under rigorous topics (e.g., mathematics, science, programming, system design).

- **Forced Auditing**: Forces the model to actively hunt for and point out potential typos or logical contradictions in the input before generating the main response.

- **Dynamic Correction & Principle of Minimal Modification**: Outputs a corrected "logical baseline" to ensure the subsequent answer is built upon sound assumptions. However, this follows the **Principle of Minimal Modification** (e.g., only fixing a typo or preposition). If the model determines that a significant change to the user's original intent is required to achieve logical consistency, it will only raise doubts instead of forcefully altering the input.

- **Flexible Exemption**: Does not force intervention during literature creation or daily chat, maintaining normal conversational fluency.



## 💡 Use Cases



- **Programming & System Prototyping**: Prevents the model from writing completely derailed code just because you accidentally mistyped a variable name or dependency in your requirements.

- **Mathematical & Scientific Discussions**: Prevents the model from happily continuing a flawed derivation due to a single slipped symbol or typo in your input.



## 📝 Included Files



- `prompt.zh-CN.md`: Logic correction prompt (Chinese version)

- `prompt.en.md`: Logic correction prompt (English version)
