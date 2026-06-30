# 高等数学学习助手 Skill v1.1.0 增强完善 Spec

## Why
当前 SKILL.md（172 行）包含三段完整的 Few-Shot 示例对话，占用了大量篇幅，降低了模型读取核心流程指令的效率。同时缺少错误处理规范和分层学习资源推荐，测试覆盖不足，README 和 CHANGELOG 需要同步更新至 v1.1.0。

## What Changes
- **重构 SKILL.md**：将三段 Few-Shot 示例对话迁移至独立的 `references/examples.md`，SKILL.md 精简至 80-100 行
- **增加错误处理规范**：在 Step 2（院校分级）、Step 3（专业分级）、Step 5（试卷检索）中增加 WebSearch 超时/无结果降级、结果矛盾处理、模糊输入澄清话术
- **创建测试用例目录**：新建 `tests/test-cases.md`，覆盖 8 个典型场景
- **扩充学习资料推荐**：在 Step 6 或 Step 7 中增加按难度评级分层的推荐资源
- **优化 README.md**：增加项目状态徽章、具体贡献指引、Roadmap 章节
- **更新 CHANGELOG.md**：版本号升至 v1.1.0
- **更新 CONTRIBUTING.md**：反映新增的 `references/` 和 `tests/` 目录结构

## Impact
- Affected specs: higher-math-learning-assistant Skill
- Affected code:
  - `.trae/skills/higher-math-learning-assistant/SKILL.md` — **重构（精简 + 增加错误处理 + 资源推荐）**
  - `references/examples.md` — **新增**
  - `tests/test-cases.md` — **新增**
  - `README.md` — **优化**
  - `CHANGELOG.md` — **更新**
  - `CONTRIBUTING.md` — **更新**

## ADDED Requirements

### Requirement: 示例对话迁移
The system SHALL 将 SKILL.md 中三段完整 Few-Shot 示例对话（985 工科、普通本科经管、985 文科）迁移到独立的 `references/examples.md` 文件中。

#### Scenario: 迁移后 SKILL.md 结构
- **THEN** SKILL.md 在 Step 8 之后保留对 references/examples.md 的引用链接
- **THEN** SKILL.md 总体行数控制在 80-100 行

### Requirement: 错误处理规范
The system SHALL 在 SKILL.md 的 Step 2、Step 3、Step 5 中增加明确的错误处理子章节。

#### Scenario: WebSearch 超时/无结果的降级策略
- **WHEN** WebSearch 调用超时或返回空结果
- **THEN** 如实告知用户"网络检索暂时无结果"，采用保守默认值（Tier 3 普通本科/通用规则）
- **THEN** 在结论中标注"默认值（检索不可用）"

#### Scenario: 检索结果相互矛盾
- **WHEN** 同一内容检索到相互矛盾的结果
- **THEN** 优先采信权威来源（教务官网 > 教育论坛 > 个人博客）
- **THEN** 如果无法判断权威性，如实告知用户"检索结果存在矛盾"，采用保守默认值

#### Scenario: 用户输入模糊
- **WHEN** 用户输入类似"某个 211 学校"或"普通一本"等模糊表述
- **THEN** 引导话术示例："请问具体是哪所大学？不同 211 院校的高数难度差异较大，需要具体名称才能精确分析。"

### Requirement: 测试用例目录
The system SHALL 创建 `tests/test-cases.md`，包含至少 8 个典型场景。

#### Scenario: 测试场景覆盖
- **THEN** C9 工科（浙大计算机）— 极高难度
- **THEN** 985 文科（北师大汉语言）— 中等难度
- **THEN** 211 经管（上财金融）— 高难度
- **THEN** 普通本科工科（苏州科技大学机械）— 较低难度
- **THEN** 未知院校（用户输入模糊院校名）— 降级处理
- **THEN** 专科（某职业技术学院）— 低难度
- **THEN** 艺术类（某美院设计专业）— 低难度
- **THEN** 在读期间同步辅导（大二学生反馈进度）— 反馈闭环

### Requirement: 分层学习资源推荐
The system SHALL 在 SKILL.md 的 Step 6 或 Step 7 中增加按难度评级分层的推荐资源。

#### Scenario: 分层推荐内容
- **THEN** 极高/高难度：同济《高等数学》+ 吉米多维奇 + 各校历年真题
- **THEN** 中等难度：同济版 + 同步辅导 + B站/慕课课程推荐
- **THEN** 较低/低难度：经管类/文科类专用教材 + 概念讲解类视频

### Requirement: README 优化
The system SHALL 优化 README.md。

#### Scenario: 增加项目状态徽章
- **THEN** 在 README 顶部增加构建状态、版本号等徽章

#### Scenario: 增加贡献指引
- **THEN** 在"如何贡献"部分增加如何提交新的院校-专业-高数级别映射数据的指引

#### Scenario: 增加 Roadmap 章节
- **THEN** 在 README 中增加"Roadmap"章节，说明后续规划（如：更多院校数据、自适应学习算法、移动端适配等）

### Requirement: CHANGELOG 更新
The system SHALL 更新 CHANGELOG.md 至 v1.1.0。

#### Scenario: v1.1.0 变更记录
- **THEN** 记录 SKILL.md 重构与精简
- **THEN** 记录错误处理规范新增
- **THEN** 记录测试用例目录创建
- **THEN** 记录分层学习资源推荐
- **THEN** 记录 README 优化
- **THEN** 记录 CONTRIBUTING.md 更新

## MODIFIED Requirements

### Requirement: CONTRIBUTING.md 目录结构更新
The system SHALL 更新 CONTRIBUTING.md 中的项目结构说明，反映新增的 `references/` 和 `tests/` 目录。

## REMOVED Requirements
无