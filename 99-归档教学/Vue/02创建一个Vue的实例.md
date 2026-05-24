## 1. Vue 应用的基本概念
>Vue (发音为 /vjuː/，类似 view) 是一款用于构建用户界面的 JavaScript 框架。它基于标准 HTML、CSS 和 JavaScript 构建，并提供了一套声明式的、组件化的编程模型，帮助你高效地开发用户界面。无论是简单还是复杂的界面，Vue 都可以胜任

在 Vue 3 中，根组件是整个应用的起点，它是 Vue 应用的第一个组件，通常用于定义应用的主要结构和逻辑。根组件通常是 `App.vue` 文件
#### 根组件的作用
1. 应用的入口：
    - 根组件是 Vue 应用的第一个加载的组件，所有其他组件都会嵌套在根组件中
    - 它通过 main.js 文件挂载到 HTML 页面中的某个 DOM 节点（如 `<div id="app">`）
2. 页面的主要结构：
    - 根组件定义了应用的主要结构，包括 HTML 模板、CSS 样式和 JavaScript 逻辑
    - 它可以包含其他组件作为子组件，形成组件树的结构
3. 管理子组件：
    - 根组件可以引入其他子组件，并通过模板将它们组合在一起
4. 共享数据和逻辑：
    - 根组件可以定义全局数据或逻辑，并通过属性或事件与子组件通信

#### 根组件的组成
根组件和普通组件的结构相同，通常由以下部分组成：
1. 模板（Template）：
    - 根组件的模板定义了应用的主要结构，包括 HTML 元素、组件标签和插值表达式
2. 脚本（Script setup）：
    - 根组件的脚本部分包含了应用的 JavaScript 逻辑，包括数据、方法和计算属性
3. 样式（Style）：
    - 根组件的样式部分定义了应用的 CSS 样式，用于控制组件的外观和布局

## 2.创建第一个Vue应用实例的步骤
#### 如果你还没有创建 Vue 项目，可以使用 Vue CLI 或 Vite 创建一个新项目：
1. 使用Vite 创建 Vue 项目
```bash
npm create vue@latest
```
2. 进入项目目录
```bash
cd 项目名称
```
3. 安装依赖
```bash
npm install
```
4. 启动开发服务器
```bash
npm run dev
```
#### 修改App.vue

`App.vue` 是 Vue 应用的根组件，负责定义页面的主要内容。你可以在这里编写模板、逻辑和样式

```html
<template>
  <div id="app">  // 定义了一个id="app"的根元素
    <h1>{{ message }}</h1>  // 使用双大括号输入要绑定的值
  </div>
</template>
<script setup>
import { ref } from 'vue';    // 引入 ref 用于定义响应式数据
const message = ref('Hello Vue!'); // 定义响应式数据 当其中的值发生变化时,页面会自动更新
</script>
```

#### 修改main.js
`main.js` 是 Vue 应用的入口文件，用于创建 Vue 应用实例并挂载到 HTML 页面上的某个 DOM 节点
```js
import { createApp } from 'vue'; // 导入 Vue 的 createApp 方法
import App from './App.vue'; // 导入根组件 App.vue
// 创建 Vue 应用实例，并挂载到 HTML 中 id 为 "app" 的元素上
createApp(App).mount('#app');
```

#### 修改index.html
``` html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Vue App</title>
</head>
<body>
  <div id="app"></div> <!-- Vue 应用的挂载点 -->
  <script type="module" src="/src/main.js"></script> <!-- 引入 main.js -->
</body>
</html>
```
## 总结：
- main.js：入口文件，创建 Vue 应用并挂载到 DOM。
- index.html：HTML 模板文件，提供挂载点。
- App.vue：根组件是应用的起点,它定义了应用的主要结构和逻辑。