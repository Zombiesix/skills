---
category: Demo
---

# VueUse Demo

VueUse 工具集演示。

## File Location

`src/demos/VueUseDemo.vue`

## Content

```vue
<template>
  <div class="vueuse-demo">
    <h2>VueUse Demo</h2>
    <n-card title="鼠标位置跟踪" style="margin-bottom: 16px; max-width: 400px">
      <p>x: {{ x }}, y: {{ y }}</p>
    </n-card>
    <n-card title="窗口大小" style="margin-bottom: 16px; max-width: 400px">
      <p>width: {{ width }}, height: {{ height }}</p>
    </n-card>
    <n-card title="暗黑模式" style="max-width: 400px">
      <p>当前模式: {{ isDark ? '暗黑' : '明亮' }}</p>
      <n-button type="primary" @click="toggleDark()">切换模式</n-button>
    </n-card>
  </div>
</template>

<script setup lang="ts">
import { useMouse, useWindowSize, useDark, useToggle } from "@vueuse/core";
import { NButton, NCard } from "naive-ui";

const { x, y } = useMouse();
const { width, height } = useWindowSize();
const isDark = useDark();
const toggleDark = useToggle(isDark);
</script>
```

## Features

- `useMouse`: 跟踪鼠标位置
- `useWindowSize`: 监听窗口大小变化
- `useDark`: 暗黑模式状态管理
- `useToggle`: 切换布尔值
