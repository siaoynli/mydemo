# CLAUDE.md

 全局使用中文回答问题。

## 项目概述

一个独立的页面，以单个 HTML 文件形式运行。无构建系统、无打包工具、无包管理器。所有依赖通过 CDN 加载。

### 技术栈
- **Vue 3** (CDN: `vue.global.prod.js`) — 组合式 API，使用 `setup()` 语法
- **Naive UI** (CDN: `naive-ui@2.41.0`) — 通过 `app.component()` 手动注册组件
- **原生 CSS** — 内嵌于 `<style>` 标签，无预处理器

### 架构

单文件应用 (`login.html`)，分为三部分：
1. **样式** — 所有 CSS 内嵌在 `<head>` 中，通过 `body.dark` 类实现明暗主题切换
2. **模板** — Vue 模板使用 Naive UI 组件（`n-config-provider`、`n-message-provider`、`n-tabs`、`n-input`、`n-button`、`n-icon`）
3. **脚本** — 通过 `createApp()` 创建 Vue 应用，手动注册组件，挂载到 `#app`

### 功能
- **三个登录标签**：密码登录（用户名/密码 + 滑块验证）、手机登录（短信验证码）、二维码登录（占位）
- **自定义滑块验证** — 拖动滑块完成安全验证（纯前端，无后端）
- **暗黑模式切换** — 在 Naive UI 默认主题和 `darkTheme` 之间切换
- **第三方登录按钮** — 微信、QQ、GitHub（仅 UI，无后端对接）

### 开发方式

- **无需构建** — 直接用浏览器打开 `login.html`，或使用任意静态服务器：
  ```bash
  python3 -m http.server 8080
  # 或
  npx serve .
  ```
- **未配置** lint、测试或类型检查

### 关键文件
- `login.html` — 整个应用的全部内容

**语言规范（强制）**

- **所有与用户的交互回答必须使用中文**。
- **CLAUDE.md 文件本身的所有内容必须使用中文**。
- 项目中所有代码文件的注释必须使用中文
- 技术栈名称、目录结构、函数名、变量名等专有名词保留英文，但描述性文字和注释一律使用中文。
- git commit  提交变更内容也使用中文
