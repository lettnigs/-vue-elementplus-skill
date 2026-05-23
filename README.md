# 🚀 Vue3 + Element Plus 企业级高阶工程自动化 Skill

[![Vue](https://img.shields.io/badge/Vue-3.x-4FC08D.svg)](https://vuejs.org/)
[![Vite](https://img.shields.io/badge/Vite-5.x-646CFF.svg)](https://vitejs.dev/)
[![Element Plus](https://img.shields.io/badge/Element%20Plus-Latest-409EFF.svg)](https://element-plus.org/)
[![pnpm](https://img.shields.io/badge/pnpm-fast-F69220.svg)](https://pnpm.io/)

> 这是一个专为 AI 编程助手（如 Cursor、GitHub Copilot、Claude 等）量身定制的自动化构建指令集（Prompt）。
> 告别繁琐的依赖安装、配置调试和底层封装，只需一段指令，即可让 AI 为你从 0 到 1 搭建出开箱即用的现代前端标准化工程。

日常新建 Vue 项目时，手动配置依赖包、UI 组件、按需导入以及各种代码规范工具，往往会产生大量重复劳动，极大拖慢开发效率。这份**全自动化构建 Skill** 彻底解决了这一痛点。它不仅对前端初学者极为友好，其严苛的工程化规范也完全满足打造高质量项目经验或投入真实业务生产的需求。

## ✨ 核心特性

* 📦 **现代技术栈全家桶**：底层基于 Vue 3 + Vite 驱动，无缝集成 Vue Router 与 Pinia。
* 🎨 **组件与图标开箱即用**：深度集成 Element Plus 及 `@element-plus/icons-vue`，实现全局图标的自动注册，直接上手画页面。
* ⚡️ **极致开发体验**：内置 `unplugin-auto-import` 和 `unplugin-vue-components`，自动生成类型声明文件，彻底解放双手，告别海量 `import` 样板代码。
* 🛡️ **严苛的工程化规范**：配置了最新的 ESLint (Flat Config) 与 Prettier，并前瞻性地引入了基于 Rust 的极速 Linter **Oxlint**，结合 `.editorconfig` 保障代码风格的绝对统一与纯净。
* 🌐 **生产级底层封装**：内置带有 Token 自动无感注入、全局异常状态拦截的 Axios 封装，以及基于 `pinia-plugin-persistedstate` 的状态持久化方案。
* ⚙️ **深度的编辑器优化**：自动生成 `.vscode/settings.json`，实现保存自动格式化与文件目录深度折叠（File Nesting），保持工作区极度清爽。

## 📖 使用说明

本仓库的核心文件是一段高度结构化的 Prompt 指令。

🔥 **[👉 点击这里获取完整的自动化构建 Skill（Markdown 文件）👈](./vue3-element-prompt.md)**

1. 在你的电脑上新建一个空的本地文件夹。
2. 在该目录下唤起你的 AI 编程助手（如 Cursor 的 Composer 模式，或终端 AI Agent）。
3. 打开上方链接，**复制全部文本**，发送给 AI。
4. 喝口水，等待 AI 自动执行完毕。
5. 运行 `pnpm dev` 启动开发服务器，享受顺滑的编码体验！

> **⚠️ 前置要求**：请确保你的系统环境已全局安装 Node.js 和包管理工具 `pnpm`。

## 📂 自动生成的目录骨架

AI 执行完毕后，你将得到如下符合企业级规范的项目结构（完美支持 VS Code 文件收纳）：

```text
my-vue-app/
├── .vscode/
│   └── settings.json           # 编辑器专属配置与文件嵌套规则
├── src/
│   ├── api/                    # 接口请求中心
│   ├── assets/                 # 静态资源与全局样式
│   │   └── main.scss
│   ├── components/             # 全局公共组件
│   ├── router/                 # 路由配置 (含拦截器逻辑)
│   │   └── index.js
│   ├── stores/                 # Pinia 状态管理 (含持久化配置)
│   │   └── user.js
│   ├── utils/                  # 工具函数库 (含 Axios 底层封装)
│   │   └── request.js
│   ├── views/                  # 业务视图
│   │   ├── article/            # 业务模块：文章
│   │   ├── layout/             # 业务模块：全局布局
│   │   ├── login/              # 业务模块：登录
│   │   └── user/               # 业务模块：用户中心
│   ├── App.vue                 # 根组件
│   ├── auto-imports.d.ts       # 自动导入 API 类型声明
│   ├── components.d.ts         # 自动导入组件类型声明
│   └── main.js                 # 项目入口文件
├── .env                        # 全局环境变量
├── .env.development            # 开发环境变量
├── .env.production             # 生产环境变量
├── .eslintrc-auto-import.json  # 自动导入 ESLint 白名单
├── .gitignore                  # Git 忽略配置
├── index.html                  # 项目 HTML 模板
├── package.json                # 项目依赖与运行脚本
│   ├── .editorconfig           # 跨编辑器代码风格统一配置 (已折叠)
│   ├── .oxlintrc.json          # Oxlint 高阶检查配置 (已折叠)
│   ├── .prettierrc.json        # Prettier 格式化规则 (已折叠)
│   ├── eslint.config.js        # ESLint 扁平化核心配置 (已折叠)
│   └── pnpm-lock.yaml          # 依赖版本锁定文件 (已折叠)
└── vite.config.js              # Vite 构建与按需导入配置
    └── jsconfig.json           # 路径别名与编译提示支持 (已折叠)
