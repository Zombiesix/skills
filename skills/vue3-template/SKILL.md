---
name: "vue3-template"
description: "初始化一个完整的 Vue3 + TypeScript 项目，包含 ESLint、Prettier、Vue Router、Pinia、VueUse、Naive UI、Axios 等配置。Invoke when user wants to create a new Vue3 project with full toolchain setup."
version: "1.0.0"
---

# Vue3 项目初始化 Skill

此 Skill 用于快速初始化一个功能完整的 Vue3 + TypeScript 项目，包含代码规范、格式化、状态管理、路由等全套配置。

> **版本信息**: v1.0.0 | 生成日期: 2026-02-26 | 详见 [GENERATION.md](./GENERATION.md)

## 使用步骤

### 第一步：初始化 Vite Vue3 项目

**必须询问用户项目名称**

在使用此 Skill 时，**必须**先询问用户输入项目名称。不能直接使用默认名称。

- 提示用户："请输入项目名称（默认：vue3-template）："
- 如果用户输入了名称，使用该名称
- 如果用户直接回车或输入为空，使用默认名称 `vue3-template`
- **禁止**在未询问的情况下直接使用默认名称

获取到项目名称后，首先尝试使用 npm 创建项目：

```bash
npm create vite@latest <project-name> -- --template vue-ts
```

**🚫 第一步限制说明（严格执行）：**

- **禁止**在第一步启动项目
- **禁止**运行 `npm run dev` 或 `npx vite`
- **禁止**执行 `cd <project-name>; npm install` 或类似命令
- 第一步只负责**创建项目骨架**，不安装依赖，不启动服务
- 项目创建完成后，**直接进入第二步**
- 所有依赖安装将在第二步及后续步骤中统一处理
- **必须等待用户明确选择**解决方案后才能继续

### 第二步：配置 Conventional Commits

进入项目目录并安装依赖：

```bash
cd <project-name>
npm install
```

安装并配置 husky 和 lint-staged：

```bash
npm install -D husky lint-staged
```

创建 `commitlint.config.js`，内容见 [references/commitlint.md](./references/commitlint.md)

在 package.json 中添加指令：`prepare: husky install`，确保 Husky 被正确安装和配置

### 第三步：添加 ESLint 配置

安装 ESLint 相关依赖：

```bash
npm install -D eslint eslint-plugin-vue @typescript-eslint/parser @typescript-eslint/eslint-plugin eslint-plugin-prettier prettier eslint-config-prettier
```

创建 `eslint.config.js`，内容见 [references/eslint-config.md](./references/eslint-config.md)

在 `.vscode` 下创建 `settings.json`，内容见 [references/vscode-settings.md](./references/vscode-settings.md)

### 第四步：添加 Prettier 配置

创建 `.prettierrc.js`，内容见 [references/prettierrc.md](./references/prettierrc.md)

### 第五步：安装 Vue3 生态库

```bash
npm install vue-router@4 pinia vueuse naive-ui axios
```

路由文件放在 router 文件夹中维护，并引入到项目中

### 第六步：更新 vite.config.ts

创建 `vite.config.ts`，内容见 [references/vite-config.md](./references/vite-config.md)

### 第七步：更新 tsconfig.app.json

创建 `tsconfig.json`，内容见 [references/tsconfig.md](./references/tsconfig.md)

### 第八步：创建 Demo 文件

所有 demo 文件通过路由进行维护，父级 path 为 `/demo`，各 demo 作为子路由

在 `src/demos/` 目录下创建以下示例文件：

| 文件 | 说明 | 引用 |
|------|------|------|
| `DemoHome.vue` | Demo 首页 | [references/demo-home.md](./references/demo-home.md) |
| `DemoLayout.vue` | Demo 布局组件 | [references/demo-layout.md](./references/demo-layout.md) |
| `RouterDemo.vue` | Router 路由演示 | [references/demo-router.md](./references/demo-router.md) |
| `PiniaDemo.vue` | Pinia 状态管理演示 | [references/demo-pinia.md](./references/demo-pinia.md) |
| `VueUseDemo.vue` | VueUse 工具集演示 | [references/demo-vueuse.md](./references/demo-vueuse.md) |
| `NaiveUIDemo.vue` | Naive UI 组件演示 | [references/demo-naive-ui.md](./references/demo-naive-ui.md) |
| `AxiosDemo.vue` | Axios 请求演示 | [references/demo-axios.md](./references/demo-axios.md) |

创建 store 文件 `src/stores/counter.ts`，内容见 [references/counter.md](./references/counter.md)

### 第九步：创建路由配置

创建路由配置文件 `src/router/index.ts`，内容见 [references/router.md](./references/router.md)

### 第十步：更新入口文件

更新 `src/main.ts`，内容见 [references/main.md](./references/main.md)

更新 `src/App.vue`，内容见 [references/app.md](./references/app.md)

### 第十一步：格式化所有代码

### 第十一步：添加环境变量文件

创建 `.env`：

```
VITE_API_URL=http://localhost:3000
```

创建 `.env.development`：

```
VITE_API_URL=http://localhost:3000
```

创建 `.env.production`：

```
VITE_API_URL=https://api.example.com
```

## References 目录结构

所有代码模板和配置文件都存储在 `references/` 目录下，便于维护和复用：

```
references/
├── Configuration/          # 配置文件
│   ├── eslint-config.md    # ESLint 配置
│   ├── prettierrc.md      # Prettier 配置
│   ├── vscode-settings.md  # VSCode 设置
│   ├── vite-config.md     # Vite 配置
│   ├── tsconfig.md        # TypeScript 配置
│   └── commitlint.md     # Commitlint 配置
├── Core/                 # 核心文件
│   ├── app.md            # 根组件
│   ├── main.md           # 入口文件
│   └── router.md         # 路由配置
├── Store/                # 状态管理
│   └── counter.md       # Pinia Store 示例
├── Service/              # 服务层
│   ├── service-types.md   # HTTP 类型定义
│   └── service-http.md   # HTTP 服务封装
└── Demo/                 # Demo 组件
    ├── demo-home.md      # Demo 首页
    ├── demo-layout.md    # Demo 布局
    ├── demo-router.md    # Router 演示
    ├── demo-pinia.md     # Pinia 演示
    ├── demo-vueuse.md    # VueUse 演示
    ├── demo-naive-ui.md  # Naive UI 演示
    └── demo-axios.md     # Axios 演示
```

## 依赖说明

### 开发依赖
- `eslint` - 代码检查
- `eslint-plugin-vue` - Vue 文件检查
- `@typescript-eslint/parser` - TypeScript 解析器
- `@typescript-eslint/eslint-plugin` - TypeScript 规则
- `eslint-plugin-prettier` - Prettier 集成
- `prettier` - 代码格式化
- `eslint-config-prettier` - 禁用与 Prettier 冲突的规则
- `husky` - Git hooks
- `lint-staged` - 暂存文件检查

### 生产依赖
- `vue-router@4` - 路由管理
- `pinia` - 状态管理
- `vueuse` - Vue 工具集
- `naive-ui` - UI 组件库
- `axios` - HTTP 请求

## 注意事项

1. **第一步限制**：严禁在第一步启动项目或安装依赖
2. **项目名称**：必须询问用户输入项目名称，不能直接使用默认值
3. **路由结构**：所有 demo 文件通过路由维护，父级 path 为 `/demo`
4. **代码规范**：使用 ESLint + Prettier 保证代码质量
5. **类型安全**：使用 TypeScript 确保类型安全
