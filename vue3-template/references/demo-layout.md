---
category: Demo
---

# Demo Layout

Demo 布局组件，包含侧边栏菜单和内容区域。

## File Location

`src/demos/DemoLayout.vue`

## Content

```vue
<template>
  <div class="demo-layout">
    <aside class="demo-sidebar">
      <h3>Demo 菜单</h3>
      <n-menu :options="menuOptions" :value="activeKey" @update:value="handleMenuSelect" />
    </aside>
    <main class="demo-content">
      <router-view />
    </main>
  </div>
</template>

<script setup lang="ts">
import { computed, h } from "vue";
import { useRoute, useRouter } from "vue-router";
import { NMenu, type MenuOption } from "naive-ui";
import { RouterLink } from "vue-router";

const route = useRoute();
const router = useRouter();

const activeKey = computed(() => route.name as string);

const menuOptions: MenuOption[] = [
  {
    label: () => h(RouterLink, { to: "/demo" }, { default: () => "首页" }),
    key: "DemoHome",
  },
  {
    label: () => h(RouterLink, { to: "/demo/router" }, { default: () => "Router 路由" }),
    key: "RouterDemo",
  },
  {
    label: () => h(RouterLink, { to: "/demo/pinia" }, { default: () => "Pinia 状态管理" }),
    key: "PiniaDemo",
  },
  {
    label: () => h(RouterLink, { to: "/demo/vueuse" }, { default: () => "VueUse 工具集" }),
    key: "VueUseDemo",
  },
  {
    label: () => h(RouterLink, { to: "/demo/naive-ui" }, { default: () => "Naive UI 组件" }),
    key: "NaiveUIDemo",
  },
  {
    label: () => h(RouterLink, { to: "/demo/axios" }, { default: () => "Axios 请求" }),
    key: "AxiosDemo",
  },
];

function handleMenuSelect(key: string) {
}
</script>

<style scoped>
.demo-layout {
  display: flex;
  min-height: 100vh;
}

.demo-sidebar {
  width: 240px;
  padding: 20px;
  background: #f5f5f5;
  border-right: 1px solid #e0e0e0;
}

.demo-content {
  flex: 1;
  padding: 20px;
}
</style>
```

## Features

- 左侧导航菜单
- 右侧内容区域
- 使用 Naive UI 的 Menu 组件
- 响应式路由视图
