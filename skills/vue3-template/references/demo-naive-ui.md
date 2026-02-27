---
category: Demo
---

# Naive UI Demo

Naive UI 组件库演示。

## File Location

`src/demos/NaiveUIDemo.vue`

## Content

```vue
<template>
  <div class="naive-demo">
    <h2>Naive UI Demo</h2>
    <n-card title="按钮组件" style="margin-bottom: 16px; max-width: 600px">
      <n-space>
        <n-button type="primary">Primary</n-button>
        <n-button type="info">Info</n-button>
        <n-button type="success">Success</n-button>
        <n-button type="warning">Warning</n-button>
        <n-button type="error">Error</n-button>
      </n-space>
    </n-card>
    <n-card title="表单组件" style="max-width: 600px">
      <n-form :model="formValue" label-placement="left" label-width="auto">
        <n-form-item label="用户名">
          <n-input v-model:value="formValue.username" placeholder="请输入用户名" />
        </n-form-item>
        <n-form-item label="邮箱">
          <n-input v-model:value="formValue.email" placeholder="请输入邮箱" />
        </n-form-item>
        <n-form-item>
          <n-button type="primary" @click="handleSubmit">提交</n-button>
        </n-form-item>
      </n-form>
    </n-card>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { NButton, NSpace, NCard, NForm, NFormItem, NInput, useMessage } from "naive-ui";

const message = useMessage();

const formValue = ref({
  username: "",
  email: "",
});

function handleSubmit() {
  message.success(`提交成功: ${JSON.stringify(formValue.value)}`);
}
</script>
```

## Features

- **Button**: 不同类型的按钮
- **Form**: 表单组件
- **Input**: 输入框组件
- **Card**: 卡片容器
- **Space**: 间距布局
- **Message**: 消息提示
