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

在源码中可以看到createElement的函数定义：

```javascript
React.createElement(
  type,
  [props],
  [...children]
)
```

type即element的类型，可能是一个原生的元素类型（div、span等），也可能是一个React Component（function、class）或者是一个 [React fragment](https://reactjs.org/docs/react-api.html#reactfragment)。这里的type其实就是给到了React创建元素对应DOM实例的方法。



createElement的函数体中会对会返回一个ReactElement函数的调用结果

```javascript
return ReactElement(
    type,
    key,
    ref,
    self,
    source,
    ReactCurrentOwner.current,
    props,
  );
```

ReactElement返回一个JS对象

```javascript
const ReactElement = function (type, key, ref, self, source, owner, props) {
  const element = {
    // This tag allows us to uniquely identify this as a React Element
    $$typeof: REACT_ELEMENT_TYPE,

    // Built-in properties that belong on the element
    type: type,
    key: key,
    ref: ref,
    props: props,

    // Record the component responsible for creating this element.
    _owner: owner,
  };

  if (__DEV__) {...}

  return element;
};
```



































