# 技术栈

vue2 + vuex + vue-router + webpack + ES6/7 + axios + sass

框架：使用了vue全家桶进行开发，路由跳转使用的是vue-router，数据请求使用了官方推荐的axios插件,使用es6/7进行开发。

移动端适配： 由于是web-app，因此需要兼容不同设备的屏幕的大小，在这里使用的手淘推荐的[flexible方案](https://www.w3cplus.com/mobile/lib-flexible-for-html5-layout.html)，通过动态的设置根元素的font-size大小，使用rem来进行移动端适配。在这里由于使用rem进行布局，而通常给我们的设计稿是640px,750px为标准的，在编写的时候把px大小转换为rem也比较麻烦，因此这里使用了postcss-px2rem，在编译的时候会将px自动转换为rem。

css预处理器：目前流行的css预处理主要是stylus，less，sass，个人感觉less和sass差别不大，stylus缩进式语法有点不太习惯，综上选择了sass进行样式的编写，通过预处理器可以以编程的方式书写css代码，添加变量，函数，样式继承等。


1. 开发模式下：需要在config下的index.js进行配置
```
proxyTable: {
     '/api': {  
         target: 'http://test.happymmall.com', //源地址
         changeOrigin: true, //改变源
         pathRewrite: {
             '^/api': '' //路径重写
         }
     }
 }
 ```
 
 在进行接口请求时在接口路径前加/api即可，编译后会将/api重写为线上的接口地址
 
 2. 生产模式下：在这里使用的是nignx，需要在远程服务器上安装nignx，然后在nginx.conf文件内配置location即可。

# 功能介绍

在这里主要用vue是把之前慕课网上电商项目进行了重构，做了个移动版本的，功能基本相同，主要是包括4个模块：

用户模块：登录，注册，个人信息修改，密码找回，更新密码。

商品模块：首页，分类，搜索商品，商品详情

购物车模块：购物车商品增加，删除，全选，单选，多选

订单模块：包括地址的管理，提交订单，订单列表，详情，取消订单等

<br>


# 项目运行

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

