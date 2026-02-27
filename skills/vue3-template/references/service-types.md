---
category: Service
---

# HTTP Service Types

HTTP 服务的 TypeScript 类型定义。

## File Location

`src/service/types.ts`

## Content

```typescript
export interface RequestConfig {
  url: string;
  method?: "GET" | "POST" | "PUT" | "DELETE" | "PATCH";
  data?: unknown;
  params?: Record<string, unknown>;
  headers?: Record<string, string>;
  timeout?: number;
}

export interface ResponseData<T = unknown> {
  code: number;
  message: string;
  data: T;
}

export interface HttpInstance {
  get<T = unknown>(url: string, params?: Record<string, unknown>): Promise<T>;
  post<T = unknown>(url: string, data?: unknown): Promise<T>;
  put<T = unknown>(url: string, data?: unknown): Promise<T>;
  delete<T = unknown>(url: string, params?: Record<string, unknown>): Promise<T>;
  patch<T = unknown>(url: string, data?: unknown): Promise<T>;
}
```

## Types

| Interface | Description |
|-----------|-------------|
| `RequestConfig` | 请求配置接口 |
| `ResponseData<T>` | 响应数据接口 |
| `HttpInstance` | HTTP 实例接口 |
