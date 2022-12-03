# FrontWebBase

> [!tip]
一起尽情学习吧 😀

[:cn:](/zh-cn/) [线上文档](https://saofeng-cyber.github.io/front_web_base/)

## 项目启动

推荐全局安装 docsify-cli 工具，可以方便地创建及在本地预览生成的文档。

``` npm
npm i docsify-cli -g
```

## 开始写文档

- `index.html` 入口文件
- 每一个文件夹下的`README.md`都会做为主页内容渲染
- `_sidebar.md`为侧边导航,在这里面可以添加侧边栏导航页面，如html，css，js文件夹
- `.nojekyll` 用于阻止 GitHub Pages 忽略掉下划线开头的文件

## 本地预览

通过运行 docsify serve 启动一个本地服务器，可以方便地实时预览效果。默认访问地址 <http://localhost:3000> 。

``` npm
docsify serve docs
```

!> 更多命令行工具用法，参考 [docsify-cli](https://github.com/docsifyjs/docsify-cli) 文档

## 图片缩放预览测试

![图片缩放预览测试](./images/mn1.jpg)
