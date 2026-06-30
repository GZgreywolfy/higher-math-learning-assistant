# 高等数学学习助手 Skill v1.2.0 核心功能增强 Spec

## Why
当前 SKILL.md 的 Step 2 院校分级和 Step 3 专业判断完全依赖 WebSearch 实时检索，缺乏内置知识库兜底，响应速度慢且易受检索质量影响。同时 MIT 学习方法缺少可操作的落地指引，缺少学习效果评估环节来形成完整的学习闭环。工程化方面缺少 CI 自动检查和手动测试文档。

## What Changes
- **建立内置院校-专业知识库**：新建 `resources/institutions.json` 和 `resources/major-mapping.json`，SKILL.md Step 2/3 改为优先查内置库 → 命中直接使用 → 未命中才走 WebSearch
- **MIT 方法落地细化**：在 SKILL.md 中新增"MIT方法落地映射表"，将四种方法论映射为具体可执行动作
- **增加学习效果评估环节（Step 9）**：2 周后自动出诊断题，按正确率分流继续/复习/重学
- **补充边界场景示例对话**：在 `references/examples.md` 新增医学专业、专科院校、未知院校降级 3 个示例
- **增加手动测试文档**：新建 `.trae/skills/higher-math-learning-assistant/TEST.md`
- **添加 GitHub Actions CI**：新建 `.github/workflows/ci.yml`
- **更新 README 与版本号**：增加"效果评估与动态调优"特性，版本号更新
- **推送至 GitHub**：按 Conventional Commits 规范提交并推送

## Impact
- Affected specs: higher-math-learning-assistant Skill
- Affected code:
  - `.trae/skills/higher-math-learning-assistant/resources/institutions.json` — **新增**
  - `.trae/skills/higher-math-learning-assistant/resources/major-mapping.json` — **新增**
  - `.trae/skills/higher-math-learning-assistant/SKILL.md` — **重构（内置库优先+MIT细化+Step 9）**
  - `references/examples.md` — **扩充（新增 3 个示例）**
  - `.trae/skills/higher-math-learning-assistant/TEST.md` — **新增**
  - `.github/workflows/ci.yml` — **新增**
  - `README.md` — **更新**
  - `CHANGELOG.md` — **更新**

## ADDED Requirements

### Requirement: 内置院校库
The system SHALL 创建 `resources/institutions.json`，包含常见院校到层次档位的映射表。

#### Scenario: 文件结构与内容
- **THEN** JSON 文件包含字段：`institution`（院校名称）、`tier`（档位 Tier1+/1/2/3/4）、`level`（层次描述 C9/985/211/普通本科/专科）、`score`（分值 5/4/3/2/1）
- **THEN** 至少包含 50 所常见院校映射数据，覆盖 C9、985、211、普通本科、专科各档
- **THEN** 文件格式合法，可通过 JSON 解析器校验

### Requirement: 内置专业库
The system SHALL 创建 `resources/major-mapping.json`，包含常见专业到高数级别的映射表。

#### Scenario: 文件结构与内容
- **THEN** JSON 文件包含字段：`major`（专业名称）、`category`（专业类别）、`level`（高数级别 A/B/C/D）、`coefficient`（系数）
- **THEN** 至少覆盖工科、理科、经管、文科/社科、医学/药学、农学、艺术/体育七大类常见专业
- **THEN** 文件格式合法，可通过 JSON 解析器校验

### Requirement: SKILL.md 内置库优先逻辑
The system SHALL 修改 SKILL.md 的 Step 2 和 Step 3 逻辑，改为内置库优先。

#### Scenario: Step 2 内置库优先流程
- **WHEN** 用户输入院校名称
- **THEN** 优先在 `institutions.json` 中匹配
- **THEN** 命中则直接使用档位和分值（标注"已知库匹配"）
- **THEN** 未命中才走 WebSearch 降级流程

#### Scenario: Step 3 内置库优先流程
- **WHEN** 用户输入专业名称
- **THEN** 优先在 `major-mapping.json` 中匹配
- **THEN** 命中则直接使用高数级别和系数
- **THEN** 未命中则基于专业类别通用规则判断

### Requirement: MIT 方法落地映射表
The system SHALL 在 SKILL.md 中新增"MIT方法落地映射表"章节，将四种方法论映射为具体可执行动作。

#### Scenario: 映射表内容
- **THEN** 主动学习 → 每日"输出练习"：每节结束后做 3 道闭卷题
- **THEN** 费曼技巧 → 每章结束后"复述挑战"：用大白话解释核心定理
- **THEN** 间隔复习 → 复习提醒时间表：第 1/3/7/14 天
- **THEN** 分块学习 → 每日学习分块：45min × 3 块，每块后休息 5min

### Requirement: 学习效果评估环节（Step 9）
The system SHALL 新增 Step 9 学习效果评估环节。

#### Scenario: 评估流程
- **WHEN** 用户学习 2 周后
- **THEN** AI 自动出 5 道本章节诊断题
- **THEN** 根据正确率分流：≥80% → 继续；60-80% → 复习；<60% → 重学
- **THEN** README 核心特性列表同步增加"效果评估与动态调优"

### Requirement: 补充边界场景示例对话
The system SHALL 在 `references/examples.md` 中新增 3 个示例对话。

#### Scenario: 新增示例
- **THEN** 示例 4：医学专业（中山大学临床医学）— 高数B/C+985
- **THEN** 示例 5：专科院校（广东某职业技术学院电子商务）— 低难度+专科
- **THEN** 示例 6：未知院校降级（新成立民办本科数据科学）— WebSearch 查证+置信度标注完整流程

### Requirement: 手动测试文档
The system SHALL 创建 `.trae/skills/higher-math-learning-assistant/TEST.md`。

#### Scenario: 测试文档内容
- **THEN** 包含 10 个以上测试用例
- **THEN** 覆盖不同院校层次、专业类型、边界场景
- **THEN** 每个用例包含预期触发方式、预期输出格式检查点
- **THEN** 包含回归测试检查清单

### Requirement: GitHub Actions CI
The system SHALL 创建 `.github/workflows/ci.yml`。

#### Scenario: CI 检查项
- **THEN** 检查 SKILL.md frontmatter 格式（name + description）
- **THEN** 检查 JSON 文件格式是否合法
- **THEN** 检查文档链接是否有效

### Requirement: 提交与推送
The system SHALL 按 Conventional Commits 规范提交并推送到 GitHub。

#### Scenario: 提交记录
- **THEN** `feat: 增加内置院校-专业知识库`
- **THEN** `feat: MIT学习方法落地细化与效果评估机制`
- **THEN** `docs: 补充边界场景示例对话与测试文档`
- **THEN** `ci: 添加 GitHub Actions CI`
- **THEN** `chore: bump version to v1.2.0`
- **THEN** 推送到远程仓库 main 分支

## MODIFIED Requirements

### Requirement: README.md 更新
The system SHALL 更新 README.md。
- **THEN** 在"核心特性"中增加"效果评估与动态调优"
- **THEN** 在"功能模块说明"表格中增加"学习效果评估"行
- **THEN** CHANGELOG 添加 v1.2.0 变更记录

## REMOVED Requirements
无