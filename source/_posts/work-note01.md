---
title: work_note01
date: 2022-05-09 21:19:36
tags: vue3 config
---
### vit2 + vue3 +js
- 最近的一个项目采用 vue3 + vite2 + element-plus + js,直接上TS感觉坑会更多，先用js。本文记录一些坑:）
 - vite2 有自动导入组件和各种API的插件，更新的还很快。按照网上的文章先安装了：unplugin-auto-import  unplugin-vue-components
 ```
  npm i -D unplugin-auto-import 
  npm i -D unplugin-vue-components
 ```
 - 在vite.config.js中
 ```
  import AutoImport from 'unplugin-auto-import/vite'
  import Components from 'unplugin-vue-components/vite'
  import { ElementPlusResolver } from 'unplugin-vue-components/resolvers'
  ......省略的部分......
  plugins: [
    Vue(),
    AutoImport({
      // 自动导入 Vue 相关函数，如：ref, reactive, toRef 等
      imports: ['vue', 'vue-router'],
      // 自动导入 Element Plus 相关函数，如：ElMessage, ElMessageBox... (带样式)
      resolvers: [
        ElementPlusResolver(),
        // 自动导入图标组件,但是element-plus icon自动导入没有生效
        //IconsResolver({
        //  prefix: 'Icon'
        //}) 
      ]
    }),
    Components({
      // allow auto load markdown components under `./src/components/`
      extensions: ['vue', 'md'],
      // allow auto import and register components used in markdown
      include: [/\.vue$/, /\.vue\?vue/, /\.md$/],
      resolvers: [
        // 自动注册图标组件
        //IconsResolver({
        //  prefix: false,
        //  enabledCollections: ['ep']
        //}),
        //ElementPlusResolver({}) 
        ElementPlusResolver({
          importStyle: 'sass'
        })
      ]
    }),

  ]
 ```
 - 然后按element-plus官方介绍配置icon的自动导入，第一个大坑出现，自动导入ICON并没生效，后面打算单独起个demo再看看
 - 然后采用B计划，采用自动导入自定义svg。 
 ```
  npm i -D vite-plugin-svg-icons
  vite-config.js中
  import { createSvgIconsPlugin } from 'vite-plugin-svg-icons'
  import path, { resolve } from 'path'
  ................
  plugins:[
    .....
    createSvgIconsPlugin({
      iconDirs: [path.resolve(process.cwd(), 'src/assets/svg')], //路径指向svg文件夹
      symbolId: 'icon-[dir]-[name]' //dir -> svg文件夹名 name -> svg文件名
    }),
    Icons({
      compiler: 'vue3',
    })
  }]
 ```
 - 然后写个全局组件 svgIcon
 ```
   //components/svgIcon/index.vue
   <template>
    <svg aria-hidden="true" :class="['svg-icon', $attrs.class]" :style="{width: iconSize + 'px',height: iconSize + 'px'}">
      <use :xlink:href="'#icon-' + iconName" :fill="color" />
    </svg>
  </template>

  <script>
  import { defineComponent } from 'vue'

  export default defineComponent({
    name: 'svgIcon',
    props: {
      iconName: {
        type: String,
        required: true
      },
      iconSize: {
        type: [Number, String],
        default: 14,
      },
      color: {
        type: String,
        default: '#1677FF'
      }
    },
    setup(props) {

    }
  })
  </script>
  <style scoped>
  .svg-icon {
    fill: currentColor;
    vertical-align: middle;
  }
  </style>
  // 从别人来ctrl+c ctrl+v而来，后面还要调整下
  //main.js中注册 全局实例化
  import 'virtual:svg-icons-register'
  import svgIcon from '@/components/svgIcon/index.vue'

  app.component('svg-icon', svgIcon)
  //实际使用
  <svg-icon icon-name="branch" color="green" icon-size="20"></svg-icon>
 ```
 - 另外下载的svg源码保存后要去掉 fill='xxxx',才能修改color
 