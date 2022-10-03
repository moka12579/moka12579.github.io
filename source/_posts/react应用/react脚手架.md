---
title: react脚手架
date: 2022-10-03 19:43:17
tags: react应用
categories:	
  - react应用
---

# react脚手架

## react脚手架

1. xxx脚手架：用来帮助程序员快读创建一个基于xxx库的模版项目 （只写了简单效果）
   1. 包含了所有需要的配置（语法检查，jsx编译……）
   2. 下载了所有的依赖
   3. 可以直接运行一个简单的效果
2. react提供了一个用于创建react项目的脚手架库：create-react-app
3. 项目整体技术为：react + webpack + es6 + eslink
4. 使用脚手架开发项目特点：模块化、组件化、工程化

## 创建项目并启动

1. 全局安装create-react-app：`npm install -g create-react-app`
2. 切换到想要创建项目的目录，使用命令：`create-react-app react_staging` 项目名字可以随便起，需要等待一段时间
   当出现如下内容时，代表执行完成
   ![](https://react-1300475487.cos.ap-chengdu.myqcloud.com/success.png)
   命令详解：
   1. `npm start` 开启服务器，写东西想看效果就需要执行这个
   2. `npm run build` 写完的项目最终进行一次打包，一般整个应用都写完了
   3. `npm test` 做测试的，一般不用
   4. `npm run eject` 所有webpack相关的命令都暴露出来，如果执行后暴露出来就没办法再隐藏了
3. 进入项目文件夹 `cd react_staging`
4. 然后执行 `npm start` ，然后就会开启项目，然后自动打开浏览器

