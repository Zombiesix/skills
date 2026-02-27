---
category: Core
---

# Router Configuration

Vue Router 路由配置，包含所有 demo 路由。

## File Location

`src/router/index.ts`

## Content

```typescript
import { createRouter, createWebHistory } from "vue-router";
import type { RouteRecordRaw } from "vue-router";

const routes: RouteRecordRaw[] = [
  {
    path: "/",
    redirect: "/demo",
  },
  {
    path: "/demo",
    component: () => import("../demos/DemoLayout.vue"),
    children: [
      {
        path: "",
        name: "DemoHome",
        component: () => import("../demos/DemoHome.vue"),
      },
      {
        path: "router",
        name: "RouterDemo",
        component: () => import("../demos/RouterDemo.vue"),
      },
      {
        path: "pinia",
        name: "PiniaDemo",
        component: () => import("../demos/PiniaDemo.vue"),
      },
      {
        path: "vueuse",
        name: "VueUseDemo",
        component: () => import("../demos/VueUseDemo.vue"),
      },
      {
        path: "naive-ui",
        name: "NaiveUIDemo",
        component: () => import("../demos/NaiveUIDemo.vue"),
      },
      {
        path: "axios",
        name: "AxiosDemo",
        component: () => import("../demos/AxiosDemo.vue"),
      },
    ],
  },
];

const router = createRouter({
  history: createWebHistory(),
  routes,
});

export default router;
```

## Routes Structure

| Path | Name | Component | Description |
|------|------|-----------|-------------|
| `/` | - | Redirect to `/demo` | 首页重定向 |
| `/demo` | - | DemoLayout | Demo 布局 |
| `/demo` | DemoHome | DemoHome | Demo 首页 |
| `/demo/router` | RouterDemo | RouterDemo | Router 演示 |
| `/demo/pinia` | PiniaDemo | PiniaDemo | Pinia 演示 |
| `/demo/vueuse` | VueUseDemo | VueUseDemo | VueUse 演示 |
| `/demo/naive-ui` | NaiveUIDemo | NaiveUIDemo | Naive UI 演示 |
| `/demo/axios` | AxiosDemo | AxiosDemo | Axios 演示 |

## Features

- 懒加载所有 demo 组件
- 嵌套路由结构
- 统一的 `/demo` 前缀
