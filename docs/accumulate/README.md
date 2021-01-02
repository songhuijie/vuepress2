# 前端了解

## html

### 什么是html
HTML称为超文本标记语言，是一种标记语言。它包括一系列标签．通过这些标签可以将网络上的文档格式统一，使分散的Internet资源连接为一个逻辑整体。HTML文本是由HTML命令组成的描述性文本，HTML命令可以说明文字，图形、动画、声音、表格、链接等。 [1] 
超文本是一种组织信息的方式，它通过超级链接方法将文本中的文字、图表与其他信息媒体相关联。这些相互关联的信息媒体可能在同一文本中，也可能是其他文件，或是地理位置相距遥远的某台计算机上的文件。这种组织信息方式将分布在不同位置的信息资源用随机方式进行连接，为人们查找，检索信息提供方便。


### html作用

HTML（HyperText Mark-up Language）即超文本bai标记du语言或超文本链接标示zhi语言，是目前网络dao上应用最为广泛的语言，也是zhuan构成网shu页文档的主要语言。HTML文本是由HTML命令组成的描述性文本，HTML命令可以说明文字、图形、动画、声音、表格、链接等。

## js

### js的介绍

JavaScript是一门脚本语言，是可以插入HTML页面的编程代码，插入HTML以后可以由所有现代浏览器运行
### 一、写如html输出

```html
<body>
<script>
    document.write("<h1>写入html输出，可以直接在页面上输出html内容</h1>");
</script>
</body>
```

### 二、对事件做出响应
```html
<body>
<script>
    document.write("<h1>写入html输出</h1>");
    function touchBegin() {
        alert("开始响应事件");
    }
 
</script>
 
<button onclick="touchBegin()">点击响应事件</button>
<br>
<p2>或者你可以这样写</p2>
<br>
<button onclick="alert('开始响应事件')">点击响应事件</button>
//注意在双引号内部不要继续使用双引号，对于字符串使用单引号代替
</body>
```

### 三、改变html内容
```js
<body>
<script>
    function changeContent() {
        x = document.getElementById("fuck");
        x.innerHTML = "我改变了你的内容";
    }
</script>

<p1 id ="fuck">这是我原来的内容</p1>
<button onclick="changeContent()">点击这里可以改变html的内容</button>
</body>
```
### 四、改变html图像
```js
<body>
<script>
    function changeImage() {
        element = document.getElementById('gewei');
        if (element.src.match("gewei")){
            element.src = "wanzi.jpg";
        }else {
            element.src = "gewei.jpeg";
        }
    }
     
</script>
<img src="gewei.jpeg" id="gewei" onclick="changeImage()">
</body>
```

## css

### css简介

css是Cascading Style Sheets的简称，中文称为层叠样式表，用来控制网页数据的表现，可以使网页的表现与数据内容分离

### css四种引入方式

- 2.1、行内式
行内式是在标记的style属性中设定CSS样式。这种方式没有体现出CSS的优势，不推荐使用。
```html
<!--第一种引入方式-->
<div style="color: red;background-color: beige">hello yuan </div>
```
- 2.2 嵌入式

```html
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        p{
            background-color: #2b99ff;
        }
    </style>
</head>
```
- 2.3 链接式
将一个.css文件引入到HTML文件中（常用）

```html
<link href="mystyle.css" rel="stylesheet" type="text/css"/>
<link href="test1.css" rel="stylesheet">
```
- 2.4 导入式

```html
<style type="text/css">
  
          @import"mystyle.css"; 此处要注意.css文件的路径
  
</style>　
```
