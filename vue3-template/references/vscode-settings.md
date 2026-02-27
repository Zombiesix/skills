---
category: Configuration
---

# VSCode Settings

VSCode 编辑器配置，集成 ESLint 和 Prettier。

## File Location

`.vscode/settings.json`

## Content

```json
{
  "prettier.enable": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit"
  },
  "[vue]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[json]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[jsonc]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[html]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[css]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[less]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "eslint.validate": [
    "javascript",
    "vue",
    "vue-html",
    "typescript",
    "typescriptreact",
    "html",
    "css",
    "less",
    "json",
    "jsonc",
    "json5",
    "markdown"
  ]
}
```

## Features

- 自动保存时修复 ESLint 错误
- 为不同文件类型配置 Prettier 作为默认格式化工具
- 配置 ESLint 验证的文件类型
