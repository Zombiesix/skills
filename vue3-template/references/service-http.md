---
category: Service
---

# HTTP Service

基于 Axios 的 HTTP 请求服务封装。

## File Location

`src/service/$http.ts`

## Content

```typescript
import axios, {
  type AxiosInstance,
  type AxiosResponse,
  type AxiosError,
} from "axios";
import type { ResponseData, HttpInstance } from "./types";

const baseURL = import.meta.env.VITE_API_BASE_URL || "/api";
const timeout = 30000;

const instance: AxiosInstance = axios.create({
  baseURL,
  timeout,
});

instance.interceptors.request.use(
  config => {
    const token = localStorage.getItem("token");
    if (token) {
      config.headers.Authorization = `Bearer ${token}`;
    }
    config.headers["Content-Type"] = "application/json";
    return config;
  },
  (error: AxiosError) => {
    console.error("请求错误:", error);
    return Promise.reject(error);
  },
);

instance.interceptors.response.use(
  (response: AxiosResponse<ResponseData>) => {
    const { code, message, data } = response.data;
    if (code === 200) {
      return data;
    } else {
      return Promise.reject(new Error(message || "请求失败"));
    }
  },
  (error: AxiosError<ResponseData>) => {
    console.error("响应错误:", error);
    return Promise.reject(error);
  },
);

const http: HttpInstance = {
  get<T = unknown>(url: string, params?: Record<string, unknown>): Promise<T> {
    return instance.get(url, { params });
  },

  post<T = unknown>(url: string, data?: unknown): Promise<T> {
    return instance.post(url, data);
  },

  put<T = unknown>(url: string, data?: unknown): Promise<T> {
    return instance.put(url, data);
  },

  delete<T = unknown>(url: string, params?: Record<string, unknown>): Promise<T> {
    return instance.delete(url, { params });
  },

  patch<T = unknown>(url: string, data?: unknown): Promise<T> {
    return instance.patch(url, data);
  },
};

export default http;
```

## Features

- **请求拦截器**: 自动添加 token 和 Content-Type
- **响应拦截器**: 统一处理响应数据
- **错误处理**: 统一错误处理机制
- **类型安全**: 完整的 TypeScript 类型支持

## Methods

| Method | Description |
|--------|-------------|
| `get<T>(url, params)` | GET 请求 |
| `post<T>(url, data)` | POST 请求 |
| `put<T>(url, data)` | PUT 请求 |
| `delete<T>(url, params)` | DELETE 请求 |
| `patch<T>(url, data)` | PATCH 请求 |

## Usage

```typescript
import http from "@/service/$http";

interface User {
  id: number;
  name: string;
  email: string;
}

const users = await http.get<User[]>("/users");
const user = await http.post<User>("/users", { name: "John", email: "john@example.com" });
```

## Environment Variables

```bash
VITE_API_BASE_URL=https://api.example.com
```
