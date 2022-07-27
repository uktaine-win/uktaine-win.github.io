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
  - create file: add.js main.js 
  ```
    <!-- add.js -->
    const PI = 3.14
    const E = 2.718
    export function addPi(x) {
      return x + PI
    }

    export function addE(x) {
      return x + E
    }
  ``` 
  ```
    import {addPi} from './add.js'
    console.log('addPi', addPi(10));
    <!-- main.js -->
  ```
  - rollup main.js --> generate code in terminal 
  - rollup main.js --file bundle.js
  - generate code in bundle.js
  ```
    const PI = 3.14;
    function addPi(x) {
      return x + PI
    }

    console.log('addPi', addPi(10));
    <!-- bundle.js -->
  ``` 
  - use tree-shaking trim exclude code,only pack related code 
  - some command and params config
    - rollup main.js --file bundle.js  --> pack into assign file
    - rollup m1.js m2.js --dir dist  --> if have more entries file,this command will pack related file in dist(assign folder)
    - rollup main.js --format iife  -> pack generate code will pass into a auto function
    - rollup main.js --compact  --> minimize pack code
    - rollup main.js | uglifyjs --output bundle.js  -->first pack main.js,then use uglify.js transfer minimal into file bundle.js