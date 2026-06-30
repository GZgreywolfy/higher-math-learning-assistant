# 验收检查清单

## SKILL.md 重构检查
- [x] Few-Shot 示例对话已从 SKILL.md 迁移至 `references/examples.md`
- [x] SKILL.md 总体行数在 80-100 行之间（实际 83 行）
- [x] SKILL.md 末尾包含对 `references/examples.md` 的正确引用链接
- [x] Step 2 包含错误处理子章节（WebSearch 超时/无结果降级、结果矛盾处理、模糊输入澄清话术）
- [x] Step 3 包含培养方案检索错误的处理子章节
- [x] Step 5 包含试卷检索错误的处理子章节
- [x] Step 6 包含按难度评级分层的学习资源推荐（极高/高、中等、较低/低三档）

## 测试用例检查
- [x] `tests/test-cases.md` 文件存在
- [x] 包含至少 8 个典型场景（实际 8 个）
- [x] 覆盖：C9工科、985文科、211经管、普通本科工科、未知院校、专科、艺术类、在读期间同步辅导

## README 优化检查
- [x] README 顶部包含项目状态徽章（version/status/license）
- [x] "如何贡献"部分包含院校-专业-高数级别映射数据提交指引
- [x] 包含"Roadmap"章节

## 工程化文档检查
- [x] CHANGELOG.md 包含 v1.1.0 变更记录
- [x] CONTRIBUTING.md 中的目录结构已更新，反映 `references/` 和 `tests/` 目录