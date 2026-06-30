# 验收检查清单

## 核心功能增强检查
- [ ] `resources/institutions.json` 文件存在，包含 50+ 院校映射数据
- [ ] `resources/major-mapping.json` 文件存在，覆盖七大类常见专业
- [ ] 两个 JSON 文件格式合法（可被 JSON 解析器校验）
- [ ] SKILL.md Step 2 包含内置库优先匹配逻辑（命中→直接使用，未命中→WebSearch）
- [ ] SKILL.md Step 3 包含内置库优先匹配逻辑
- [ ] SKILL.md 包含"MIT方法落地映射表"（主动学习→输出练习、费曼→复述挑战、间隔复习→时间表、分块→45min×3）
- [ ] SKILL.md 包含 Step 9 学习效果评估（2 周诊断题 + 正确率分流）

## 文档完善检查
- [ ] `references/examples.md` 包含示例 4（医学专业）
- [ ] `references/examples.md` 包含示例 5（专科院校）
- [ ] `references/examples.md` 包含示例 6（未知院校降级流程）
- [ ] `TEST.md` 文件存在，包含 10+ 测试用例
- [ ] 测试用例覆盖不同院校层次、专业类型、边界场景

## 工程化改进检查
- [ ] `.github/workflows/ci.yml` 文件存在
- [ ] CI 包含 SKILL.md frontmatter 格式检查
- [ ] CI 包含 JSON 格式校验
- [ ] CI 包含文档链接有效性检查
- [ ] README.md 核心特性列表包含"效果评估与动态调优"
- [ ] README.md 功能模块表包含"学习效果评估"行
- [ ] CHANGELOG.md 包含 v1.2.0 变更记录

## GitHub 提交检查
- [ ] 包含 `feat: 增加内置院校-专业知识库` 提交
- [ ] 包含 `feat: MIT学习方法落地细化与效果评估机制` 提交
- [ ] 包含 `docs: 补充边界场景示例对话与测试文档` 提交
- [ ] 包含 `ci: 添加 GitHub Actions CI` 提交
- [ ] 包含 `chore: bump version to v1.2.0` 提交
- [ ] 已推送到远程仓库 main 分支