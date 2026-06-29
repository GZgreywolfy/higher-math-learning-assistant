# 高等数学学习助手 Skill 完善重构 Spec

## Why
现有 SKILL.md 已具备基础功能，但院校分级缺少"无法识别院校"的稳健降级逻辑，综合难度评估缺乏量化打分模型，试卷检索缺少可信度判别标准，且缺少 few-shot 示例对话来稳定模型输出质量。同时工程化文档（README、LICENSE、CONTRIBUTING、CHANGELOG）缺失，需要补齐。

## What Changes
- **重构 SKILL.md**：完善院校分级降级逻辑、引入量化打分模型、增加培养方案校验步骤、增设检索结果可信度判别、新增反馈闭环、补充 few-shot 示例对话
- **重写 README.md**：包含项目简介、导入使用步骤、目录结构、使用示例、功能模块说明、免责声明
- **新增 LICENSE（MIT）、.gitignore、CONTRIBUTING.md、CHANGELOG.md**
- **同步修正 tasks.md 检查状态**
- **创建 v1.0.0 Release/Tag** 并推送到远程仓库

## Impact
- Affected specs: higher-math-learning-assistant Skill
- Affected code:
  - `.trae/skills/higher-math-learning-assistant/SKILL.md` — **重写主体**
  - `README.md` — **重写**
  - `LICENSE` — **新增**
  - `.gitignore` — **新增**
  - `CONTRIBUTING.md` — **新增**
  - `CHANGELOG.md` — **新增**
  - `.trae/specs/refine-higher-math-learning-skill/tasks.md` — **新增**
  - `.trae/specs/refine-higher-math-learning-skill/checklist.md` — **新增**

## ADDED Requirements

### Requirement: 院校分级 — 无法识别院校时的处理流程
The system SHALL 在无法识别院校时，优先使用 WebSearch 查询该校层次与高考录取分数线，再给出带置信度标注的估算。

#### Scenario: 用户输入的院校不在已知列表中
- **WHEN** 系统无法直接确定院校层次
- **THEN** 使用 WebSearch 检索 "\{院校名称\} 是 \{985/211/双一流\} 吗" 和 "\{院校名称\} 高考录取分数线"
- **THEN** 根据检索结果标注置信度（高/中/低），例如 "根据网络检索，XX大学属于普通一本院校（置信度：高）"
- **THEN** 禁止直接编造，若检索无果则如实告知用户并提供通用参考

### Requirement: 量化打分模型
The system SHALL 将综合难度评估改为可操作的量化打分模型。

#### Scenario: 分值映射
- **THEN** 院校档位分值：Tier1+=5, Tier1=4, Tier2=3, Tier3=2, Tier4=1
- **THEN** 专业系数：高数A=1.0, 高数B=0.8, 高数C=0.6, 高数D=0.4
- **THEN** 总分 = 院校分值 × 专业系数
- **THEN** 总分 → 难度评级：≥4.5 → 极高, ≥3.5 → 高, ≥2.5 → 中等, ≥1.5 → 较低, <1.5 → 低

### Requirement: 专业分级 — 培养方案校验
The system SHALL 增加"以院校实际培养方案为准"的校验步骤。

#### Scenario: 培养方案检索
- **WHEN** 根据专业类别得到默认高数级别后
- **THEN** 使用 WebSearch 检索 "\{院校\} \{专业\} 培养方案 高等数学 学分" 来修正默认映射
- **THEN** 在结论中标注信息来源（"基于默认规则"或"基于\{来源\}培养方案"）

### Requirement: 试卷检索 — 可信度判别与降级
The system SHALL 增加检索结果可信度判别标准。

#### Scenario: 可信度评估
- **WHEN** 检索到试卷信息
- **THEN** 判断来源：教务官网/权威教辅 > 教育论坛 > 个人博客/自媒体
- **THEN** 判断年份：近3年内 +1分，3-5年 +0分，>5年 -1分
- **THEN** 输出时标注可信度（高/中/低）

#### Scenario: 低可信/检索失败
- **WHEN** 检索失败或可信度低
- **THEN** 降级为基于院校档位+专业级别的通用题型预估
- **THEN** 所有真题分析标注"基于网络检索，仅供参考，以开学后教师公布为准"

### Requirement: 反馈闭环
The system SHALL 新增"计划执行追踪"环节。

#### Scenario: 学生反馈进度
- **WHEN** 学生在执行计划后反馈已完成某阶段进度
- **THEN** 系统根据反馈动态修订后续阶段计划（加速/减速/补充薄弱环节）

### Requirement: Few-shot 示例对话
The system SHALL 在 SKILL.md 中补充 2-3 段完整示例对话。

#### Scenario: 典型场景覆盖
- **THEN** 包含"985工科"场景（极高难度，从高考后立即开始预习）
- **THEN** 包含"普通本科经管"场景（中等难度，按部就班）
- **THEN** 包含"文科"场景（较低难度，侧重基础概念）

### Requirement: 工程化文档
The system SHALL 创建完整的工程化文档。

#### Scenario: README.md
- **THEN** 包含项目简介、导入 Trae 使用步骤、目录结构说明、完整使用示例（含示例对话）、功能模块说明、免责声明

#### Scenario: LICENSE
- **THEN** 使用 MIT 协议

#### Scenario: .gitignore
- **THEN** 忽略 .DS_Store、临时文件、node_modules、__pycache__、*.log 等

#### Scenario: CONTRIBUTING.md
- **THEN** 包含贡献指南、PR 流程、代码规范

#### Scenario: CHANGELOG.md
- **THEN** 包含版本记录，初始版本 v1.0.0

### Requirement: 提交规范
The system SHALL 按 Conventional Commits 规范提交，创建 v1.0.0 Release/Tag，推送 main 分支。

#### Scenario: 提交与发布
- **THEN** 使用 feat:、docs:、refactor: 等语义化前缀
- **THEN** 创建 v1.0.0 Git Tag
- **THEN** 创建 GitHub Release v1.0.0
- **THEN** 推送到原远程仓库 main 分支

## REMOVED Requirements
无
