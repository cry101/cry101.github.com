---
title: weex小记
date: 2017-12-27 17:10:25
tags: [vue,weex]
---
### 1.weex和浏览器的差异
（1）weex中不存在window对象



### 2.[weex中使用scss](http://blog.csdn.net/seafishyls/article/details/64444819)
官方lang="stylus"
使用scss则会报错: scss-loader not found
似乎weex-loader中会自动根据lang寻找对应的loader
然而scss使用的是sass-loader 造成了名称不对应的情况


可通过标签引入
```html
<style src='./style.css' />
```
serve下@import同个文件，会造成px解析不对




### 3.weex与vue-route
vue-router不能支持导航链接，只支持编程式导航


### 4.[weex选取图片](https://github.com/voids/weex-image-crop-picker)


### 5.weex plugin add *** 报错，安卓环境问题
could not find gradle wrapper within android sdk
https://www.jianshu.com/p/5d925413c79f

### 6.Couldn't find preset "env" relative to directory
https://www.cnblogs.com/ye-hcj/p/7070084.html


### 7.为什么app端的登陆验证需要在请求头加token
因为传统浏览器端的登陆验证是通过cookie的值，而app使用需要后端设置跨域：
```javascript
//Access-Control-Allow-Origin: '*',
```
而带cookie请求需要设置credentials mode 为 'include'
```javascript
//比如fetch需要设置 
{ credentials: "include" }//带cookie请求

//axios需要设置
{ withCredentials: true} //带cookie请求
```
此时会报错
The value of the 'Access-Control-Allow-Origin' header in the response must not be the wildcard '*' when the request's credentials mode is 'include'.

所以最后的解决方案是通过把登陆校验的值放在请求头里


### 8.打包的时候路由模式hash
