# Webpack

标签（空格分隔）： webpack

---
##安装##
新建一个空的练习文件夹（此处命名为test），打开此文件夹按住shift键的同时单击右键,点击在此处打开命令行.
    
##使用webpack前的准备##
首先在test文件夹中创建一个package.json文件(包括当前项目的依赖模块，自定义的脚本任务等等);
在终端键入**`npm init`**命令可以自动创建这个package.json文件. 输入这个命令后，终端会问你一系列诸如项目名称，项目描述，作者等信息，**回车默认即可**。**注意的是入口文件要设置一下.**

安装完成之后,package.json文件已经就绪.我们在本项目中安装Webpack作为依赖包

    npm install --save-dev webpack

新建一个`index.html`文件,页面结构为基础的页面结构

    <!DOCTYPE html>
    <html lang="zh-cn">
    	<head>
    		<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
            <title></title>
    		<style></style>
    	</head>
    	<body>
    		<p id="box">这是一段话</p>
    		<script src="./build/build.js"></script>
    	</body>
    </html>

新建一个js文件夹,创建两个js文件(main.js和a.js)
`main.js` 用来把Greeter模块返回的节点插入页面。

    var greeter = require('./a.js');
    document.getElementById('root').appendChild(greeter());

`a.js`    只包括一个用来返回包含问候信息的html元素的函数。

    module.exports = function() {
      var div = document.createElement('div');
      div.textContent = "Hi there and greetings!";
      return div;
    };
    
这个时候准备工作已经做完了,下面碍事正式使用webpack.

##正式使用Webpack##

webpack可以在终端中使用，其命令格式是
`webpack 入口文件 index.html中引入的js文件`

**入口文件**是指`package.json`文件中的`"main":入口文件,`

在test文件夹下,js文件夹下的main.js作为入口文件,index.html文件中引入的js文件为build.js,所以在这里,要输入的命令是`webpack ./js/main.js ./build.js`,回车之后就会看到我发给你的那个图片,就说明成功了,这个时候打开index.html就可以看到a.js中插入到页面结构中的内容了.
