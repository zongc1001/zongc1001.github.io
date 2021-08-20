---
title: react源码解读(1)：JSX语法
date: 2021-08-20 17:32:05
tags: react
---
# JSX语法

> jsx in depth：https://reactjs.org/docs/jsx-in-depth.html#gatsby-focus-wrapper

JSX本质上只是React提供的语法糖，经过编译之后会转换成React.createElement的调用

```jsx
<MyButton color="blue" shadowSize={2}>
  Click Me
</MyButton>
```

经过编译后：

```js
React.createElement(
  MyButton,
  {color: 'blue', shadowSize: 2},
  'Click Me'
)
```

## React.createElement

在源码中可以看到createElement的函数定义	

![image-20210820184758759](/Users/bytedance/pj/blog/source/_posts/react源码解读1/image-20210820184758759.png)
