# 任务清单

## 任务列表

- [x] 任务 1: 核心功能增强 — 内置知识库 + MIT细化 + Step 9
  - [x] 子任务 1.1: 创建 `resources/institutions.json`（55 所院校映射数据）
  - [x] 子任务 1.2: 创建 `resources/major-mapping.json`（41 个专业七大类映射）
  - [x] 子任务 1.3: 重构 SKILL.md Step 2 — 增加内置库优先匹配逻辑
  - [x] 子任务 1.4: 重构 SKILL.md Step 3 — 增加内置库优先匹配逻辑
  - [x] 子任务 1.5: 在 SKILL.md 中新增"MIT方法落地映射表"章节
  - [x] 子任务 1.6: 在 SKILL.md 工作流末尾新增 Step 9 学习效果评估

- [x] 任务 2: 文档完善 — 示例对话 + 测试文档
  - [x] 子任务 2.1: 在 `references/examples.md` 新增示例 4（医学专业）
  - [x] 子任务 2.2: 在 `references/examples.md` 新增示例 5（专科院校）
  - [x] 子任务 2.3: 在 `references/examples.md` 新增示例 6（未知院校降级流程）
  - [x] 子任务 2.4: 创建 `.trae/skills/higher-math-learning-assistant/TEST.md`（12 个测试用例）

- [x] 任务 3: 工程化改进 — CI + README
  - [x] 子任务 3.1: 创建 `.github/workflows/ci.yml`（frontmatter 检查 + JSON 校验 + 链接检查）
  - [x] 子任务 3.2: 更新 README.md — 核心特性增加"效果评估与动态调优"、功能模块表增加"学习效果评估"行
  - [x] 子任务 3.3: 更新 CHANGELOG.md — 添加 v1.1.0 变更记录

- [x] 任务 4: GitHub 提交与推送
  - [x] 子任务 4.1: git add 所有变更
  - [x] 子任务 4.2: 按 Conventional Commits 规范分步提交（5 个提交）
  - [ ] 子任务 4.3: 推送到远程仓库 main 分支（受阻：网络连接超时）

## 任务依赖关系
- [任务 1] 和 [任务 2] 可并行执行
- [任务 3] 依赖 [任务 1] 完成
- [任务 4] 依赖 [任务 1]、[任务 2]、[任务 3]