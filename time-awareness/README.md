# Time Awareness (时间感知)

简体中文 | [English](#english-version)

这个目录下的 Prompt 旨在为大模型添加一层“时间感知”机制。核心指令只有一句话：“每次对话前，主动查询一次当前时间”。

## 📖 产生背景与作用

对于指令遵守较好的模型（即不会虚空编造时间的模型），引入这条时间查询指令后，模型对连续对话中的时间节点会更加敏感。

当模型有了时间的参照，不仅能对事件的先后顺序和时长有更加清晰的概念，而且能有效避免“时空错乱”的问题：**当模型不知道时间时，常常会把过去的事情和当前的事情混在一个优先级去讨论，或者不知道主动查询最新的信息，而是把过去的事情当现在来讨论**。实时的“时间戳”会修正这一错觉。（即使底层系统可能已经隐式地注入了时间或地理位置等元数据，在缺乏明确意图指向时，这些信息也很容易被模型的注意力机制所忽略，因此显式的时间查询依然必要。）

此外，引入时间维度的输入能让模型具备更好的交互和理解能力，使其在需要时间动态评估的场景下（例如日程安排、数据时效性分析、事件追踪等）表现得更加可靠。**我们推测，在最新的 Claude 4.6 模型中，也已经在底层引入了类似对时间的感知机制。**

## 🔬 实验与观察

我们在实际测试中得到了一些有趣的观察结果（详细日志请见 [`experiment-log.md`](experiment-log.md)）：

1. **元数据唤醒**：模型往往不需要高成本地调用外部 Function Call 获取时间，底层系统通常会隐式注入时空快照。该 Prompt 的作用本质上是“唤醒”了模型对这些元数据的注意力权重。
2. **Logit 采样幻觉带来的时间漂移**：在连续的大上下文对话中，模型有时会产生向未来的“时间漂移”。这很可能是拟人化的伪随机采样（Temperature > 0）在复杂上下文干扰下引发的采样幻觉，并非简单的系统 Bug。

## 📝 包含的文件

- `prompt.zh-CN.md`: 时间感知提示词（中文版）
- `prompt.en.md`: 时间感知提示词（英文版）
- `experiment-log.md`: 实验日志与深入分析

---
---

<a id="english-version"></a>

# Time Awareness

[简体中文](#time-awareness-时间感知) | English

The prompts in this directory are designed to add a "time awareness" mechanism to Large Language Models. The core instruction is just one sentence: "Before each conversation, actively query the current time once."

## 📖 Background & Purpose

For models with good instruction-following capabilities (i.e., those that do not hallucinate times), introducing this time-querying instruction makes the model more sensitive to time nodes in continuous conversations.

When the model has a temporal reference, it not only gains a clearer concept of the chronological order and duration of events but also effectively avoids the issue of "temporal confusion": **without knowing the current time, models often discuss past and present events with the same priority, or fail to actively query the latest information, treating outdated events as current.** A real-time "timestamp" corrects this illusion. (Even if underlying systems might have implicitly injected metadata like time or geolocation, this information is easily ignored by the model's attention mechanism lacking clear intent directives, making explicit time querying necessary.)

Furthermore, the input of the time dimension significantly enhances the model's interactive and comprehension skills, making it much more reliable in scenarios requiring dynamic time evaluation (such as scheduling, data timeliness analysis, event tracking, etc.). **We hypothesize that the latest Claude 4.6 model has also incorporated a similar underlying time-awareness mechanism.**

## 🔬 Experiments & Observations

We gathered some interesting insights during practical testing (detailed logs available in [`experiment-log.md`](experiment-log.md)):

1. **Metadata Awakening**: Models often do not need costly external Function Calls to get time; underlying systems typically inject a space-time snapshot. The prompt essentially "awakens" the model's attention weight towards this metadata.
2. **Time Drift via Logit Sampling Hallucination**: In continuous conversations with long contexts, models occasionally produce a "time drift" towards the future. This is highly likely a result of pseudo-random sampling (Temperature > 0) causing hallucinations under complex context interference, rather than a bug in time acquisition.

## 📝 Included Files

- `prompt.zh-CN.md`: Time awareness prompt (Chinese version)
- `prompt.en.md`: Time awareness prompt (English version)
- `experiment-log.md`: Experiment log and analysis
