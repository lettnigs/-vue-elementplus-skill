name: 一键构建 Vue3 标准化工程
description: 自动搭建基于 Vue3 + Element Plus + Pinia + 规范化 ESLint 的高阶前端项目


Skill: 一键构建 Vue 3 + Element Plus 标准化高阶工程

请作为资深前端 Agent，在当前目录创建名为 my-vue-app 的项目，并严格一次性连贯执行以下所有构建操作。遇报错请自动修复，提供的代码块必须 100% 原样写入。

一、 脚手架与依赖构建

1. 运行 pnpm create vue@latest my-vue-app 并进入目录。（注：默认选择并集成 Vue Router、Pinia、ESLint 和 Prettier 配置）。然后执行
       pnpm i
   
2. 安装 UI 组件库与业务生产依赖：运行 pnpm add element-plus @element-plus/icons-vue axios pinia-plugin-persistedstate。
3. 安装补充开发依赖：运行 pnpm add -D sass unplugin-auto-import unplugin-vue-components oxlint vite-plugin-vue-devtools vue-eslint-parser eslint-plugin-prettier eslint-config-prettier。
4. 在 package.json 中补充脚本：执行 npm pkg set scripts.lint:oxlint="oxlint ."。

二、 工程清理与目录结构骨架

1. 清空 src 下的默认无用文件（如 assets/main.css、默认 components 等）。严格按照以下规范构建 src 下的目录树：
2. 创建基础文件夹：api, assets, components, router, stores, utils, views。
3. 在 views 文件夹下，创建四个业务子文件夹：article, layout, login, user。
4. 创建 src/assets/main.scss 写入基础样式并在 main.js 引入。
5. 重写 App.vue，仅保留 <router-view /> 占位。
6. 在 main.js 中按如下方式注册所有图标：
       import * as ElementPlusIconsVue from '@element-plus/icons-vue'
       // app 实例化后
       for (const [key, component] of Object.entries(ElementPlusIconsVue)) {
         app.component(key, component)
       }

三、 状态、路由与网络底层封装

在 main.js 挂载 Pinia 及 pinia-plugin-persistedstate；建 stores/user.js 处理 Token 存取并设 persist: true；建 router/index.js 配 / 与 /login 基础路由；建 utils/request.js 封装 Axios（请求头自动挂载 Bearer Token；响应拦截需包含“// TODO: 根据后端实际成功 code 修改判断逻辑”注释，以及 401/500 状态下使用 ElMessage 抛出错误提示、清除凭证跳 /login 的逻辑。注意：在 Axios 响应拦截器内部进行 router 的动态导入或调用，避免顶层引用导致初始化顺序错误）。

四、 核心配置文件强制覆写 (严格按以下代码写入)：

【文件 1】覆盖 vite.config.js：

    import { fileURLToPath, URL } from 'node:url'
    import { defineConfig } from 'vite'
    import vue from '@vitejs/plugin-vue'
    import vueDevTools from 'vite-plugin-vue-devtools'
    import AutoImport from 'unplugin-auto-import/vite'
    import Components from 'unplugin-vue-components/vite'
    import { ElementPlusResolver } from 'unplugin-vue-components/resolvers'
    
    export default defineConfig({
      plugins: [
        vue(),
        vueDevTools(),
        AutoImport({ 
          resolvers: [ElementPlusResolver({ importStyle: 'css' })],
          eslintrc: {
            enabled: true,
            filepath: './.eslintrc-auto-import.json',
            globalsPropValue: true,
          }
        }),
        Components({ 
          resolvers: [ElementPlusResolver({ importStyle: 'css' })] 
        }),
      ],
      base: '/',
      resolve: { 
        alias: { 
          '@': fileURLToPath(new URL('./src', import.meta.url)) 
        } 
      },
    })

【文件 2】创建 jsconfig.json：

    {
      "compilerOptions": { "paths": { "@/*": ["./src/*"] } },
      "exclude": ["node_modules", "dist"],
      "include": ["src/**/*.js", "src/**/*.vue", "src/**/*.d.ts"]
    }

【文件 3】创建 .prettierrc.json：

    {
      "semi": false,
      "singleQuote": true,
      "tabWidth": 2,
      "trailingComma": "es5",
      "printWidth": 80,
      "bracketSpacing": true,
      "arrowParens": "avoid",
      "endOfLine": "lf",
      "vueIndentScriptAndStyle": false,
      "htmlWhitespaceSensitivity": "ignore"
    }

【文件 4】覆盖 eslint.config.js：

    import pluginVue from 'eslint-plugin-vue'
    import prettier from 'eslint-plugin-prettier'
    import configPrettier from 'eslint-config-prettier'
    import vueParser from 'vue-eslint-parser'
    import fs from 'node:fs'
    import path from 'node:path'
    
    let autoImportGlobals = {}
    try {
      const autoImportPath = path.resolve(process.cwd(), './.eslintrc-auto-import.json')
      if (fs.existsSync(autoImportPath)) {
        autoImportGlobals = JSON.parse(fs.readFileSync(autoImportPath, 'utf8')).globals || {}
      }
    } catch (e) {
      console.warn('等待 auto-imports 插件生成配置文件...')
    }
    
    export default [
      {
        ignores: ['node_modules/', 'dist/', '*.config.js', '*.min.js'],
      },
      {
        files: ['**/*.{js,jsx,vue}'],
        languageOptions: {
          parser: vueParser,
          parserOptions: {
            sourceType: 'module',
            ecmaVersion: 'latest',
          },
          globals: {
            window: 'readonly',
            document: 'readonly',
            console: 'readonly',
            Vue: 'readonly',
            ...autoImportGlobals, 
          },
        },
        plugins: {
          vue: pluginVue,
          prettier: prettier,
        },
        rules: {
          'no-console': process.env.NODE_ENV === 'production' ? 'error' : 'warn',
          'no-debugger': process.env.NODE_ENV === 'production' ? 'error' : 'off',
          'no-unused-vars': ['warn', { argsIgnorePattern: '^_' }],
          'prettier/prettier': 'error',
          'vue/multi-word-component-names': 'warn',
          'vue/no-unused-vars': 'error',
          'vue/script-setup-uses-vars': 'error',
          'vue/no-v-html': 'warn',
        },
      },
      configPrettier,
      ...pluginVue.configs['flat/recommended']
    ]

【文件 5】创建 .vscode/settings.json：

    {
      "explorer.fileNesting.enabled": true,
      "explorer.fileNesting.patterns": {
        "tsconfig.json": "tsconfig.*.json, env.d.ts, typed-router.d.ts",
        "vite.config.*": "jsconfig*, vitest.config.*, cypress.config.*, playwright.config.*",
        "package.json": "package-lock.json, pnpm*, .yarnrc*, yarn*, .eslint*, eslint*, .oxlint*, oxli*"
      },
      "editor.codeActionsOnSave": { "source.fixAll.eslint": "explicit" },
      "editor.formatOnSave": true,
      "editor.defaultFormatter": "esbenp.prettier-vscode",
      "[vue]": { "editor.defaultFormatter": "esbenp.prettier-vscode" },
      "prettier.requireConfig": true,
      "prettier.enable": true,
      "eslint.validate": ["vue", "javascript"]
    }


