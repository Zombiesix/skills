---
category: Store
---

# Counter Store

Pinia 计数器 store，演示状态管理。

## File Location

`src/stores/counter.ts`

## Content

```typescript
import { defineStore } from "pinia";
import { computed, ref } from "vue";

export const useCounterStore = defineStore("counter", () => {
  const count = ref(0);
  const doubleCount = computed(() => count.value * 2);

  function increment() {
    count.value++;
  }

  function decrement() {
    count.value--;
  }

  function $reset() {
    count.value = 0;
  }

  return { count, doubleCount, increment, decrement, $reset };
});
```

## State

| Property | Type | Description |
|-----------|-------|-------------|
| `count` | `Ref<number>` | 当前计数值 |
| `doubleCount` | `ComputedRef<number>` | 计数值的两倍 |

## Actions

| Method | Description |
|--------|-------------|
| `increment()` | 计数值加 1 |
| `decrement()` | 计数值减 1 |
| `$reset()` | 重置为 0 |

## Usage

```vue
<script setup lang="ts">
import { useCounterStore } from "@/stores/counter";

const counter = useCounterStore();
</script>

<template>
  <div>
    <p>Count: {{ counter.count }}</p>
    <p>Double Count: {{ counter.doubleCount }}</p>
    <button @click="counter.increment()">Increment</button>
  </div>
</template>
```
