---
category: Core
---

# Application Entry

Vue 应用入口文件，初始化应用并注册插件。

## File Location

`src/main.ts`

## Content

```typescript
import { createApp } from "vue";
import { createPinia } from "pinia";
import naive from "naive-ui";
import router from "./router";
import App from "./App.vue";

const app = createApp(App);
app.use(createPinia());
app.use(router);
app.use(naive);
app.mount("#app");
```

## Features

- 创建 Vue 应用实例
- 注册 Pinia 状态管理
- 注册 Vue Router 路由
- 注册 Naive UI 组件库（全局注册组件）
- 挂载应用到 DOM

> **注意**: Naive UI 的功能（如 `useMessage`、`useDialog`、`useNotification`）需要在 App.vue 中使用对应的 Provider 组件包裹。
