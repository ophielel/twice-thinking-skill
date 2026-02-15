# Twice-Thinking Agent Skill

[English](#english-version) | [中文](#chinese-version)

---

## 中文版本

> 一个通过多轮追问来深入理解用户需求的 AI Agent Skill。

### 简介

Twice-Thinking 是一个 AI Agent 专用 Skill，通过系统化的多轮追问，将模糊的用户需求转化为清晰、完整、可执行的需求文档。

### 核心理念

在实际开发中，用户的需求往往不够清晰：
- "开发一个应用" - 太笼统
- "做一个工具" - 不知道具体要什么
- "集成某某功能" - 不清楚边界条件

这会导致：
- 需求不明确就开始开发
- 做到一半发现方向错了
- 重复沟通浪费时间

Twice-Thinking 通过 7 个维度的系统化追问，把模糊需求转化成结构化的需求文档。

### 核心特性

- **需求分析** - 识别主要意图、检测模糊点
- **多轮追问** - 每次只问 1-2 个问题
- **需求总结** - 生成规范的需求文档
- **对话记录** - 完整保留所有问答历史
- **7 个维度覆盖** - 目标/场景/功能/技术/用户体验/边界/成功标准

### 追问维度

1. **目标确认** - 用户真正想解决什么问题？达到什么目的？
2. **使用场景** - 在什么场景下使用？有什么约束？
3. **功能范围** - 需要/不需要什么功能？优先级如何？
4. **技术细节** - 技术栈、集成要求、数据格式？
5. **用户体验** - 预期用户角色、使用频率、操作流程？
6. **边界条件** - 性能要求、兼容性、扩展性考虑？
7. **成功标准** - 如何判断需求是否满足？测试验证方式？

### 优势

- 避免因需求不明确导致的返工
- 发现用户自己没考虑到的边界条件
- 通过对话逐步建立信任
- 可追溯的推理过程
- 一次性收集所有必要信息

### 文档结构

```
twice-thinking/
├── skill/
│   ├── SKILL_MANIFEST.md      # Skill 核心设计文档
│   ├── INTEGRATION_GUIDES.md   # 多种集成方式指南
│   └── TEST_EXAMPLES.md       # 完整对话示例
└── README.md                   # 项目说明（本文件）
```

### 集成方式

#### 方式1：System Prompt

在 AI 的 system prompt 中配置触发条件和处理流程。

#### 方式2：Claude Agent SDK

使用官方 Agent SDK 创建自定义 Agent。

#### 方式3：OpenAI Agents

包装为 Function Calling，在 OpenAI Agent 生态中使用。

#### 方式4：LangChain/LangGraph

在第三方编排框架中实现。

### 使用示例

详见 [TEST_EXAMPLES.md](skill/TEST_EXAMPLES.md)

### 贡献

这个 Skill 的设计是开放的，可以根据实际使用反馈持续改进。

### 许可证

本项目采用 WTFPL 许可证（详见项目根目录 LICENSE 文件）。

---

## English Version

> A deep questioning agent skill that clarifies user requirements through multiple rounds of dialogue.

### Introduction

Twice-Thinking is a specialized AI Agent Skill that systematically clarifies ambiguous user requirements through multiple rounds of dialogue, transforming fuzzy user requests into clear, complete, actionable requirement documents.

### Core Concept

In actual development, user requirements are often unclear:
- "Build an app" - too vague
- "Make a tool" - unclear about specifics
- "Integrate X feature" - boundary conditions undefined

This leads to:
- Starting development with unclear requirements
- Discovering wrong direction halfway through
- Wasting time on repeated communication

Twice-Thinking transforms fuzzy requirements into structured requirement documents through systematic multi-round questioning across 7 dimensions.

### Key Features

- **Requirement Analysis** - Identify primary intent, detect ambiguities
- **Multi-round Follow-up** - Ask only 1-2 questions each round
- **Requirement Summary** - Generate standardized requirement documents
- **Conversation History** - Complete record of all Q&A
- **7-Dimension Coverage** - Goal/Scenario/Scope/Tech/UX/Boundary/Success

### Questioning Dimensions

1. **Goal Confirmation** - What problem does the user really want to solve? What purpose to achieve?
2. **Usage Scenario** - In what context? What constraints?
3. **Functional Scope** - Required/not required features? Priority?
4. **Technical Details** - Tech stack, integration requirements, data formats?
5. **User Experience** - Expected user roles, usage frequency, operation flows?
6. **Boundary Conditions** - Performance requirements, compatibility, extensibility?
7. **Success Criteria** - How to judge if requirements are met? Testing methods?

### Advantages

- Avoid rework caused by unclear requirements
- Discover boundary conditions users didn't consider
- Build trust gradually through dialogue
- Traceable reasoning process
- Collect all necessary information at once

### Documentation Structure

```
twice-thinking/
├── skill/
│   ├── SKILL_MANIFEST.md      # Core skill design document
│   ├── INTEGRATION_GUIDES.md   # Multiple integration approaches
│   └── TEST_EXAMPLES.md       # Complete dialogue examples
└── README.md                   # Project description (this file)
```

### Integration Methods

#### Method 1: System Prompt

Configure trigger conditions and processing flow in the AI's system prompt.

#### Method 2: Claude Agent SDK

Create custom agents using the official Agent SDK.

#### Method 3: OpenAI Agents

Wrap as Function Calling for use in the OpenAI Agent ecosystem.

#### Method 4: LangChain/LangGraph

Implement within third-party orchestration frameworks.

### Usage Examples

See [TEST_EXAMPLES.md](skill/TEST_EXAMPLES.md) for details.

### Contributing

This skill's design is open and can be improved based on actual usage feedback.

### License

This project is licensed under WTFPL (see LICENSE file in the project root).

---

## License

```
            DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE
                    Version 2, December 2004

 Copyright (C) 2025 ophielel

 Everyone is permitted to copy and distribute verbatim copies
 of this license document, but changing it is not allowed.

            PREAMBLE

The intent of this license is to promote sharing and use of software
and other works, not to restrict it. This is especially important
for software that was written collaboratively, or where the work is
intended to be a free replacement for something that exists and that has
existing limitations.

We want:
- Tools and other utilities to be available for everyone
- Educational use of tools and software without licensing restrictions

We acknowledge that:
- Some people and organizations might want to restrict or control
- This license does not enforce any particular restrictions

Therefore:

- Everyone can use this work for any purpose
- No warranties or guarantees are provided
- Attribution is appreciated but not required

            TERMS AND CONDITIONS

0. You just DO WHAT THE FUCK YOU WANT TO.

   1. You CAN copy and distribute this software
   2. You CAN modify this software
   3. You CAN use this software for any purpose
   4. You CAN sell this software
   5. You CAN do whatever you want

That's it. Have fun!
```
