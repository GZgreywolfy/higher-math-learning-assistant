# Tasks
- [ ] 任务 1: 创建 validate-skill.yml 工作流
  - 在 `.github/workflows/` 目录下创建 `validate-skill.yml`
  - 包含 SKILL.md YAML frontmatter 格式校验
  - 检查必要字段：name、description、triggers、workflow
  - 检查 triggers 关键词包含 "帮我学高数"、"高等数学怎么学"、"大一高数预习计划"
  - 在 push/PR 到 main 分支时触发

- [ ] 任务 2: 更新 README.md
  - 在"使用示例"部分之后新增"实际运行演示"章节（GIF/截图占位）
  - 在文档末尾新增"常见问题 (FAQ)"章节（3 个 Q&A）
  - 将版本号统一更新为 v1.2.0（顶部徽章 + 底部版本声明）
  - 更新目录结构

- [ ] 任务 3: 新增 references/scoring-model.md
  - 院校档位分值表（C9/985/211/双一流/普通本科/专科）
  - 专业系数表（工科/理科/经管/文科/医学/农学/艺术）
  - 综合评分与五档难度评级映射关系及阈值

- [ ] 任务 4: 扩充 tests/test-cases.md
  - 新增"普通本科 + 文科专业 → 低难度"场景
  - 新增"211院校 + 经管专业 → 中低难度"场景
  - 新增"未知院校 + WebSearch 降级场景"
  - 新增"用户中途退出再恢复的对话连续性测试"场景

- [ ] 任务 5: 清理过期 specs
  - 将 `.trae/specs/enhance-skill-v1.1.0/` 目录移至 `.trae/specs/archive/`

- [ ] 任务 6: Git 提交与推送至 GitHub
  - 使用 Conventional Commits 规范：`feat: 文档完善与自动化验证 v1.2.1`
  - 推送至 origin main

- [ ] 任务 7: 创建 GitHub Release v1.2.1
  - Tag: v1.2.1
  - Title: v1.2.1 - 文档完善与自动化验证
  - Release notes 包含本次所有改动的简要说明

## Task Dependencies
- [任务 1] 至 [任务 5] 可并行执行
- [任务 6] 依赖 [任务 1] ~ [任务 5] 全部完成
- [任务 7] 依赖 [任务 6] 完成