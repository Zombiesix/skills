---
category: Configuration
---

# TypeScript Configuration

TypeScript 编译器配置。

> **注意**: Vite 7.x 使用 Project References 结构，应用源码配置在 `tsconfig.app.json` 中。

## Project Structure

Vite 7.x 创建的 Vue 项目使用以下 TypeScript 配置结构：

```
tsconfig.json          # 项目引用入口（Project References）
├── tsconfig.app.json  # 应用源码配置 ⬅️ 修改此文件
└── tsconfig.node.json # Node 环境配置（Vite 配置等）
```

## File Location

`tsconfig.app.json`

## Content

```json
{
  "extends": "@vue/tsconfig/tsconfig.dom.json",
  "compilerOptions": {
    "tsBuildInfoFile": "./node_modules/.tmp/tsconfig.app.tsbuildinfo",
    "types": ["vite/client", "naive-ui/volar"],
    "baseUrl": ".",
    "paths": {
      "@/*": ["src/*"]
    },
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noFallthroughCasesInSwitch": true,
    "moduleResolution": "bundler"
  },
  "include": ["src/**/*.ts", "src/**/*.tsx", "src/**/*.vue", "*.config.ts"]
}
```

## Options

| Option | Value | Description |
|--------|-------|-------------|
| `extends` | `"@vue/tsconfig/tsconfig.dom.json"` | 继承 Vue 推荐的 DOM 配置 |
| `baseUrl` | `"."` | 基础路径 |
| `paths` | `{ "@/*": ["src/*"] }` | 路径别名配置 |
| `types` | `["vite/client", "naive-ui/volar"]` | 包含 Vite 和 Naive UI 类型定义 |
| `strict` | `true` | 启用严格模式 |
| `moduleResolution` | `"bundler"` | 使用打包器的模块解析策略 |

## Notes

- 不要直接修改 `tsconfig.json`，它是 Project References 的入口文件
- 所有应用相关的 TypeScript 配置都在 `tsconfig.app.json` 中
- `include` 需要包含 `*.config.ts` 以确保 `vite.config.ts` 能被正确解析
