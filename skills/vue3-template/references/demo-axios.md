---
category: Demo
---

# Axios Demo

Axios HTTP 请求演示。

## File Location

`src/demos/AxiosDemo.vue`

## Content

```vue
<template>
  <div class="axios-demo">
    <h2>Axios Demo</h2>
    <n-card style="max-width: 600px">
      <n-space vertical>
        <n-button type="primary" @click="fetchData" :loading="loading">获取数据</n-button>
        <n-alert v-if="error" type="error" :title="'请求失败'">
          {{ error }}
        </n-alert>
        <n-code v-if="data" :code="JSON.stringify(data, null, 2)" language="json" />
      </n-space>
    </n-card>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import http from "../service/$http";
import { NButton, NCard, NSpace, NAlert, NCode, useMessage } from "naive-ui";

const message = useMessage();
const loading = ref(false);
const data = ref(null);
const error = ref("");

async function fetchData() {
  loading.value = true;
  error.value = "";
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/posts/1");
    data.value = await response.json();
    message.success("数据获取成功");
  } catch (err: any) {
    error.value = err.message || "请求失败";
    message.error(error.value);
  } finally {
    loading.value = false;
  }
}
</script>
```

## Related Service

See [HTTP service](./service-http.md) for the service implementation.

## Features

- 演示 HTTP 请求
- 加载状态管理
- 错误处理
- 数据展示
