---
category: Configuration
---

# Vite Configuration

Vite 构建工具配置，包含插件、别名、代理等设置。

## File Location

`vite.config.ts`

## Content

```typescript
import { ConfigEnv, defineConfig, loadEnv } from "vite";
import vue from "@vitejs/plugin-vue";
import path from "path";
import VueJsx from "@vitejs/plugin-vue-jsx";
import viteCompression from "vite-plugin-compression";
import { createSvgIconsPlugin } from "vite-plugin-svg-icons";
import { Drop } from "esbuild";

export default defineConfig(({ mode }: ConfigEnv) => {
  const env = loadEnv(mode, process.cwd());
  const config = {
    plugins: [
      vue(),
      VueJsx(),
      createSvgIconsPlugin({
        iconDirs: [path.resolve(process.cwd(), "src/assets/icons")],
        symbolId: "icon-[dir]-[name]",
      }),
      viteCompression({
        verbose: true,
        disable: false,
        threshold: 10240,
        algorithm: "gzip",
        ext: ".gz",
      }),
    ],
    esbuild: {
      drop: (env.NODE_ENV === "production" ? ["console", "debugger"] : []) as Drop[],
    },
    resolve: {
      alias: {
        "@": path.resolve(__dirname, "src"),
      },
    },
    css: {
      preprocessorOptions: {
        less: {
          additionalData: '@import "@/assets/style/main.less";',
        },
      },
    },
    server: {
      host: "0.0.0.0",
      port: 5238,
      open: true,
      proxy: {
        "^/api/.*": {
          target: env.VITE_API_URL,
        },
      },
    },
  };
  return config;
});
```

## Features

- **Vue Plugin**: 支持 Vue 单文件组件
- **Vue JSX**: 支持 JSX 语法
- **SVG Icons**: 自动导入 SVG 图标
- **Gzip 压缩**: 生产环境自动压缩
- **路径别名**: `@` 指向 `src` 目录
- **Less 预处理**: 自动导入全局样式
- **开发代理**: API 请求代理到后端服务

## Dependencies

```bash
yarn add -D @vitejs/plugin-vue @vitejs/plugin-vue-jsx vite-plugin-compression vite-plugin-svg-icons esbuild
```
