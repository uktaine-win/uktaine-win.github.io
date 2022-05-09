---
title: Vue3-new01
date: 2022-05-09 21:55:59
tags: vue3 new api
---
### 异步组件 defineAsyncComponent()
- 创建异步组件 可以配置相关options

### <script setup></script>
- props emit
### 自定义hooks
  - 封装了数据处理逻辑，返回的值至于传入的参数有关，相当于一个纯函数
### teleport
  - 将子组件挂载到指定的dom下，全局弹窗，全局消息组件
### suspense
  - 会先渲染临时内容 #fallback，等数据或者状态都更新再渲染指定内容 #default
  ```
  <Suspense>
        <template #default>
            <async-component></async-component>
        </template>
        <template #fallback>
            <div>
                Loading...
            </div>
        </template>
  </Suspense>
  //asyncComponent.vue
  <template>
    <div>
        <h4>这个是一个异步加载数据</h4>
        <p>用户名：{{user.nickname}}</p>
        <p>年龄：{{user.age}}</p>
    </div>
    </template>

    <script>
    import { defineComponent } from "vue"
    import axios from "axios"
    export default defineComponent({
        setup(){
            const rawData = await axios.get("http://xxx.xinp.cn/user")
            return {
                user: rawData.data
            }
        }
    })
    </script>
  ```
### 相对vue2的改变
- 对数组的监听
- 没有特殊标记的template会被渲染为普通元素
- slot 写法的调整
- 自定义指令
