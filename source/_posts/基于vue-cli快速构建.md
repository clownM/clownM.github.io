---
title: 基于vue-cli快速构建
date: 2017-10-02 20:05:00
tags: vue
---

​	vue-cli是一个快速构建vue单页应用的脚手架。

#### **npm全局安装vue-cli步骤**

```
#全局安装 vue-cli
npm install --global vue-cli
#新建项目
vue init webpack myProject
#进入项目目录
cd myProject
#安装相关依赖
npm install
```

<!--more-->

#### 其他相关命令**

```
#开发环境预览项目
npm run dev
#打包部署至服务器
npm run build
#删除依赖（node_modules文件夹）
rimraf node_modules
```

