---
title: npx-note
date: 2022-05-26 14:40:11
tags: note
---
### simply introduce
- install Node will auto install npm,and take npx
- main utility: use some module
  - ex: use module: Mocha
  - normal  => node-module/.bin/mocha  --version 
  - npx mocha --version
  - theory: check node-module/.bin and #PATH，find module.
  - 避免全局安装模块
    - 将需要用到的包下载在本地某个文件夹使用后会自动删除
    - 可以用来临时安装指定node版本 使用后会自动删除

### rollup
- npm install --global rollup