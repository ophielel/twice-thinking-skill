# Twice-Thinking Skill 集成指南

## 集成方式总览

Twice-Thinking Skill 可以通过多种方式集成到 AI 系统中：

1. **System Prompt** - 最简单，任何 AI 都能用
2. **Claude Agent** - 官方 Agent SDK
3. **OpenAI Agents** - OpenAI 的 Agent 框架
4. **LangChain/LangGraph** - 第三方编排框架
5. **自定义实现** - 在自己的代码库中实现

---

## 方式1：System Prompt 集成（推荐）

### 适用场景
任何支持 system prompt 的 AI 工具

### 配置示例

```
# System Prompt 部分

## Twice-Thinking Skill 配置

当用户提出以下类型的需求时，启用 Twice-Thinking 模式：

### 触发条件
用户请求包含以下关键词时启动：
- "开发"、"写"、"做"、"创建"、"build"、"implement" - 创建类
- "修改"、"改"、"更新"、"优化"、"fix"、"refactor" - 修改类
- "学习"、"了解"、"教"、"explain" - 学习类
- "集成"、"连接"、"对接" - 集成类
- "分析"、"看"、"检查"、"review" - 分析类

### 处理流程

```
步骤1: 需求分析
用户说：{用户原始请求}

你需要：
1. 识别这是一个什么类型的需求（创建/修改/学习/集成/分析）
2. 识别这个请求中有哪些模糊点、歧义表达
3. 确定需要追问的维度（从以下7个维度中选择）
4. 生成3-5个追问问题

追问维度清单：
- 目标确认
- 使用场景
- 功能范围
- 技术细节
- 用户体验
- 边界条件
- 成功标准

追问要求：
- 每次只问1-2个问题
- 问题要具体、有针对性
- 避免用户回答"随便"
- 记录用户的回答

步骤2: 追问跟进
重复以下过程，直到：
- 7个维度都已覆盖，或
- 用户主动说"差不多就这样"、"先这样"，或
- 用户说"我先开始做，遇到问题再说"

步骤3: 需求总结
生成需求文档，格式如下：

# [项目类型] 需求文档

## 1. 基本信息
- 需求类型: 创建/修改/学习/集成/分析
- 迭代次数: N
- 澄清日期: YYYY-MM-DD

## 2. 原始需求
> 用户的原始请求

## 3. 需求理解
### 3.1 主要目标
[描述用户真正想解决的问题]

### 3.2 目标用户
- 用户角色: ...
- 预期规模: ...
- 使用频率: ...

### 3.3 功能范围
#### 必须实现
- 功能1: ...
- 功能2: ...

#### 可选功能
- 功能1: ...
- 功能2: ...

#### 明确不做的
- 功能1: ...
- 功能2: ...

### 3.4 技术要求
- 技术栈: ...
- 集成要求: ...
- 数据格式: ...
- 环境要求: ...

### 3.5 用户体验
- 界面风格: ...
- 操作流程: ...
- 性能要求: ...
- 兼容性: ...

### 3.6 边界条件
- 性能指标: ...
- 安全考虑: ...
- 扩展性: ...
- 合规性: ...

### 3.7 成功标准
- 功能完整性: ...
- 用户体验指标: ...
- 性能标准: ...
- 测试要求: ...

## 4. 已澄清的关键点
- 维度1: [内容]
- 维度2: [内容]
- ...

## 5. 对话历史
### 迭代1
- 问题: ...
- 回答: ...

### 迭代2
- 问题: ...
- 回答: ...

...

## 6. 下一步建议
1. 开始需求文档细化
2. 进行技术方案设计
3. 开始开发实现

### 输出示例
```
# 效率工具应用 需求文档

## 1. 基本信息
- 需求类型: 创建
- 迭代次数: 5
- 澄清日期: 2025-02-15

## 2. 原始需求
> 开发一个团队用的效率工具，桌面应用

## 3. 需求理解
### 3.1 主要目标
帮助5-10人的团队提高项目管理效率，支持文档协作和数据同步。

### 3.2 目标用户
- 用户角色: 企业团队（5-10人）
- 预期规模: 小型团队，日常使用
- 使用频率: 每天多次，高频使用

### 3.3 功能范围
#### 必须实现
- 项目任务管理（创建、分配、跟踪）
- 文档协作（创建、编辑、共享）
- 数据同步（Office格式）
- SharePoint集成

#### 可选功能
- 实时协作
- 离线模式
- 版本历史

#### 明确不做的
- 复杂权限管理
- 多级审批流程

## 4. 已澄清的关键点
- 目标确认: 提高团队效率
- 使用场景: 项目管理和文档协作
- 功能范围: 任务管理、文档协作、数据同步
- 技术细节: 桌面应用，Office格式，SharePoint集成
- 用户体验: 现代简约
- 边界条件: 5-10人团队
- 成功标准: 支持基础CRUD

## 5. 对话历史
### 迭代1
- 问题: 这个应用主要解决什么问题？是提高效率还是解决具体痛点？
- 回答: 提高团队效率，主要是项目管理

### 迭代2
- 问题: 目标用户是谁？有多少人？
- 回答: 5-10人，企业团队

...

## 6. 下一步建议
1. 绘制信息架构图
2. 设计数据模型
3. 编写技术方案文档
4. 搭建开发框架
```

### 优势
- 配置简单，一条 system prompt 就能启用
- 不需要额外的服务或框架
- 适用于任何 AI

---

## 方式2：Claude Agent SDK 集成

### 适用场景
在 Claude Agent 生态中使用

### 代码结构

```
twice_thinking/
├── agent/
│   ├── __init__.py
│   ├── skill.py           # Twice-Thinking Skill 实现
│   └── models.py          # 数据模型
├── prompts/
│   └── system.yaml       # System prompt 模板
├── tests/
│   └── test_skill.py      # 测试
└── pyproject.toml
```

### Agent 实现（伪代码）

```python
# agent/skill.py

from typing import Dict, List, Optional
from dataclasses import dataclass
from enum import Enum

class RequirementType(Enum):
    CREATE = "创建"
    MODIFY = "修改"
    LEARN = "学习"
    INTEGRATE = "集成"
    ANALYZE = "分析"

class QuestionDimension(Enum):
    GOAL = "目标确认"
    SCENARIO = "使用场景"
    SCOPE = "功能范围"
    TECHNICAL = "技术细节"
    USER_EXPERIENCE = "用户体验"
    BOUNDARY = "边界条件"
    SUCCESS = "成功标准"

@dataclass
class ConversationState:
    """对话状态"""
    session_id: str
    user_request: str
    requirement_type: RequirementType
    current_dimension: QuestionDimension
    clarified_aspects: Dict[str, str]
    questions_asked: List[Dict]
    iteration_count: int
    status: str  # analyzing|clarifying|complete

class TwiceThinkingAgent:
    """Twice-Thinking Agent 实现"""

    def __init__(self):
        self.sessions: Dict[str, ConversationState] = {}

    def analyze_requirement(self, user_request: str) -> ConversationState:
        """
        分析需求，生成初始追问计划
        """
        session_id = self._generate_session_id(user_request)

        # 识别需求类型
        req_type = self._detect_requirement_type(user_request)

        # 识别模糊点
        ambiguities = self._detect_ambiguities(user_request)

        # 确定需要追问的维度
        dimensions = self._select_dimensions(req_type, ambiguities)

        # 生成初始问题（3-5个）
        initial_questions = self._generate_questions(req_type, dimensions)

        state = ConversationState(
            session_id=session_id,
            user_request=user_request,
            requirement_type=req_type,
            current_dimension=dimensions[0],
            clarified_aspects={},
            questions_asked=[],
            iteration_count=0,
            status="clarifying"
        )

        self.sessions[session_id] = state
        return state

    def follow_up(self, session_id: str, answer: str) -> Dict:
        """
        处理用户回答，生成下一轮追问或总结
        """
        if session_id not in self.sessions:
            return {"error": "Session not found"}

        state = self.sessions[session_id]

        # 记录回答
        current_question = state.questions_asked[-1]
        state.clarified_aspects[current_question['dimension']] = answer

        # 判断是否需要继续追问
        if self._should_continue_clarifying(state):
            # 生成下一轮问题（1-2个）
            next_questions = self._generate_next_questions(state)
            state.questions_asked.extend(next_questions)
            state.iteration_count += 1
            state.status = "clarifying"
            return {
                "action": "continue",
                "questions": next_questions,
                "iteration": state.iteration_count
            }
        else:
            # 生成需求总结
            summary = self._generate_summary(state)
            state.status = "complete"
            return {
                "action": "complete",
                "summary": summary
            }

    def _detect_requirement_type(self, request: str) -> RequirementType:
        """检测需求类型"""
        keywords = {
            RequirementType.CREATE: ["创建", "开发", "写", "做", "build", "implement"],
            RequirementType.MODIFY: ["修改", "改", "更新", "优化", "fix", "refactor"],
            RequirementType.LEARN: ["学习", "了解", "教", "explain", "告诉"],
            RequirementType.INTEGRATE: ["集成", "连接", "对接", "接"],
            RequirementType.ANALYZE: ["分析", "看", "检查", "review"]
        }

        for req_type, keywords_list in keywords.items():
            if any(keyword in request for keyword in keywords_list):
                return req_type

        return RequirementType.CREATE  # 默认

    def _detect_ambiguities(self, request: str) -> List[str]:
        """检测模糊点"""
        ambiguities = []
        if "这个" in request:
            ambiguities.append("'这个'指代不明确")
        if "那" in request:
            ambiguities.append("'那'指代不明确")
        if "应用" in request and ("什么" not in request and "具体" not in request):
            ambiguities.append("应用类型不明确")
        if "工具" in request and ("功能" not in request):
            ambiguities.append("功能范围不明确")
        return ambiguities

    def _select_dimensions(self, req_type: RequirementType, ambiguities: List[str]) -> List[QuestionDimension]:
        """选择需要追问的维度"""
        dimensions = []

        # 基础维度（总是需要）
        dimensions.extend([
            QuestionDimension.GOAL,
            QuestionDimension.SCENARIO,
            QuestionDimension.SCOPE
        ])

        # 根据类型和模糊点选择额外维度
        if req_type in [RequirementType.CREATE, RequirementType.MODIFY]:
            dimensions.extend([
                QuestionDimension.TECHNICAL,
                QuestionDimension.USER_EXPERIENCE
            ])
        if "工具" in self._accumulated_request or "系统" in self._accumulated_request:
            dimensions.append(QuestionDimension.BOUNDARY)

        return dimensions

    def _should_continue_clarifying(self, state: ConversationState) -> bool:
        """判断是否应该继续追问"""
        # 检查7个维度是否都覆盖
        covered_dimensions = set()
        for q in state.questions_asked:
            covered_dimensions.add(q['dimension'])

        required_dimensions = {
            QuestionDimension.GOAL, QuestionDimension.SCENARIO, QuestionDimension.SCOPE
        }

        return len(covered_dimensions) < len(required_dimensions) and state.iteration_count < 10

    def _generate_summary(self, state: ConversationState) -> str:
        """生成需求总结（markdown格式）"""
        # 实现略...按照 SKILL_MANIFEST.md 中的格式生成
        pass
```

### 配置示例

```json
{
  "agent_name": "twice-thinking",
  "description": "深度需求追问 Agent",
  "tools": [
    {
      "name": "analyze_requirement",
      "description": "分析用户需求"
    },
    {
      "name": "follow_up",
      "description": "记录回答并继续追问"
    },
    {
      "name": "get_summary",
      "description": "获取需求总结"
    }
  ]
}
```

---

## 方式3：OpenAI Agents 集成

### 适用场景
OpenAI Assistants API 和 GPT Agents

### 实现要点

将 Twice-Thinking 包装成一个 Function Calling：

```json
{
  "type": "function",
  "function": {
    "name": "twice_thinking_analyze",
    "description": "分析需求并生成追问计划",
    "parameters": {
      "type": "object",
      "properties": {
        "user_request": {
          "type": "string",
          "description": "用户的原始需求"
        }
      },
      "required": ["user_request"]
    }
  }
}
```

---

## 最佳实践

1. **状态管理**：使用持久化存储会话状态，避免重启丢失
2. **错误处理**：当用户回答不相关时，重新提问
3. **超时处理**：会话超过一定时间自动关闭
4. **会话管理**：支持多个并发会话
5. **日志记录**：记录完整对话历史，便于回溯
6. **用户反馈**：在需求总结后收集用户确认
7. **迭代改进**：根据实际使用反馈调整追问策略
