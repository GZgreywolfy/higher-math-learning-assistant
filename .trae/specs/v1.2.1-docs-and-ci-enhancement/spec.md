# 文档完善与自动化验证 v1.2.1 Spec

## Why
当前项目缺少更精细的验证工作流（仅 basic CI）、README 缺少演示章节和 FAQ、评分模型缺少独立文档、测试用例覆盖不全，需要系统性地完善文档与 CI 体系，并推送至 GitHub 发布 Release。

## What Changes
- **新增 validate-skill.yml 工作流**：对 SKILL.md 进行 YAML frontmatter 格式校验、必要字段检查、triggers 关键词检查
- **更新 README.md**：新增"实际运行演示"章节（GIF/截图占位）、新增"常见问题 (FAQ)"章节、版本号统一更新为 v1.2.0
- **新增 scoring-model.md**：详细说明院校档位分值表、专业系数表、综合评分与五档难度评级映射
- **扩充 test-cases.md**：新增 4 个测试场景（普通本科+文科、211+经管、未知院校+WebSearch 降级、对话连续性）
- **清理过期 specs**：将 v1.1.0 规格文档移至 archive/ 目录
- **Git 提交与推送**：提交全部变更至 main 分支并推送
- **GitHub Release**：创建 v1.2.1 Release

## Impact
- Affected specs: higher-math-learning-assistant Skill
- Affected code:
  - `.github/workflows/validate-skill.yml` — **新增**
  - `README.md` — **修改**
  - `references/scoring-model.md` — **新增**
  - `tests/test-cases.md` — **修改**
  - `.trae/specs/enhance-skill-v1.1.0/` — **移至 archive/**

## ADDED Requirements

### Requirement: validate-skill.yml 工作流
The system SHALL 创建 `.github/workflows/validate-skill.yml`。

#### Scenario: YAML frontmatter 格式校验
- **WHEN** push 或 PR 到 main 分支
- **THEN** 对 `.trae/skills/higher-math-learning-assistant/SKILL.md` 进行 YAML frontmatter 格式校验
- **THEN** 检查是否包含必要字段：`name`、`description`、`triggers`、`workflow`
- **THEN** 检查 triggers 中是否包含 "帮我学高数"、"高等数学怎么学"、"大一高数预习计划" 等关键词

### Requirement: README.md 更新
The system SHALL 更新 README.md。

#### Scenario: 实际运行演示章节
- **WHEN** 在"使用示例"部分之后
- **THEN** 增加"实际运行演示"章节，预留 GIF/截图位置，添加占位说明

#### Scenario: 常见问题 (FAQ) 章节
- **WHEN** 在文档末尾
- **THEN** 增加"常见问题 (FAQ)"章节，至少包含：
  - Q: Skill 没有自动激活怎么办？
  - Q: AI 不支持 WebSearch 怎么办？
  - Q: 我的院校不在内置库中怎么办？

#### Scenario: 版本号更新
- **THEN** 将版本号统一更新为 v1.2.0
- **THEN** 清理 specs 目录中过期的 v1.1.0 规格文档（移至 archive/ 目录）

### Requirement: scoring-model.md
The system SHALL 在 `references/` 目录下新增 `scoring-model.md`。

#### Scenario: 文件内容
- **THEN** 包含院校档位分值表（C9/985/211/双一流/普通本科/专科 各自的分值）
- **THEN** 包含专业系数表（工科/理科/经管/文科/医学/农学/艺术 各自的系数）
- **THEN** 包含综合评分与五档难度评级的映射关系及阈值

### Requirement: test-cases.md 扩充
The system SHALL 扩充 `tests/test-cases.md`。

#### Scenario: 新增测试场景
- **THEN** 新增"普通本科 + 文科专业 → 低难度"场景
- **THEN** 新增"211院校 + 经管专业 → 中低难度"场景
- **THEN** 新增"未知院校 + WebSearch 降级场景"
- **THEN** 新增"用户中途退出再恢复的对话连续性测试"场景

## MODIFIED Requirements

### Requirement: 过期 specs 清理
The system SHALL 将 `.trae/specs/enhance-skill-v1.1.0/` 目录整体移至 `.trae/specs/archive/` 目录下。
- **THEN** archive 目录结构保持原有文件层级
- **THEN** 不影响当前有效的 specs 文档

## REMOVED Requirements
无