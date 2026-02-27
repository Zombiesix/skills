---
category: Demo
---

# Router Demo

Vue Router 路由功能演示。

## File Location

`src/demos/RouterDemo.vue`

## Content

```vue
<template>
  <div class="router-demo">
    <h2>Vue Router Demo</h2>
    <p>当前路由路径: {{ route.path }}</p>
    <p>当前路由名称: {{ route.name }}</p>
    <n-space>
      <n-button @click="router.push('/demo/router')">刷新当前页</n-button>
      <n-button @click="router.push('/demo/pinia')">跳转到 Pinia Demo</n-button>
    </n-space>
  </div>
</template>

<script setup lang="ts">
import { useRoute, useRouter } from "vue-router";
import { NButton, NSpace } from "naive-ui";

const route = useRoute();
const router = useRouter();
</script>
```

## Features

- 展示当前路由信息
- 演示路由跳转功能
- 使用 `useRoute` 获取路由信息
- 使用 `useRouter` 进行路由跳转
