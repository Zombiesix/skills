---
category: Core
---

# Root Component

Vue 应用根组件。

## File Location

`src/App.vue`

## Content

```vue
<template>
  <n-config-provider>
    <n-message-provider>
      <n-dialog-provider>
        <n-notification-provider>
          <div id="app">
            <router-view />
          </div>
        </n-notification-provider>
      </n-dialog-provider>
    </n-message-provider>
  </n-config-provider>
</template>

<script setup lang="ts">
import { NConfigProvider, NMessageProvider, NDialogProvider, NNotificationProvider } from "naive-ui";
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
}
</style>
```

## Features

- 使用 `router-view` 渲染路由组件
- 全局样式重置
- 设置默认字体
- **NConfigProvider**: Naive UI 全局配置提供者
- **NMessageProvider**: 消息提示提供者（支持 `useMessage`）
- **NDialogProvider**: 对话框提供者（支持 `useDialog`）
- **NNotificationProvider**: 通知提供者（支持 `useNotification`）
