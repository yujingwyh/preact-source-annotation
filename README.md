preact 源码注释

** 注:每个文件的注释在 链接 ,觉得好的话麻烦点个star **
序言
一直想去研究react源码,看到一半然后不聊聊值了,主要是由于react项目过于庞大,代码也比较颗粒化 ,执行流转比较复杂,另外也没有过多的精力,所有没有持续下去,关注preact有很长一段时间了,有天想想为什么不研究研究preact源码呢,这个号称只有3KB的react浓缩版.
看了下市面上也有很多preact源码解析,但我感觉都有一些不足,很多都是老版本,例如preact 8,与10版本在代码结构上还是有很大差别的,另外大部分都是分析主要渲染的流程,而对于一些关键点没有去分析,例如为什么有lastDom,为什么value没有在diffProps中处理,这才是重中之重,也是学习源码的收益点,推测作者的用意,还有没有更好的办法,不是提示思维的最佳方式吗?
##一.文件接口结构
这是preact项目src目录的文件 <br />
/diff/catch-error.js      处理组件出现错误情况 <br />
/diff/children.js   子节点的处理 <br />
/diff/index.js 对比虚拟节点<br />
/diff/props 虚拟节点props处理<br />
clone-element.js克隆元素<br />
component.js 组件相关<br />
constants.js 一些常量<br />
create-context.js 创建context<br />
create-element.js 虚拟节点相关<br />
index.js 入口文件<br />
options.js  保存一些设置<br />
render.js  渲染虚拟节点到真实节点<br />
util.js 一些单元方法
##二.渲染原理
```jsx
import { Component,render, h } from '../src';
/**
* react下应该是这样
* import React,{Component} from 'react'
* import {render} from 'react-dom'
*/

class App extends Component{
render(){
  return <div></div>
}
}
function Root(){
 return <App />
}

render(<Root />,document.getElementById('root'));
```


##三.重点深剖
###1.component
###2.diff
###3.context
defaultValue
value
##四.解惑疑点
lastchild 
props中value 单独处理    
{type:null,props:123,..}
createElement children有多个children是数组，单个不是
defer
_catchError _processingException enqueueRender
diffProps _listeners
