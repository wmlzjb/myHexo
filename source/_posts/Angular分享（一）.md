---
title: Angular分享（一）
date: 2018-10-18 11:42:02
tags:
  - Angular
  - TypeScript
  - npm
  - less
categories:
  - 前端开发
---

# 相关资料

- [Angular 中文文档](https://angular.cn/)
- [Angular-CLI](https://cli.angular.io/)

# 开始

好的工具能让开发更加简单快捷。
Angular CLI 是一个命令行界面工具，它可以创建项目、添加文件以及执行一大堆开发任务，比如测试、打包和发布。
本章的目标是构建并运行一个超级简单的 TypeScript Angular 应用。使用 Angular CLI 来让每个 Angular 应用从风格指南的那些建议中获益。
在本章的末尾，你会对用 CLI 进行开发有一个最基本的理解，并将其作为其它文档范例以及真实应用的基础。
你还可以 下载这个例子。

## 环境

在开始工作之前，你必须设置好开发环境。
如果你的电脑里没有 Node.js 和 npm，请安装[它们](https://nodejs.org/en/download/)。

> 请先在终端/控制台窗口中运行命令 node -v 和 npm -v， 来验证一下你正在运行 node 8.x 和 npm 5.x 以上的版本。 更老的版本可能会出现错误，更新的版本则没问题。

然后全局安装 Angular CLI

```bash
npm install -g @angular/cli
```

## 创建

打开终端窗口。
运行下列命令来生成一个新项目以及默认的应用代码：

```bash
ng new my-app
```

## 启动

和普通的正常双击打开 `html` 文件访问不一样， `Angular` 应用必须通过 `webservice` 访问。

```bash
ng serve
```

ng serve 命令会启动开发服务器，监听文件变化，并在修改这些文件时重新构建此应用。
使用 --open（或 -o）参数可以自动打开浏览器并访问 `http://localhost:4200/`

## 了解项目结构

### src 文件夹

`browserslist` 一个配置文件，用来在不同的前端工具之间共享目标浏览器，代表这个项目的浏览器兼容情况。

`polyfills.ts` 不同的浏览器对 Web 标准的支持程度也不同。 腻子脚本（polyfill）能把这些不同点进行标准化，填补不同浏览器缺失的 API。

`styles.css` 这里是你的全局样式。 大多数情况下，你会希望在组件中使用局部样式，以利于维护，不过那些会影响你整个应用的样式你还是需要集中存放在这里。

### angular.json 文件

`ng-cli` 运行的配置文件

- 全局引用的 style 和 js
- 环境变量的配置

### package.json 文件

`npm` 包管理的配置文件

- `dependencies` 项目的依赖包
- `devDependencies` 环境的依赖包
- `scripts` npm run 执行的命令
- 本地安装包的引用

### tsconfig.json 文件

`typescript` 编译时的配置文件

### tslint.json 文件

`typescript` 开发时的语法检查配置文件

### README.MD 读我

这个文件也就和字面意思差不多，算是项目介绍文档，使用 `markdown` 编写，针对团队开发的话建议可以把一些执行命令和一些注意事项写在该文件内，方便其它人知晓。

## Angular 的模块 (NgModule)

NgModules 用于配置注入器和编译器，并帮你把那些相关的东西组织在一起。

### 特性模块

针对业务逻辑创建的模块。

### sharedModule

共享组件和指令的模块。

### coreModule

共享服务模块。

### 关于模块的组件和服务的分布

- `sharedModule` 最好是只导出 `component` 和 `directive`
- `coreModule` 最好是只注入服务，不导出组件和指令
- 如果有特殊业务逻辑的复用组件不一定要写在 `sharedModule` 可以放在特性模块内，因为特性模块之间也可以相互引用，但是惰性加载的方式不推荐互相引用。
  1. 组件可能不是一个单纯的 UI 交互性的组件
  2. 组件依赖服务，但是服务并不是公用服务
  3. 修改组件的写法，将组件和服务分离

## Angular 的路由

在用户使用应用程序时，Angular 的路由器能让用户从一个视图导航到另一个视图。

## 路由守护

现在，任何用户都能在任何时候导航到任何地方。 但有时候这样是不对的。

- 该用户可能无权导航到目标组件。
- 可能用户得先登录（认证）。
- 在显示目标组件前，你可能得先获取某些数据。
- 在离开组件前，你可能要先保存修改。
- 你可能要询问用户：你是否要放弃本次更改，而不用保存它们？

你可以往路由配置中添加守卫，来处理这些场景

## Http 拦截

HTTP 拦截机制是 @angular/common/http 中的主要特性之一。 使用这种拦截机制，你可以声明一些拦截器，用它们监视和转换从应用发送到服务器的 HTTP 请求。 拦截器还可以用监视和转换从服务器返回到本应用的那些响应。 多个选择器会构成一个“请求/响应处理器”的双向链表。
