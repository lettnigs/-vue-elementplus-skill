# 🚀 Vue3 + Element Plus 自动化高阶工程构建 Skill

[![Vue](https://img.shields.io/badge/Vue-3.x-4FC08D.svg)](https://vuejs.org/)
[![Vite](https://img.shields.io/badge/Vite-5.x-646CFF.svg)](https://vitejs.dev/)
[![Element Plus](https://img.shields.io/badge/Element%20Plus-Latest-409EFF.svg)](https://element-plus.org/)
[![pnpm](https://img.shields.io/badge/pnpm-fast-F69220.svg)](https://pnpm.io/)

> 这是一个专为 AI 编程助手（如 Cursor、GitHub Copilot、Claude 等）设计的自动化构建指令集（Prompt）。
> 只需将本指令喂给 AI Agent，即可一键自动完成 Vue3 现代前端标准化工程的从 0 到 1 搭建，彻底告别繁琐的手动配置。

## ✨ 核心特性

* 📦 **现代技术栈全家桶**：底层基于 Vue 3 + Vite，无缝集成 Vue Router 与 Pinia。
* 🎨 **组件与图标开箱即用**：深度集成 Element Plus 及 `@element-plus/icons-vue`，实现图标的自动全局注册。
* ⚡️ **极致开发体验**：内置 `unplugin-auto-import` 和 `unplugin-vue-components`，彻底解放双手，告别海量 `import` 样板代码。
* 🛡️ **严苛的工程化规范**：配置了最新的 ESLint (Flat Config) 与 Prettier，并前瞻性地引入了基于 Rust 的极速 Linter **Oxlint**，保障代码极致纯净。
* 🌐 **生产级底层封装**：内置带有 Token 自动无感注入、全局异常状态拦截的 Axios 封装，以及基于 `pinia-plugin-persistedstate` 的状态持久化方案。
* ⚙️ **深度的编辑器优化**：自动生成 `.vscode/settings.json`，实现保存自动格式化与文件目录折叠（File Nesting），保持工作区极度清爽。

## 📖 使用说明

本仓库包含的核心文件为一段高度结构化的 Prompt 指令。

1. 新建一个空的本地文件夹。
2. 在该目录下唤起你的 AI 编程助手（如 Cursor 的 Composer 模式，或任意终端 AI Agent）。
3. 复制本仓库中 `前端vue+elementplus.md` 的全部文本，发送给 AI。
4. 喝口水，等待 AI 自动执行完毕。

> **⚠️ 前置要求**：请确保你的系统环境已全局安装 Node.js 和 `pnpm`。

## 📂 自动生成的目录骨架

AI 执行完毕后，你将得到如下符合企业级规范的项目结构：

```text
my-vue-app/
├── src/
│   ├── api/            # 接口请求中心
│   ├── assets/         # 静态资源与全局样式 (main.scss)
│   ├── components/     # 全局公共组件
│   ├── router/         # 路由配置 (含拦截器)
│   ├── stores/         # Pinia 状态管理 (含持久化配置)
│   ├── utils/          # 工具函数库 (含 Axios 封装)
│   └── views/          # 业务视图
│       ├── article/    # 文章模块
│       ├── layout/     # 全局布局
│       ├── login/      # 登录模块
│       └── user/       # 用户模块
├── .eslintrc-auto-import.json
├── .prettierrc.json
├── eslint.config.js
├── jsconfig.json
├── package.json
└── vite.config.js
