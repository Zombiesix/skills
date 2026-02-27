---
category: Demo
---

# Pinia Demo

Pinia 状态管理演示。

## File Location

`src/demos/PiniaDemo.vue`

## Content

```vue
<template>
  <div class="pinia-demo">
    <h2>Pinia Store Demo</h2>
    <n-card title="计数器状态" style="max-width: 400px">
      <p>Count: {{ counter.count }}</p>
      <p>Double Count: {{ counter.doubleCount }}</p>
      <n-space>
        <n-button type="primary" @click="counter.increment()">Increment</n-button>
        <n-button @click="counter.decrement()">Decrement</n-button>
        <n-button type="warning" @click="counter.$reset()">Reset</n-button>
      </n-space>
    </n-card>
  </div>
</template>

<script setup lang="ts">
import { useCounterStore } from "../stores/counter";
import { NButton, NSpace, NCard } from "naive-ui";

const counter = useCounterStore();
</script>
```

## Related Store

See [counter store](./counter.md) for the store implementation.

## Features

- 展示 Pinia store 的使用
- 演示状态读取和修改
- 演示计算属性
- 演示 store 方法调用
