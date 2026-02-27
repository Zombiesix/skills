---
category: Configuration
---

# Prettier Configuration

Prettier 代码格式化配置。

## File Location

`.prettierrc.js`

## Content

```javascript
export default {
  arrowParens: "avoid",
  singleQuote: false,
  semi: true,
  printWidth: 100,
  tabWidth: 2,
  useTabs: false,
  quoteProps: "as-needed",
  bracketSpacing: true,
  jsxBracketSameLine: false,
  jsxSingleQuote: false,
  htmlWhitespaceSensitivity: "ignore",
  overrides: [
    {
      files: "*.json",
      options: {
        printWidth: 200,
      },
    },
  ],
};
```

## Options

| Option | Value | Description |
|--------|-------|-------------|
| `arrowParens` | `"avoid"` | 箭头函数参数省略括号 |
| `singleQuote` | `false` | 使用双引号 |
| `semi` | `true` | 使用分号 |
| `printWidth` | `100` | 每行最大字符数 |
| `tabWidth` | `2` | 缩进空格数 |
| `useTabs` | `false` | 使用空格而非制表符 |
