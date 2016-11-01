# React 组件

可以这么说，一个 React 应用就是构建在 React 组件之上的。

组件有两个核心概念：

- props
- state

一个组件就是通过这两个属性的值在 `render` 方法里面生成这个组件对应的 HTML 结构。

_注意：组件生成的 HTML 结构只能有一个单一的根节点。_

## props

前面也提到很多次了，`props` 就是组件的属性，由外部通过 JSX
属性传入设置，一旦初始设置完成，就可以认为 `this.props` 是不可更改的，所以**不要**轻易更改设置 `this.props` 里面的值（虽然对于一个 JS 对象你可以做任何事）。

## state

`state` 是组件的当前状态，可以把组件简单看成一个“状态机”，根据状态 `state`
呈现不同的 UI 展示。

一旦状态（数据）更改，组件就会自动调用 `render` 重新渲染 UI，这个更改的动作会通过
`this.setState` 方法来触发。

## 划分状态数据

一条原则：让组件尽可能地少状态。

这样组件逻辑就越容易维护。

什么样的数据属性可以当作状态？

当更改这个状态（数据）需要更新组件 UI 的就可以认为是 `state`，下面这些可以认为**不是**状态：

- 可计算的数据：比如一个数组的长度
- 和 props 重复的数据：除非这个数据是要做变更的

最后回过头来反复看几遍 [Thinking in
React](http://facebook.github.io/react/docs/thinking-in-react.html)，相信会对组件有更深刻的认识。

## 无状态组件

你也可以用纯粹的函数来定义无状态的组件(stateless function)，这种组件没有状态，没有生命周期，只是简单的接受 props 渲染生成 DOM 结构。无状态组件非常简单，开销很低，如果可能的话尽量使用无状态组件。比如使用箭头函数定义：

```javascript
const HelloMessage = (props) => <div> Hello {props.name}</div>;
render(<HelloMessage name="John" />, mountNode);
```

因为无状态组件只是函数，所以它没有实例返回，这点在想用 refs
获取无状态组件的时候要注意，参见[DOM 操作](dom.md)。
