# 验收检查清单

## validate-skill.yml 工作流
- [ ] `.github/workflows/validate-skill.yml` 文件存在
- [ ] 包含 SKILL.md YAML frontmatter 格式校验步骤
- [ ] 检查必要字段：name、description、triggers、workflow
- [ ] 检查 triggers 包含 "帮我学高数"、"高等数学怎么学"、"大一高数预习计划"
- [ ] 在 push 和 PR 到 main 分支时触发

## README.md 更新
- [ ] 在"使用示例"部分之后新增"实际运行演示"章节
- [ ] "实际运行演示"包含 GIF/截图占位说明
- [ ] 文档末尾新增"常见问题 (FAQ)"章节
- [ ] FAQ 至少包含 3 个 Q&A（Skill 未激活、WebSearch 不支持、院校不在内置库）
- [ ] 顶部徽章版本号更新为 v1.2.0
- [ ] 底部版本声明更新为 v1.2.0
- [ ] 目录结构同步更新

## references/scoring-model.md
- [ ] 文件 `references/scoring-model.md` 存在
- [ ] 包含院校档位分值表（C9/985/211/双一流/普通本科/专科）
- [ ] 包含专业系数表（工科/理科/经管/文科/医学/农学/艺术）
- [ ] 包含综合评分与五档难度评级映射关系及阈值

## tests/test-cases.md 扩充
- [ ] 新增"普通本科 + 文科专业 → 低难度"场景
- [ ] 新增"211院校 + 经管专业 → 中低难度"场景
- [ ] 新增"未知院校 + WebSearch 降级场景"
- [ ] 新增"用户中途退出再恢复的对话连续性测试"场景

## 过期 specs 清理
- [ ] `enhance-skill-v1.1.0/` 已移至 `.trae/specs/archive/`
- [ ] archive 目录结构完整，保持原有文件层级
- [ ] 当前有效 specs 不受影响

## Git 提交与推送
- [ ] 所有改动已提交
- [ ] 当前分支为 main
- [ ] 已成功 push 至远程仓库 origin main

## GitHub Release
- [ ] Release v1.2.1 已创建
- [ ] Tag 为 v1.2.1
- [ ] Release notes 包含本次所有改动说明