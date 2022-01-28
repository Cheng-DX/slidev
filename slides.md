---
layout: center
highlighter: shiki
monaco: true
mode: dark
fonts:
  mono: Input Mono
title: "About Vue.js"  
download: true
---
# About Vue.js
<a href="https://github.com/Cheng-DX" target="_blank">Cheng-DX</a>
@ 2022-01-18


---
layout: center
---

# 路由
# 状态管理
# 图表
# 权限管理
# Vue3.2

---
layout: center
---

# 路由

---

## VueRouter v3.x

  路由器是在SPA中管理页面的一种程序

- 路由对象 `RouteConfig` 和 嵌套路由
<div class="grid grid-cols-2 gap-x-2 gap-y-4" style="margin-top: 10px">
<div>

#### RouteConfig接口

```ts {all|3,4,5,7,10,13}
// language: TypeScript
interface RouteConfig = {
  path: string,
  component?: Component,
  name?: string,
  components?: { [name: string]: Component },
  redirect?: string | Location | Function,
  props?: boolean | Object | Function,
  alias?: string | Array<string>,
  children?: Array<RouteConfig>, 
  beforeEnter?: 
  (to: Route, from: Route,next: Function) => void,
  meta?: any,
  caseSensitive?: boolean, 
  pathToRegexpOptions?: Object 
}
```
</div>

<div>

#### 举个例子

```js
const route = {
    path: '/profile',
    name: '个人中心',
    component: Layout,
    meta: {
      icon: 'el-icon-user',
    },
    children: [{
        path: 'me',
        name: '我',
        component: () => import('views/user/Me.vue'),
        meta: {
          icon: 'el-icon-medal-1'
        }
      },
    ],
  },
```

</div>
</div>

---

## 路由器对象

```js{all|6}
const routes = [
  // 路由结构
]
const router = new VueRouter({
  mode: 'history', // 路由模式
  routes: routes, // 路由结构
  base: '/', // 基础路径
})
```

<v-click>

### 简写

```js{all|3}
const router = new VueRouter({
  mode: 'history',
  routes,
  base: '/', 
})
```
</v-click>
---

## 内置组件

```vue
  <router-view/>
  <router-link/>
  <keep-alive/>
```

## 导航守卫

```js
router.beforeEach()
router.afterEach()
beforeEnter()
```


## 全局挂载


- router
  使用 `this.$router` 访问
- route
  使用`this.$route`访问

---

## 2 v4.x for Vue3

- 更好的TypeScript支持
- 运行时更改路由
- 组合式API支持

---
layout: center
---
# 状态管理

---

## Vuex
把组件的共享状态抽取出来，并以一个`全局单例模式`管理。在这种模式下，我们的组件树构成了一个巨大的“视图”，不管在树的哪个位置，任何组件都能获取并更改状态

<div class="grid grid-cols-2 gap-x-2 gap-y-4" style="margin-top: 10px">
<div>

#### 举个例子

```js 
const store = new Vuex.Store({
  state: {
    count: 0
  },
  mutations: {
    increment (state) {
      state.count++
    },
    decrement (state) {
      state.count--
    }
  }
})
```
</div>
<div>

#### 效果

<Counter/>

</div>
</div>

特别提示：
我们项目的Vuex文件夹不是标准的Vuex项目结构，仅个人实验使用
合理的项目结构应正确区分state、mutations、actions、getters、modules
---

## Pinia —— Vue的下一代状态管理库

- 更好的TypeScript支持
- 更加轻量级

---
layout: center
---
# 图表


---

# ECharts
百度出品  Apache2.0协议 免费商用
<div class="grid grid-cols-2 gap-x-2 gap-y-4" style="margin-top: 10px">
<div>

#### `vue-echarts` 官方vue组件
option属性传递图表对象，官网示例丰富易上手

<div style="height: 320px">

```js
const option = {
  title: {
    text: 'Stacked Area Chart'
  },
  tooltip: {
    trigger: 'axis',
    axisPointer: {
      type: 'cross',
      label: {
        backgroundColor: '#6a7985'
      }
    }
  },
  legend: {
    data: ['Email', 'Union Ads', 'Video Ads', 'Direct', 'Search Engine']
  },
  toolbox: {
    feature: {
      saveAsImage: {}
    }
  },
  grid: {
    left: '3%',
    right: '4%',
    bottom: '3%',
    containLabel: true
  },
  xAxis: [
    {
      type: 'category',
      boundaryGap: false,
      data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
    }
  ],
  yAxis: [
    {
      type: 'value'
    }
  ],
  series: [
    {
      name: 'Email',
      type: 'line',
      stack: 'Total',
      areaStyle: {},
      emphasis: {
        focus: 'series'
      },
      data: [120, 132, 101, 134, 90, 230, 210]
    },
    {
      name: 'Union Ads',
      type: 'line',
      stack: 'Total',
      areaStyle: {},
      emphasis: {
        focus: 'series'
      },
      data: [220, 182, 191, 234, 290, 330, 310]
    },
    {
      name: 'Video Ads',
      type: 'line',
      stack: 'Total',
      areaStyle: {},
      emphasis: {
        focus: 'series'
      },
      data: [150, 232, 201, 154, 190, 330, 410]
    },
    {
      name: 'Direct',
      type: 'line',
      stack: 'Total',
      areaStyle: {},
      emphasis: {
        focus: 'series'
      },
      data: [320, 332, 301, 334, 390, 330, 320]
    },
    {
      name: 'Search Engine',
      type: 'line',
      stack: 'Total',
      label: {
        show: true,
        position: 'top'
      },
      areaStyle: {},
      emphasis: {
        focus: 'series'
      },
      data: [820, 932, 901, 934, 1290, 1330, 1320]
    }
  ]
};
```

</div>

</div>
<div>

#### 效果
外部使用固定大小的div
```html
<div style="height: 300px;width: 500px;" >
    <v-chart :option="option" />
</div>
```

<Test/>

</div>
</div>

---

# DCharts

个人组件，封装了图像全屏和数据视图，支持快速模式
<div class="grid grid-cols-2 gap-x-2 gap-y-4" style="margin-top: 10px">
  <div>
  
```js
const chart = {
    xData: [1,2,3,4,5],
    yData: [2,3,4,5,6],
    title: "快速模式",
    label: true,
    type: 'bar'
}
```

```html
<d-chart
   fastMode
   :xData="chart.xData"
   :yData="chart.yData"   
   :title="chart.title"
   :label="chart.label"
   :type="chart.type"
/>
```
  </div>
  <div>
    <Test2/>
  </div>
</div>

---
layout: center
---

# 权限管理

---

<div class="grid grid-cols-2 gap-x-2 gap-y-4" style="margin-top: 10px">
  <div>

## token
定义一个结构token，保存你的登录状态、你的权限信息、过期时间等

```js
const token = {
    isLogin: true,
    permission: 'admin',
    lastLoginTime: '2022-01-10'
}
```

## 导航守卫

```js
router.beforeEach((to, from, next) => {
	if( hasToken() ){
        next();
    }else{
        router.push('/login')
    }
})
```
  </div>

  <div>

## 路由权限
利用路由meta属性给路由添加权限，在导航守卫内判断访问的目标路由是否有权限，若没有则导航至403页面

```js
router.beforeEach((to, from, next) => {
	if( hasToken() && hasPermission(permission) ){
        next();
    }else{
        router.push('/login')
    }
})  
```

  </div>
</div>

---
layout: center
---

# Vue3.2

---
layout: center
---
 
<v-clicks>

- 使用TypeScript重写——原生ts支持
- 更快的速度
- 更好的Vite支持
- 向外暴露的响应式系统
- 组合式API
- 方便的 `<script setup>` 语法糖
- 全新的官方文档:[Vue.js - The Progressive JavaScript Framework | Vue.js (vuejs.org)](https://staging.vuejs.org/)
- 没理由不用

</v-clicks>



