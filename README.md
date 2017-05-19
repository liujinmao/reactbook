JSX语法

定义：JSX像是在Javascript代码里直接写XML的语法，每一个XML标签都会被JSX转换工具转换成纯Javascript代码。
结构：var demo = \<h1\>hello world!\</h1\>;

ReactDOM.render语法结构：
var React = require('react');
var ReactDOM = require('react-dom');

var theBestString = 'tralalalala i am da best';

ReactDOM.render(\<h1\>{theBestString}\</h1\>, document.getElementById('app'));


ReactDOM.render()注意点：
1、必须有闭合标签例如：\<img /\> \<br /\>;
2、属性class不能直接用“class=""”,而是用className=""代替；
3、可以嵌套多个HTML标签，但是一定要有个最外层的div包裹，
例如：var demo = (
        \<h1\>hello world!\</h1\>,
        \<p\>\</p\>
      );
  这是错误的，最外层没有一个父级包裹，不会运行；
4、相同的dom不能同时在一个类名里执行两次，
