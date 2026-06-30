# 贡献指南

感谢你考虑为本项目做出贡献！

## 提交 Issue

如果你发现了 bug 或有功能建议，请先检查现有的 Issues 中是否已有相关讨论。如果没有，欢迎创建新的 Issue。

### 提交院校-专业-高数级别映射数据

具体指引请参考 [README.md](./README.md) 中的"如何贡献"章节。

## 提交 Pull Request

1. Fork 本仓库
2. 从 `main` 分支创建你的特性分支：`git checkout -b feat/your-feature-name`
3. 按照 Conventional Commits 规范提交变更
4. 确保所有检查点通过
5. 向 `main` 分支发起 Pull Request

## 开发规范

### Commit 规范

本项目遵循 [Conventional Commits](https://www.conventionalcommits.org/) 规范：

- `feat:` — 新功能
- `fix:` — Bug 修复
- `docs:` — 文档变更
- `refactor:` — 重构
- `style:` — 代码格式调整
- `chore:` — 构建/工具链变更

### 代码规范

- SKILL.md 的 frontmatter 必须包含 `name` 和 `description` 字段
- 所有模块的交互逻辑应有清晰的步骤说明
- 涉及外部检索的内容必须标注信息来源和可信度
- 示例对话遵循已有示例的格式和语气

## 项目结构

```
.trae/
├── skills/<skill-name>/SKILL.md   # Skill 核心定义
└── specs/<change-id>/              # 规格文档
    ├── spec.md
    ├── tasks.md
    └── checklist.md

references/                          # 参考文件（示例对话等）
tests/                               # 测试用例
```

## 许可

通过提交 PR，你同意你的贡献将按照项目的 MIT 许可证进行许可。