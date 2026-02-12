# AI Agent 团队协作系统

## 项目概述

这是一个用于构建临时 AI Agent 团队协作的系统。该系统预设了多个不同职能的 AI Agent，每个 Agent 都融合了著名专家的思维模型，可以在复杂任务中组建专业团队进行协作。

## 项目结构

```
├── settings.json                    # Claude Code 配置，启用 Agent Teams 功能
├── skills/
│   └── team/
│       └── SKILL.md                 # 团队组建技能定义
└── agents/                          # Agent 定义文件目录
    ├── ceo-bezos.md                 # CEO（Jeff Bezos 思维模型）
    ├── cto-vogels.md                # CTO（Werner Vogels 思维模型）
    ├── product-norman.md            # 产品设计（Don Norman 思维模型）
    ├── ui-duarte.md                 # UI 设计（Matías Duarte 思维模型）
    ├── interaction-cooper.md        # 交互设计（Alan Cooper 思维模型）
    ├── fullstack-dhh.md             # 全栈开发（DHH 思维模型）
    ├── qa-bach.md                   # QA（James Bach 思维模型）
    ├── marketing-godin.md           # 营销（Seth Godin 思维模型）
    ├── operations-pg.md             # 运营（Paul Graham 思维模型）
    └── sales-ross.md                # 销售（Aaron Ross 思维模型）
```

## 核心配置

### settings.json

```json
{
  "permissions": {
    "defaultMode": "bypassPermissions",
    "allow": ["WebSearch", "Bash", "Edit", "Write", "WebFetch", "NotebookEdit", "Skill"],
    "ask": [],
    "deny": []
  },
  "env": {
    "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1"
  },
  "enableAllProjectMcpServers": true
}
```

这个配置文件启用了实验性的 Agent Teams 功能，允许创建和管理临时 AI 团队。

## Agent 团队成员

### 战略层

| Agent | 思维模型 | 核心职能 |
|-------|---------|---------|
| [CEO](agents/ceo-bezos.md) | Jeff Bezos | 战略决策、商业模式、PR/FAQ、优先级排序 |
| [CTO](agents/cto-vogels.md) | Werner Vogels | 技术架构、技术选型、系统性能评估 |

### 产品设计层

| Agent | 思维模型 | 核心职能 |
|-------|---------|---------|
| [产品设计](agents/product-norman.md) | Don Norman | 产品定义、用户体验、可用性分析 |
| [UI 设计](agents/ui-duarte.md) | Matías Duarte | 视觉设计、设计系统、配色排版 |
| [交互设计](agents/interaction-cooper.md) | Alan Cooper | 用户流程、Persona 定义、交互模式 |

### 技术实现层

| Agent | 思维模型 | 核心职能 |
|-------|---------|---------|
| [全栈开发](agents/fullstack-dhh.md) | DHH | 代码实现、技术方案、开发效率 |
| [QA](agents/qa-bach.md) | James Bach | 测试策略、质量把控、Bug 分析 |

### 商业运营层

| Agent | 思维模型 | 核心职能 |
|-------|---------|---------|
| [营销](agents/marketing-godin.md) | Seth Godin | 定位、品牌、获客、内容策略 |
| [运营](agents/operations-pg.md) | Paul Graham | 用户运营、增长、社区、PMF |
| [销售](agents/sales-ross.md) | Aaron Ross | 定价、销售漏斗、转化优化 |

## 工作流程

### 1. 任务分析

当接收到任务时，系统会根据任务性质选择 2-5 个最相关的 Agent 组成团队。选择原则：
- **只选必要的**：精准匹配任务需求
- **考虑协作链**：确保关键角色都在
- **避免冗余**：不选择职能重叠的 Agent

### 2. 团队组建

系统会：
1. 为团队创建简短的英文名称（kebab-case 格式）
2. 为每个成员创建具体任务描述
3. 使用 Agent Teams 功能创建临时团队
4. 各成员在 `docs/<role>/` 目录下产出文档

### 3. 协调与汇总

- Team Lead 协调各成员工作
- 收集并汇总产出文档
- 如有分歧，列出各方观点供决策
- 任务完成后解散临时团队

## 文档存放规范

每个 Agent 有指定的文档存放目录：

| Agent | 目录 |
|-------|------|
| CEO | `docs/ceo/` |
| CTO | `docs/cto/` |
| 产品设计 | `docs/product/` |
| UI 设计 | `docs/ui/` |
| 交互设计 | `docs/interaction/` |
| 全栈开发 | `docs/fullstack/` |
| QA | `docs/qa/` |
| 营销 | `docs/marketing/` |
| 运营 | `docs/operations/` |
| 销售 | `docs/sales/` |

## 沟通规范

- 所有沟通使用**中文**
- 技术术语保留**英文**
- 创始人是最终决策者，Agent 提供建议但不替代决策
- 团队是临时的，任务完成后即解散

## 使用场景示例

### 示例 1：新产品立项

当需要评估新产品想法时，可能的团队配置：
- CEO（Jeff Bezos）：评估商业模式和优先级
- 产品设计（Don Norman）：定义产品需求
- 营销（Seth Godin）：制定定位策略

### 示例 2：技术架构设计

当需要设计系统架构时，可能的团队配置：
- CTO（Werner Vogels）：技术架构设计
- 全栈开发（DHH）：技术方案评估
- QA（James Bach）：制定测试策略

### 示例 3：产品发布准备

当准备发布产品时，可能的团队配置：
- CEO（Jeff Bezos）：PR/FAQ 审核
- UI/交互设计：最终界面检查
- 全栈开发：技术实现确认
- QA：发布前质量检查
- 营销：发布策略制定

## 设计理念

### 思维模型

每个 Agent 都融合了一位真实专家的思维模型，这些专家在各自领域有深刻见解：
- **Jeff Bezos**：长期主义、客户至上、飞轮效应
- **Werner Vogels**：Everything Fails、You Build It You Run It
- **Don Norman**：以人为本、可供性、心智模型
- **DHH**：简洁、开发者幸福感、Majestic Monolitheth Godin**：
- **S紫牛、许可营销部落理论
- **James Bach**：探索性测试、上下文驱动测试

### 决策框架

每个 Agent 都有清晰的决策框架，确保输出的一致性和专业性。

### 务实原则

- 独立开发者的建议与大型团队不同
- 强调简单性和可执行性
- 警惕过度工程化

## 扩展说明

### 添加新 Agent

如需添加新的 Agent 角色：
1. 在 `agents/` 目录下创建新的 `.md` 文件
2. 参考现有 Agent 文件的结构定义 Role、Persona、Core Principles 等
3. 在 `skills/team/SKILL.md` 的表格中添加新 Agent

### 修改团队行为

如需调整团队协作流程，修改 `skills/team/SKILL.md` 中的执行步骤。
