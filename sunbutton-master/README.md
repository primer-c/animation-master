---
date: November 2 2020
title: Demo for Sun Button
tags: CSS
---

#### 1. 编辑器说明

- VS Code
- 安装插件： `Sass/Less/Scss/Typescript/Javascript/Jade/Pug Compile Hero Pro`
- 配置： Setting.json

  ```json
  {
  "compile-hero": {
      "disable-compile-files-on-did-save-code": false,
      "notification-toggle": false,
      "typescript-output-directory": "./out",
      "javascript-output-toggle": false,
      "sass-output-directory": "./out",
      "less-output-directory": "./out",
      "sass-output-toggle": true,
      "ignore": ["src/test.js", "*/test.scss", "**/spec/*", "**/src/**/*"],
    }
  }
  ```
- 更具路径修改： `sass-output-directory`,`typescript-output-directory`,`less-output-directory`

#### 2.目录结构

- 创建项目目录如下图

  ![demo-sunbutton](/media/web/567AD58E7AD56B6F/Note Book/CSS/sunbutton/demo-sunbutton.png)

#### 3. html

- demo-sunbutton.html
  ```html
  <!DOCTYPE html>
  <html lang="en">
    <head>
      <meta charset="UTF-8"/>
      <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
      <title>Demo of SunButton</title>
      <link rel="shortcut icon" href="../../imgs/favicon.ico" type="image/x-icon"/>
      <link rel="stylesheet" href="../../css/demo-sunbutton.css"/>
    </head>
    <body>
      <a href="#">Sun Button</a>
    </body>
  </html>
  ```
#### 3. less

- demo-sunbutton.less

- 第一步: a标签设置样式，以及渐变效果

  ```less
  a {
    background: linear-gradient(45deg, #00f,#ae2ab3,#0f0,#03a9f4);
    background-size: 400%;
  }
  ```
- 第二步: 设置与调用动画

  ```less
  @keyframes sun {
    100% {
      background-position: -400% 0;
    }
  }
  ```
- 第三步: 创建`a::before`伪类
  1)通过absolute绝对定位,将`a::before`边界扩展`5px`
  2)设置a元素和`a::before`的`z-index值`使a元素呈现
  3)为了实现发光效果，使用了`filter`属性，使之模糊度`10px`

- 第四步: 当`a:hover`时，`a::before`也调用相同动画

- demo-sunbutton.less

  ```less
  * {
    margin: 0;
    padding: 0;
  }
  .center {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  body {
    min-height: 100vh;
    background: #000;
    .center;
    a {
      text-decoration: none;
      font-size: 18px;
      padding: 15px 50px;
      border-radius: 25px;
      color: #fff;
      text-transform: uppercase;
      background: linear-gradient(45deg, #00f,#ae2ab3,#0f0,#03a9f4);
      background-size: 400%;
      position: relative;
      z-index: 1;
      &:hover {
        animation: sun 10s infinite;
      }
      &:hover:before{
        animation: sun 10s infinite;
      }
      &:before {
        content: "";
        position: absolute;
        top: -5px;
        left: -5px;
        right: -5px;
        bottom: -5px;
        background: linear-gradient(45deg, #00f,#ae2ab3,#0f0,#03a9f4);
        background-size: 400%;
        border-radius: 30px;
        z-index: -1;
        filter: blur(10px);
      }
    }
  }
  @keyframes sun {
    100% {
      background-position: -400% 0;
    }
  }
  ```
- 编译后： `demo-sunbutton.css`

  ```css
  * {
    margin: 0;
    padding: 0;
  }
  .center {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  body {
    min-height: 100vh;
    background: #000;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  body a {
    text-decoration: none;
    font-size: 18px;
    padding: 15px 50px;
    border-radius: 25px;
    color: #fff;
    text-transform: uppercase;
    background: linear-gradient(45deg, #00f, #ae2ab3, #0f0, #03a9f4);
    background-size: 400%;
    position: relative;
    z-index: 1;
  }
  body a:hover {
    animation: sun 10s infinite;
  }
  body a:hover:before {
    animation: sun 10s infinite;
  }
  body a:before {
    content: "";
    position: absolute;
    top: -5px;
    left: -5px;
    right: -5px;
    bottom: -5px;
    background: linear-gradient(45deg, #00f, #ae2ab3, #0f0, #03a9f4);
    background-size: 400%;
    border-radius: 30px;
    z-index: -1;
    filter: blur(10px);
  }
  @keyframes sun {
    100% {
      background-position: -400% 0;
    }
  }
  ```

#### 4. 参考文档

[[]]()

#### 5. 联系方式

邮箱： yuanmin8888@outlook.com