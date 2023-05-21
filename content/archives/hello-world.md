---
title: 郭渝怀的网络自留地
---
简介：Welcome to [SDIOPID](https://www.sdiopid.top/)! This is my very first post. 
<div style="margin-top: 200px"></div>

<!--more-->

## 坑

dom后hover失效：js优先级高于css，使用!important提高css优先级。*还以为是使用dom0覆盖了时间，一搜才发现是优先级的问题*

感谢：[js 操作 dom 后，css hover失效 - 少元 - 博客园 (cnblogs.com)](https://www.cnblogs.com/xch-jiang/p/12197720.html)



## 20211031

### 1.python程序框架

写程序的基本知识还不全

### 2.nodejs使用规范

据说nodejs开发后可以发布为包，而包可以在hexo直接引用。


## hello hexo world!
### 尝试搭建评论区2021|04|21
[感谢这篇文章](https://blog.csdn.net/weixin_34389926/article/details/92404497)

### 尝试修改背景图2021|04|21
### 通过onenote编辑的笔记可以使用typora进行格式化2021|04|23
注意在用onenote记笔记时遵守markdown语法
直接使用复制粘贴，而且经typora进行格式化是必要的
<!-- forms -->

### Quick Start

### Create a new post

``` bash
$ hexo new "My New Post"
```

More info: [Writing](https://hexo.io/docs/writing.html)

### Run server

``` bash
$ hexo server
```

More info: [Server](https://hexo.io/docs/server.html)

### Generate static files

``` bash
$ hexo generate
```

More info: [Generating](https://hexo.io/docs/generating.html)

### Deploy to remote sites

``` bash
$ hexo deploy
```

blog部署成功的要点：

+ 确保相关文件被关闭，没有被读取占用
+ 确保刚刚登录国github账号

More info: [Deployment](https://hexo.io/docs/one-command-deployment.html)

```
<iframe src="https://www.sdiopid.top/nodeppt/test_3.html" width="100%" height="500" name="topFrame" scrolling="yes" noresize="noresize" frameborder="0" id="topFrame"></iframe>
```

[VIEW](https://www.sdiopid.top/nodeppt/test_3.html)

<iframe src="https://www.sdiopid.top/nodeppt/test_3.html" width="100%" height="250" name="topFrame" scrolling="no" noresize="noresize" frameborder="1" id="topFrame"></iframe>


<iframe src="https://nodeppt.js.org/layout.html" width="100%" height="270" name="topFrame" scrolling="auto" noresize="noresize" frameborder="0" id="topFrame"></iframe>

## js

<script>   
function GetRandomNum(Min,Max)
{   
    var Range = Max - Min;   
    var Rand = Math.random();   
    return(Min + Math.round(Rand * Range));   
}   
var num = GetRandomNum(1,10);   
document.write(num);
var request=require("superagent");
request
    .post("http://api.getlove.cn/api/poetry")
    .set("apikey","56eab527a0facb6670b552fd")
    .send({title:"绝句",start:5})
    .end(function(err,res){
        console.log(res.body);
    });
document.write(infoText);
</script>

<span id="jinrishici-sentence">正在加载今日诗词....</span>

<script src="https://sdk.jinrishici.com/v2/browser/jinrishici.js" charset="utf-8"></script>





<div>num</div>

nww

<script>
	function demo(a,b){
        var sum = a+b;
        return sum;
    }    
    var vi = demo(20,10);
    alert(sum);
</script>

```js
// 调用函数
function demo(a){
    var a =1;
}
<button onclick="demo()">按钮</button>
// button触发函数
//hanshu参数：按顺序传参
//返回值：return会停止函数，向外部返回值。
//给个id，找到id再innerhtml
//函数内的调用了才有，局部变量：var i；对内存好。n=10；全局变量。
//异常抛出：
try{
	deemo();
}catch(err){
    alert(err);
}
//创建自定义错误：抛出
throw"第一个异常：输入错误";
//事件
<button onclick="demo()">
<div class="div" onmouseout="demo(this)" onmouseover=""> </div>
//this指针
<script>
    function demo(ooj){
    ooj.innerHTML="hello";
}

    </scrript>
<input type="text">
//单击事件、鼠标经过、鼠标移除、文本内容改变、文本框选中、光标聚集、移开光标、网页加载、关闭网页
 
DOM简介
1.改变输出流
	1.1明白同时加载和先后加载，注意覆盖问题
    1.2document.getElementbYiD("indname");然后innerHTML（）改变。
    1.3修改属性：直接.属性
2.操作css
	2.1document.getElementById().style.background="blue"
3.事件句柄
	function demo（）{
    }
	function hello(){
        
    }
	var ele=dgid（）.addEventListener("click",function(){
        alert("hello")；
    })
    //xianzia调用函数不会被覆盖，因为加了句柄。使用remove删除句柄。
    
HTML事件处理：对html元素处理,具体到某一个，要一个一个改。
DOM0级事件：调用html数据进行处理，但是事件会被覆盖
DIM2级事件：添加句柄：事件名称，事件函数，布尔值。
	.addEventListener("click",demo(),true)
 
    
	

```

![处理事件](/img/image-20211031134405503-1635659047921.png)

### 事件对象

获取类型：type

click，add句柄后改type

获取目标：target

冒泡：事件比如click会一步一步往上传，上一级div会检测到，故使用阻止冒泡：stopPropagation（）

阻止默认事件。prevent



### 内置对象

对象有属性和方法

people = new Object（）；

people.name=;

people.age=;



或者

people = {

name:””,age:””

}

函数

function people（name,age）{

this._name = name;

this._age=age;

}

son = new people(name,age);

### 字符串对象

length字符串长度

查找字符串是否存在

.indexOf(“查的”)返回位置。

.match()匹配

.replace(before,after)

.toUpperCase().toLowerCase()大小写

转换为数组.split(“,”);