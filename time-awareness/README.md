# Time Awareness (时间感知)

简体中文 | [English](#english-version)

这个目录下的 Prompt 旨在为大模型添加一层“时间感知”机制。核心指令只有一句话：“每次对话前，主动查询一次当前时间”。

## 📖 产生背景与作用

对于指令遵守较好的模型（即不会虚空编造时间的模型），引入这条时间查询指令后，模型对连续对话中的时间节点会更加敏感。

当模型对事件的先后顺序和时长有了清晰的概念之后，能够得出更加合理的推理。时间维度的输入能让模型具备更好的交互和理解能力，从而在需要时间动态评估的场景下（例如日程安排、数据时效性分析、事件追踪等）表现得更加可靠。

## 📝 包含的文件

- `prompt.zh-CN.md`: 时间感知提示词（中文版）
- `prompt.en.md`: 时间感知提示词（英文版）

---
---

<a id="english-version"></a>

# Time Awareness

[简体中文](#time-awareness-时间感知) | English

The prompts in this directory are designed to add a "time awareness" mechanism to Large Language Models. The core instruction is just one sentence: "Before each conversation, actively query the current time once."

## 📖 Background & Purpose

For models with good instruction-following capabilities (i.e., those that do not hallucinate times), introducing this time-querying instruction makes the model more sensitive to time nodes in continuous conversations.

Once the model has a clear concept of chronological order and duration of events, it can draw more reasonable inferences. The input of the time dimension gives the model better interactive and comprehension skills, making it much more reliable in scenarios requiring dynamic time evaluation (such as scheduling, data timeliness analysis, event tracking, etc.).

## 📝 Included Files

- `prompt.zh-CN.md`: Time awareness prompt (Chinese version)
- `prompt.en.md`: Time awareness prompt (English version)
