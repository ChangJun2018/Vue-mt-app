# mt-app

> A Vue.js project
仿美团app项目

##项目演示
![avatar](./gif_20180601_133110.gif)


##项目目录
[TOC]

## 背景
利用vue完成实战项目仿照美团app，在这个过程中，了解了一个项目前端开发的整个流程，将学到的新的知识点进行整理。


## moke假数据
前后端分离开发的时候，前端和后端是并行开发的，前端往往刚开始不能拿到测试的数据，所以这个时候都需要去moke假数据。在本案例中data文件夹下就是moke的假数据

###配置moke的假数据，vue-cli中配置本地json
######在build中打开webpack.dev.conf.js文件
在```const PORT = process.env.PORT && Number(process.env.PORT)```后写入
```
// 配置moke数据
// 导入express
const express=require("express");
// 创建express实例
const app=express();

// 引入数据
var goods=require("../data/goods.json");
var ratings=require("../data/ratings.json");
var seller=require("../data/seller.json");
```
######在devserver中添加
```
 // 需要在服务启动时，拿到app然后配置路由
    before(app){
        app.get("/api/goods",(req,res)=>{
          res.json(goods)
        })

        app.get("/api/ratings",(req,res)=>{
          res.json(ratings)
        })

        app.get("/api/seller",(req,res)=>{
          res.json(seller)
        })
    }
```

##vue中ref和$refs

ref 被用来给元素或子组件注册引用信息。引用信息将会注册在父组件的 $refs 对象上。如果在普通的 DOM 元素上使用，引用指向的就是 DOM 元素；如果用在子组件上，引用就指向组件实例

**用法**：```<div class="menu-wrapper" ref="menuScroll"></div>```

$refs 是所有注册过的ref的一个集合

**用法**：```this.$refs.menuScroll```

##better-scroll
在本案例中多个场景运用到了滚动，此时，用到了better-scroll,此处简单介绍一下其用法。详情请看其文档。[better-scroll](http://ustbhuangyi.github.io/better-scroll/doc/zh-hans/)
####安装
```npm install better-scroll --save```
**用法**：
```<div class="menu-wrapper" ref="menuScroll"></div>```

``` 
      // 实例化滚动对象
      this.menuScroll=new BScroll(this.$refs.menuScroll,{
        click:true
      })
```