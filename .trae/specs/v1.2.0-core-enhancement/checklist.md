# 验收检查清单

## 核心功能增强检查
- [x] `resources/institutions.json` 文件存在，包含 55 所院校映射数据
- [x] `resources/major-mapping.json` 文件存在，覆盖七大类 41 个专业
- [x] 两个 JSON 文件格式合法
- [x] SKILL.md Step 2 包含内置库优先匹配逻辑
- [x] SKILL.md Step 3 包含内置库优先匹配逻辑
- [x] SKILL.md 包含"MIT方法落地映射表"
- [x] SKILL.md 包含 Step 9 学习效果评估

## 文档完善检查
- [x] `references/examples.md` 包含示例 4（医学专业）
- [x] `references/examples.md` 包含示例 5（专科院校）
- [x] `references/examples.md` 包含示例 6（未知院校降级流程）
- [x] `TEST.md` 文件存在，包含 12 个测试用例
- [x] 测试用例覆盖不同院校层次、专业类型、边界场景

## 工程化改进检查
- [x] `.github/workflows/ci.yml` 文件存在
- [x] CI 包含 SKILL.md frontmatter 格式检查
- [x] CI 包含 JSON 格式校验
- [x] CI 包含文档链接有效性检查
- [x] README.md 核心特性列表包含"效果评估与动态调优"
- [x] README.md 功能模块表包含"学习效果评估"行
- [x] CHANGELOG.md 包含 v1.1.0 变更记录

## GitHub 提交检查
- [x] 包含 `feat: 增加内置院校-专业知识库` 提交 (9d21b32)
- [x] 包含 `feat: MIT学习方法落地细化与效果评估机制` 提交 (f1b4b71)
- [x] 包含 `docs: 补充边界场景示例对话与测试文档` 提交 (5aa8cfe)
- [x] 包含 `ci: 添加 GitHub Actions CI` 提交 (dfd0874)
- [x] 包含 `chore: bump version to v1.1.0` 提交 (25f06c9)
- [ ] 已推送到远程仓库 main 分支（需用户解决网络问题后手动 `git push origin main`）