---
category: Configuration
---

# ESLint Configuration

ESLint 配置文件，用于代码检查和规范。

## File Location

`eslint.config.js`

## Content

```javascript
import eslint from "@eslint/js";
import globals from "globals";
import tseslint from "typescript-eslint";
import pluginVue from "eslint-plugin-vue";
import { defineConfig } from "eslint/config";

import vueParser from "vue-eslint-parser";
import eslintPluginPrettierRecommended from "eslint-plugin-prettier/recommended";
import tsParser from "@typescript-eslint/parser";
import tsPlugin from "@typescript-eslint/eslint-plugin";

export default defineConfig([
  {
    ignores: [
      "node_modules",
      "dist",
      "package-lock.json",
      "dist-ssr",
      "*.local",
      ".npmrc",
      ".DS_Store",
      "*.d.ts",
    ],
  },
  eslint.configs.recommended,
  ...pluginVue.configs["flat/recommended"],
  eslintPluginPrettierRecommended,
  {
    files: ["**/*.ts", "**/*.tsx"],
    languageOptions: {
      parser: tsParser,
      parserOptions: {
        project: true,  // 自动查找最近的 tsconfig.json
        tsconfigRootDir: import.meta.dirname,
        sourceType: "module",
        ecmaVersion: "latest",
      },
    },
    plugins: {
      "@typescript-eslint": tsPlugin,
    },
    rules: {
      "@typescript-eslint/ban-ts-ignore": "off",
      "@typescript-eslint/no-unused-vars": "off",
      "@typescript-eslint/explicit-function-return-type": "off",
      "@typescript-eslint/no-explicit-any": "off",
      "@typescript-eslint/no-var-requires": "off",
      "@typescript-eslint/no-empty-function": "off",
      "@typescript-eslint/no-use-before-define": "off",
      "@typescript-eslint/ban-ts-comment": "off",
      "@typescript-eslint/no-non-null-assertion": "off",
      "@typescript-eslint/explicit-module-boundary-types": "off",
    },
  },
  {
    files: ["**/*.{js,mjs,cjs,vue,ts}"],
    rules: {
      "comma-dangle": "off",
      "no-undef": "off",
      "no-undefined": "off",
      "no-unused-vars": "off",
      "no-irregular-whitespace": "off",
      "space-before-function-paren": 0,
      "arrow-spacing": [2, { before: true, after: true }],
      "block-spacing": [2, "always"],
      "brace-style": [2, "1tbs", { allowSingleLine: true }],
      "object-property-newline": "off",
      "jsx-quotes": [2, "prefer-single"],
      "key-spacing": [2, { beforeColon: false, afterColon: true }],
      "keyword-spacing": [2, { before: true, after: true }],
      "new-cap": [2, { newIsCap: true, capIsNew: false }],
      "new-parens": 2,
      "no-array-constructor": 2,
      "no-caller": 2,
      "no-class-assign": 2,
      "no-cond-assign": 2,
      "no-const-assign": 2,
      "no-control-regex": 0,
      "no-delete-var": 2,
      "no-dupe-args": 2,
      "no-dupe-class-members": 2,
      "no-dupe-keys": 2,
      "no-duplicate-case": 2,
      "no-empty-character-class": 2,
      "no-empty-pattern": 2,
      "no-eval": 2,
      "no-empty": 2,
      "no-extra-boolean-cast": 2,
      "no-extra-parens": [2, "functions"],
      "no-fallthrough": 2,
      "no-floating-decimal": 2,
      "no-func-assign": 2,
      "no-unexpected-multiline": 2,
      "no-useless-escape": 0,
      "array-bracket-spacing": [2, "never"],
    },
  },
  {
    files: ["**/*.vue"],
    languageOptions: {
      parser: vueParser,
      globals: { ...globals.browser, ...globals.node },
      parserOptions: {
        parser: tseslint.parser,
        ecmaVersion: "latest",
        ecmaFeatures: { jsx: true },
      },
    },
    rules: {
      "vue/component-definition-name-casing": "off",
      "vue/singleline-html-element-content-newline": ["off"],
      "vue/no-mutating-props": ["error", { shallowOnly: true }],
      "vue/multi-word-component-names": "off",
      "vue/comment-directive": "off",
      "vue/valid-define-props": "off",
      "vue/one-component-per-file": "off",
      "vue/require-prop-types": "off",
      "vue/attributes-order": "off",
      "vue/require-default-prop": "off",
      "vue/attribute-hyphenation": "off",
      "vue/html-self-closing": "off",
      "vue/html-closing-bracket-newline": "off",
      "vue/no-v-html": "off",
      "no-useless-assignment": "off",
    },
  },
]);
```

## Dependencies

```bash
npm install -D eslint eslint-plugin-vue @typescript-eslint/parser @typescript-eslint/eslint-plugin eslint-plugin-prettier prettier eslint-config-prettier
```
