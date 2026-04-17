# CLAUDE.md

全局使用中文回答问题。

## 项目概述

多个独立的页面，以单个 HTML 文件形式运行。无构建系统、无打包工具、无包管理器。所有依赖通过 CDN 加载。

### 技术栈

- **Vue 3** (CDN: `vue.global.prod.js`) — 组合式 API，使用 `setup()` 语法
- **Naive UI** (CDN: `naive-ui@2.41.0`) — 通过 `app.component()` 手动注册组件
- **原生 CSS** — 内嵌于 `<style>` 标签，无预处理器

### 架构

静态html分为三部分：

1. **样式** — 所有 CSS 内嵌在 `<head>` 中，通过 `body.dark` 类实现明暗主题切换
2. **模板** — Vue 模板使用 Naive UI 组件（`n-config-provider`、`n-message-provider`、`n-tabs`、`n-input`、`n-button`、`n-icon`）
3. **脚本** — 通过 `createApp()` 创建 Vue 应用，手动注册组件，挂载到 `#app`
4. **组件** - 优先使用naiveui的组件实现页面布局，比如卡片，滚动条使用naiveui提供的,所有组件需要可以跟随主题变化样式,图标优先使用xicons图标库

### 开发方式

- **无需构建** — 直接用浏览器打开对应静态文件，或使用任意静态服务器：
  ```bash
  python3 -m http.server 8080
  # 或
  npx serve .
  ```
- **未配置** lint、测试或类型检查

**语言规范（强制）**

- **所有与用户的交互回答必须使用中文**。
- **CLAUDE.md 文件本身的所有内容必须使用中文**。
- 项目中所有代码文件的注释必须使用中文
- 技术栈名称、目录结构、函数名、变量名等专有名词保留英文，但描述性文字和注释一律使用中文。
- git commit 提交变更内容也使用中文
