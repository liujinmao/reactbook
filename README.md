（一）<strong>JSX语法</strong>

定义：JSX像是在Javascript代码里直接写XML的语法，每一个XML标签都会被JSX转换工具转换成纯Javascript代码;<br>
结构：var demo = \<h1\>hello world!\</h1\>;

ReactDOM.render语法结构：<br>
var React = require('react') -> 在你的文件里储存了一个js对象，对象里包含react方法例如：React.createElement、React.createClass;<br>
var ReactDOM = require('react-dom') -> 储存了另一个js对象，对象里包含的方法对DOM交互相关;<br>
var theBestString = 'tralalalala i am da best';<br>
ReactDOM.render(\<h1\>{theBestString}\</h1\>, document.getElementById('app'));<br><br>


ReactDOM.render()注意点：<br>
1、必须有闭合标签例如：\<img /\> \<br /\>;<br>
2、属性class不能直接用“class=""”,而是用className=""代替；<br>
3、可以嵌套多个HTML标签，但是一定要有个最外层的div包裹，<br>
例如：var demo = (
        \<h1\>hello world!\</h1\>,
        \<p\>\</p\>
      );
  这是错误的，最外层没有一个父级包裹，不会运行；<br>
4、相同的dom不能同时在一个类名里执行两次，<br><br>

inject:<br>
JSX语句里不能注入if声明语句；<br>
if条件语句可以写在外面，例如: function coninToss(){return math.random()*10};<br>            
if(coninToss() == 1){var h = \<h1\>我是一个大数\</h1\>}else{var h = \<h1\>我是一个小数\</h1\>}；
或者直接var h1 = \<h1\>{coninToss() == 1 ? "我是一个大数" : "我是一个小数"  }\</h1\>;
ReactDOM.render(h1,document.getElementById('..'));<br>
if 语句除了运用三木运算符之外还可以用<strong>&&</strong>
var = （\<ul\>
  \<li\>{ coninToss()>0 } && item 1\</li\>
  \<li\>{ coninToss()>3 } && item 2\</li\>
  \<li\>{ coninToss()>7 } && item 3\</li\>
\</ul\>）<br><br>
 
 map的使用<br>
 1、一般用于列表渲染、数组处理等,<br>
 例：var personName = ['Amy','Anna','Ener'];<br>
var personList = personName.map(function(person,i){ return \<li key="person_" + i\>{person}\</li\>});<br>
 ReactDOM.render(\<ul\>{personList}\</ul\>,document.getElementById('..'));<br>
 
 ReactDOM.creatElement()<br>
 用来创建DOM元素，例：ReactDOM.creatElement(“p”,null, "内容")；<br><br><hr>
 
 (二)<strong>React Component(组件)</strong><br>
 React 允许将代码封装成组件（component），然后像插入普通 HTML 标签一样，在网页中插入这个组件。；<br>
 例：var MyComponentClass = <span style="color:red;">ReactDOM.createClass</span>({
          render: function(){
            return \<h1\>hello world\</h1\>;
         }
     });<br>

ReactDOM.render(
   \<MyComponentClass /\>,
    document.getElementById('app')
);<br><br>

render function, this的使用<br>
例：React.createClass({
  myFunc: function () {
    alert('Stop it.  Stop hovering.');
  },<br>

  render: function () {
    return (
      \<div onHover={this.myFunc}\>
      \</div\>;
    );
  }
});<br><br>

component实例化引用<br>
例：var NavBar = React.creatClass({<br>
      render:function(){
        var pages = ['home', 'blog', 'pics', 'bio', 'art', 'shop', 'about', 'contact'];<br>
        var navLinks = pages.map(function(page){<br>
             return (
                \<a  href={'/' + page}\>{page}\</a\>
             )
        })<br>
        return \<nav\>{navLinks}\</nav\>;
      }
  })<br>
  
  var NavBar = require('NavBar');<br>
  var ProfilePage = React.createClass({<br>
  render: function () {<br>
   &nbsp;&nbsp; return (<br>
    &nbsp;&nbsp; &nbsp;&nbsp;\<div\><br>
    &nbsp;&nbsp; &nbsp;&nbsp;&nbsp;\<NavBar /\><br>
    &nbsp;&nbsp; &nbsp;&nbsp;&nbsp;\<h1\>All About Me!\</h1\><br>
    &nbsp;&nbsp; &nbsp;&nbsp;&nbsp;\<p\>I like movies and blah blah blah blah blah\</p\><br>
    &nbsp;&nbsp; &nbsp;&nbsp;&nbsp;\<img src="https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-monkeyselfie.jpg" /\><br>
    &nbsp;&nbsp; &nbsp;&nbsp;\</div\><br>
    );
  }
});


