---
category: Configuration
---

# Commitlint Configuration

Git 提交信息规范检查配置。

## File Location

`commitlint.config.js`

## Content

```javascript
export default {
  extends: ["@commitlint/config-conventional"],
};
```

## Commit Message Format

遵循 Conventional Commits 规范：

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types

| Type | Description |
|------|-------------|
| `feat` | 新功能 |
| `fix` | 修复 bug |
| `docs` | 文档更新 |
| `style` | 代码格式调整 |
| `refactor` | 重构代码 |
| `perf` | 性能优化 |
| `test` | 测试相关 |
| `chore` | 构建/工具相关 |

### Example

```
feat(router): add lazy loading for demo routes

Improve initial load time by implementing lazy loading
for all demo route components.

Closes #123
```

## Dependencies

```bash
yarn add -D @commitlint/cli @commitlint/config-conventional husky lint-staged
```
