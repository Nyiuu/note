## ==常见模板==
- ### ==计算器、背景变色、时钟==
<!DOCTYPE html>
```
<html lang="en">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>JavaScript Demo</title>

    <style>

        body {

            font-family: Arial, sans-serif;

            text-align: center;

        }

        #calculator {

            margin: 20px;

        }

        input[type="text"] {

            padding: 10px;

            font-size: 18px;

            margin: 5px;

        }

        button {

            padding: 10px 20px;

            font-size: 16px;

            cursor: pointer;

            margin: 5px;

        }

        #clock {

            font-size: 30px;

            margin-top: 20px;

        }

    </style>

</head>

<body>

  

    <h1>JavaScript Demo</h1>

  

    <!-- 1. JavaScript Simple Calculator -->

    <div id="calculator">

        <h2>Simple Calculator</h2>

        <input type="number" id="num1" placeholder="Enter first number">

        <input type="number" id="num2" placeholder="Enter second number">

        <select id="operation">

            <option value="add">Add</option>

            <option value="subtract">Subtract</option>

            <option value="multiply">Multiply</option>

            <option value="divide">Divide</option>

        </select>

        <button onclick="calculate()">Calculate</button>

        <p>Result: <span id="calcResult">0</span></p>

    </div>

  

    <!-- 2. Dynamic Clock -->

    <div id="clock">

        <h2>Current Time</h2>

        <p id="time">Loading time...</p>

    </div>

  

    <!-- 3. Background Color Change -->

    <h2>Page Background Color Changes Every 5 Seconds</h2>

  

    <script>

        // 1. Simple Calculator

        function calculate() {

            var num1 = parseFloat(document.getElementById('num1').value);

            var num2 = parseFloat(document.getElementById('num2').value);

            var operation = document.getElementById('operation').value;

            var result;

  

            if (isNaN(num1) || isNaN(num2)) {

                alert("Please enter valid numbers.");

                return;

            }

  

            switch (operation) {

                case 'add':

                    result = num1 + num2;

                    break;

                case 'subtract':

                    result = num1 - num2;

                    break;

                case 'multiply':

                    result = num1 * num2;

                    break;

                case 'divide':

                    if (num2 === 0) {

                        alert("Cannot divide by zero.");

                        return;

                    }

                    result = num1 / num2;

                    break;

                default:

                    alert("Invalid operation");

                    return;

            }

  

            document.getElementById('calcResult').innerText = result;

        }

  

        // 2. Dynamic Clock

        function updateClock() {

            var now = new Date();

            var hours = now.getHours().toString().padStart(2, '0');

            var minutes = now.getMinutes().toString().padStart(2, '0');

            var seconds = now.getSeconds().toString().padStart(2, '0');

            var timeString = hours + ':' + minutes + ':' + seconds;

            document.getElementById('time').innerText = timeString;

        }

  

        setInterval(updateClock, 1000); // Update clock every second

  

        // 3. Background Color Change

        function changeBackgroundColor() {

            var colors = ['#FF5733', '#33FF57', '#3357FF', '#FFFF33', '#FF33FF', '#33FFFF'];

            var randomColor = colors[Math.floor(Math.random() * colors.length)];

            document.body.style.backgroundColor = randomColor;

        }

  

        setInterval(changeBackgroundColor, 5000); // Change background color every 5 seconds

    </script>

  

</body>

</html>
```

- ![[截屏2024-12-06 15.28.34.png]]
- ### ==eg1.打开窗口、用户改变背景颜色==

```
 <html>

    <head>

        <title>eg1</title>

        <style>

  

        </style>

    </head>

    <script language ="javascript">

        function test()               //用户改变背景颜色

        {

            var x, y;

            x = window.confirm("Are you sure to place order?");

            if (x == true)   //这里怎么判断用户输入？-> confirm只给你是或否，是用户点击

            {

                y = window.prompt("your favorite color is:","");

                //document.bgcolor = y;         //已被弃用，但是教材代码

                document.body.style.backgroundColor = y;

            }

            else

                alert("you cancelled this order!");

        }

        function open_win()           //打开窗口

        {

            window.open("https://www.baidu.com","","width = 800, height = 600, left = 300, top = 300");

            window.open("https://cn.bing.com","", "width = 400, height = 300, left = 0, top = 0")

        }

  

    </script>

    <body>

       <input type="button" value="confirm" onclick="test()" />

       <input type="button" value="openwin" onclick="open_win()" />

    </body>

</html>
```
- ### ==eg2.div的移动和旋转==
```
 <!DOCTYPE html>

<html>

    <head>

        <title>eg2</title>

        <style>

            #one {

                height: 100px;

                width: 100px;

                background-color: aqua;

                padding: 5px;

                position: absolute; /* 添加绝对定位，以便可以调整left和top */

                transition: transform 0.5s, left 0.5s, top 0.5s; /* 添加过渡效果 */

            }

        </style>

    </head>

    <script language="javascript">

        var deg = 0; // 使用var声明全局变量

  

        function movediv(event) {

            var x = document.getElementById("one");

  

            if (event.keyCode == 97) { // 键码97对应'a'

                x.style.left = (x.offsetLeft - 10) + "px";

            }

            if (event.keyCode == 100) { // 键码100对应'd'

                x.style.left = (x.offsetLeft + 10) + "px";

            }

            if (String.fromCharCode(event.keyCode) == 's') { // 字符's'

                x.style.top = (x.offsetTop + 10) + "px";

            }

            if (String.fromCharCode(event.keyCode) == 'w') { // 字符'w'

                x.style.top = (x.offsetTop - 10) + "px";

            }

            if (event.keyCode == 32) { // 键码32对应空格

                deg += 30;

                if (deg == 360) {

                    deg = 0;

                }

                var d = deg + "deg"; // 计算旋转角度字符串

                x.style.transform = "rotate(" + d + ")"; // 应用旋转角度

            }

        }

  

        document.onkeypress = movediv; // 将函数赋值给事件处理程序 注意不打括号

    </script>

    <body>

        <div id="one"></div>

    </body>

</html>
```
- ### ==eg3.利用表单改变颜色==
```
	 <!DOCTYPE html>

<html lang="zh-CN">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>改变字体颜色和样式</title>

    <style>

        #text-container {

            margin-top: 20px;

            font-size: 16px;

            color: black;

            font-weight: normal;

            font-style: normal;

        }

    </style>

</head>

<body>

    <h1>改变字体颜色和样式</h1>

    <form id="font-form">

        <label for="color">选择字体颜色:</label>

        <select id="color" name="color">

            <option value="black">黑色</option>

            <option value="red">红色</option>

            <option value="green">绿色</option>

            <option value="blue">蓝色</option>

            <option value="yellow">黄色</option>

        </select>

  

        <label for="size">选择字体大小:</label>

        <select id="size" name="size">

            <option value="12px">12px</option>

            <option value="14px">14px</option>

            <option value="16px">16px</option>

            <option value="18px">18px</option>

            <option value="20px">20px</option>

        </select>

  

        <label for="weight">选择字体粗细:</label>

        <select id="weight" name="weight">

            <option value="normal">正常</option>

            <option value="bold">粗体</option>

        </select>

  

        <label for="style">选择字体样式:</label>

        <select id="style" name="style">

            <option value="normal">正常</option>

            <option value="italic">斜体</option>

        </select>

  

        <input type="button" value="应用更改" onclick="applyChanges()">

    </form>

  

    <div id="text-container">

        这里是需要改变样式的文本。

    </div>

  

    <script language="javascript">

        function applyChanges() {

            var textContainer = document.getElementById("text-container");

            var colorSelect = document.getElementById("color");

            var sizeSelect = document.getElementById("size");

            var weightSelect = document.getElementById("weight");

            var styleSelect = document.getElementById("style");

  

            // 获取选中的值

            var selectedColor = colorSelect.value;

            var selectedSize = sizeSelect.value;

            var selectedWeight = weightSelect.value;

            var selectedStyle = styleSelect.value;

  

            // 应用选中的值到文本容器

            textContainer.style.color = selectedColor;

            textContainer.style.fontSize = selectedSize;

            textContainer.style.fontWeight = selectedWeight;

            textContainer.style.fontStyle = selectedStyle;

  
  

        }

    </script>

</body>

</html>
```
- ### ==jQuery应用实例==
```
<!DOCTYPE html>

<html lang="zh-CN">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>jQuery 文本消失与显示</title>

    <style>

        #text-container {

            margin-top: 20px;

            font-size: 16px;

        }

    </style>

    <!-- 引入jQuery库 -->

    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>

</head>

<body>

    <h1>jQuery 文本消失与显示示例</h1>

    <div id="text-container">

        这里是需要消失和显示的文本。

    </div>

    <button id="toggle-button">消失/显示</button>

  

    <script language="javascript">

        $(document).ready(function() {

            // 为按钮添加点击事件处理程序

            $('#toggle-button').click(function() {

                // 切换#text-container的显示状态

                $('#text-container').toggle();

            });

        });

    </script>

</body>

</html>
```



## ==语言基础==

==数据类型==
- 数值
	各种进制
	浮点型
	- Infinity 
		如果一个数值超出了JavaScript所能表示的最大值的范围，JavaScript就会输出Infinity；如果一个数值超出了JavaScript所能表示的最小值的范围，JavaScript就会输出-Infinity。
  NaN(非数字)
- 字符串
- 布尔 
- 特殊
	未定义值 
	空值 null

==常量和变量==
- 声明->var
- 赋值-> =
- 打印->`document.write()`
	
==运算符和表达式==
- 有自增  ++   --
-  字符串相加是连接
		![[Pasted image 20241212143814.png]]
-  比较运算符
		![[Pasted image 20241212144336.png]]

- 其他运算符
	![[Pasted image 20241212150119.png]]
	![[Pasted image 20241212150229.png]]
- 运算优先级
	![[Pasted image 20241212150647.png]]
- 
==JavaScript基本语句==
- 跟C一样
==函数==
- 定义
	![[Pasted image 20241212151953.png]]
- 调用
	- 函数的简单调用
	- 在事件响应中调用函数
	- ![[Pasted image 20241212152250.png]]
- 参数
- 返回值
- 嵌套函数
- 变量
- 内置函数
	- ![[Pasted image 20241212152647.png]]
	- 数值处理
		- ![[Pasted image 20241212152757.png]]
		- ![[Pasted image 20241212152946.png]]
		- ![[Pasted image 20241212153001.png]]
		- ![[Pasted image 20241212153010.png]]
	- 字符串处理函数
		- ![[Pasted image 20241212193456.png]]
		- ![[Pasted image 20241212193657.png]]
		- ![[Pasted image 20241212193712.png]]
- 定义函数的其他方法
	- ![[Pasted image 20241212193831.png]]
	- ![[Pasted image 20241212193901.png]]
## ==常用内部对象==
- ==Math对象==
	- 属性![[Pasted image 20241213131922.png]]
	- 方法![[Pasted image 20241213131945.png]]
	- 访问 Math.xxx
- ==Number对象==
	- ![[Pasted image 20241213132517.png]]
	- ![[Pasted image 20241213132543.png]]
	- ![[Pasted image 20241213132609.png]]
	- ![[Pasted image 20241213132701.png]]
	- ![[Pasted image 20241213132736.png]]
	- ![[Pasted image 20241213132805.png]]
- ==Date对象==
	- ![[Pasted image 20241213132847.png]]
	- ![[Pasted image 20241213132938.png]]
	- ![[Pasted image 20241213133023.png]]
	- Date对象的方法![[Pasted image 20241213133059.png]]
		- 注意范围
	- ![[Pasted image 20241213133339.png]]
	- ![[Pasted image 20241213133351.png]]
	- 
- ==数组对象==
	- 介绍
	- 定义
		- ![[Pasted image 20241213133602.png]]
		- ![[Pasted image 20241213133619.png]]
		- ![[Pasted image 20241213133629.png]]
		- ![[Pasted image 20241213133646.png]]
	- 操作
		- ![[Pasted image 20241213133730.png]]
		- ![[Pasted image 20241213133757.png]]
		- ![[Pasted image 20241213133825.png]]
		- ![[Pasted image 20241213133913.png]]
		- ![[Pasted image 20241213133928.png]]
	- 属性
		- ![[Pasted image 20241213134134.png]]
		- ![[Pasted image 20241213134153.png]]
		- ![[Pasted image 20241213134217.png]]
	- 方法
		- ![[Pasted image 20241213134304.png]]
			- ![[Pasted image 20241213134610.png]]
			- ![[Pasted image 20241213134619.png]]
			- ![[Pasted image 20241213134718.png]]
			- ![[Pasted image 20241213134729.png]]
			- ![[Pasted image 20241213134738.png]]
			- ![[Pasted image 20241213134747.png]]
			- ![[Pasted image 20241213134758.png]]
			- ![[Pasted image 20241213134817.png]]
			- ![[Pasted image 20241213134852.png]]
			- ![[Pasted image 20241213134927.png]]
			- ![[Pasted image 20241213135048.png]]
			- ![[Pasted image 20241213135100.png]]
- ==String==
	- 创建
		- 
	- 属性
		- ![[Pasted image 20241213141732.png]]
		- ![[Pasted image 20241213141803.png]]
		- ![[Pasted image 20241213141829.png]]
	- 方法
		- ![[Pasted image 20241213142033.png]]
		- ![[Pasted image 20241213142108.png]]
		- ![[Pasted image 20241213142118.png]]
		- ![[Pasted image 20241213142132.png]]
		- ![[Pasted image 20241213142141.png]]
	- ![[Pasted image 20241213142214.png]]
	- ![[Pasted image 20241213142229.png]]
	- ![[Pasted image 20241213142315.png]]
	- ![[Pasted image 20241213142325.png]]
	- ![[Pasted image 20241213142341.png]]

## ==JavaScript常用文档对象==

- Document对象
	- ==文档对象概述==
		- ![[Pasted image 20241214120456.png]]
	- ==文档对象的常用属性、方法与事件==
		- ![[Pasted image 20241214120550.png]]
		- ![[Pasted image 20241214120608.png]]
		- ![[Pasted image 20241214120622.png]]
	- ==Document对象的应用==
	- ==JavaScript中的cookie设置==
		- ![[Pasted image 20241214121438.png]]
	- ![[Pasted image 20241214121537.png]]
	- ![[Pasted image 20241214121600.png]]
- ==表单对象==
	- ![[Pasted image 20241214121632.png]]
	- ![[Pasted image 20241214121645.png]]
	- ![[Pasted image 20241214121654.png]]
	- ![[Pasted image 20241214121705.png]]
- ==图像对象==
	- ![[Pasted image 20241214121719.png]]
## ==Window窗口对象==
- ==Window对象概述==
	- ![[Pasted image 20241214122407.png]]
	- ![[Pasted image 20241214122421.png]]
	- ![[Pasted image 20241214122510.png]]
- ==对话框==
	- ![[Pasted image 20241214122703.png]]
	- ![[Pasted image 20241214122715.png]]
	- ![[Pasted image 20241214122744.png]]
- ==打开与关闭窗口==
	- ![[Pasted image 20241214122809.png]]
	- ![[Pasted image 20241214122845.png]]
	- ![[Pasted image 20241214122900.png]]
- ==控制窗口==
	- ![[Pasted image 20241214122915.png]]
	- ![[Pasted image 20241214122925.png]]
	- ![[Pasted image 20241214123007.png]]
	- ![[Pasted image 20241214123111.png]]
	- ![[Pasted image 20241214123134.png]]
	- ![[Pasted image 20241214123227.png]]
	- ![[Pasted image 20241214123429.png]]
	- ![[Pasted image 20241214123438.png]]
	- ![[Pasted image 20241214123459.png]]
- ==窗口事件==
	- ![[Pasted image 20241214123812.png]]
	- ![[Pasted image 20241214123819.png]]
- ## ==jQuery选择器==
	- jQuery的工厂函数
		- ![[Pasted image 20241215115303.png]]
	- 基本选择器
		- ![[Pasted image 20241215115336.png]]
		- ![[Pasted image 20241215115421.png]]
		- ![[Pasted image 20241215115428.png]]
		- ![[Pasted image 20241215115435.png]]
		- ![[Pasted image 20241215115444.png]]
	- 层级选择器
		- ![[Pasted image 20241215115519.png]]
		- ![[Pasted image 20241215115528.png]]
		- ![[Pasted image 20241215115536.png]]
		- ![[Pasted image 20241215115607.png]]
	- 过滤选择器
		- ![[Pasted image 20241215115625.png]]
		- ![[Pasted image 20241215115645.png]]
		- ![[Pasted image 20241215115653.png]]
		- ![[Pasted image 20241215115715.png]]
		- ![[Pasted image 20241215115726.png]]
	- 属性选择器
		- ![[Pasted image 20241215115757.png]]
	- 表单选择器
		- ![[Pasted image 20241215115835.png]]
- ## ==JQuery的动画效果==
	- 基本的动画效果
		- ![[Pasted image 20241215120229.png]]
		- ![[Pasted image 20241215120302.png]]
		- ![[Pasted image 20241215120414.png]]
	- 淡入淡出的动画效果
		- ![[Pasted image 20241215120529.png]]
	- 滑动效果
		- ![[Pasted image 20241215120632.png]]
		- ![[Pasted image 20241215120641.png]]
		- ![[Pasted image 20241215120649.png]]
	- 自定义的动画效果
		- ![[Pasted image 20241215120742.png]]
		- ![[Pasted image 20241215120817.png]]
	