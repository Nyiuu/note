# ==2020年==
-  ![[Pasted image 20241215230935.png]]
- 代码
 ```
 <!DOCTYPE html>

<html lang="zh-CN">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>home</title>

    <link rel="stylesheet" href="../css/960_12_col.css">

  

    <style>

        body {

            font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;

        }

  

        .header {

            height: 157px; /* 设置 div 的高度 */

            position: relative;

            overflow: hidden;

            background-image: url('../image/bg.jpg');

            background-repeat:repeat-x;

            background-position: center;

            background-size: auto; /* 让背景图片等比例拉长至宽度为960px，并自动调整高度 */

            padding:0;

        }

  

        .header .alpha, .header .omega {

            /* 为 .alpha 和 .omega 应用的样式 */

            height: 100%;

        }

  

        .header .just {

            /* 为 .just 应用的样式 */

            height: 100%;

            background-image: url('../image/header.jpg');

            background-repeat: no-repeat;

            background-position: center;

            background-size:auto;

            /* 让背景图片等比例拉长至宽度为960px，并自动调整高度 */

        }

        .grid_10.just {

            position: relative; /* 使子元素可以绝对定位 */

        }

  

        .icon-container {

            position: absolute; /* 绝对定位 */

            top: 0;

            right: 0;

            display: flex;

            flex-direction: column; /* 垂直排列 */

            gap: 10px; /* 图标行之间的间距 */

        }

  

        .icon-row {

            display: flex;

            gap: 10px; /* 图标之间的间距 */

        }

  

        .icon {

            width: 30px; /* 图标宽度 */

            height: 30px; /* 图标高度 */

        }

        .first-icon {

            width: auto; /* 使用图片本来的宽度 */

            height: auto; /* 使用图片本来的高度 */

        }

        .nav {

            margin-top: 25px;

            height: 40px; /* 设置导航栏的高度 */

            right: 0;

            bottom: 0;

        }

  

        .nav ul {

            list-style-type: none; /* 移除默认的列表样式 */

            margin: 0; /* 移除默认的边距 */

            padding: 0; /* 移除默认的内边距 */

            overflow: hidden; /* 清除浮动 */

        }

  

        .nav ul li {

            float: right; /* 将列表项水平排列 */

            display: inline; /* 确保列表项在同一行显示 */

        }

  

        .nav ul li a {

            display: block; /* 使链接块级显示 */

            color: black; /* 设置链接文字颜色 */

            text-align: center; /* 文字居中 */

            padding: 10px 16px; /* 设置内边距 */

            text-decoration: none; /* 移除链接下划线 */

        }

  

        .nav ul li a:hover {

            color: aliceblue; /* 鼠标悬停时改变背景颜色 */

        }

        .content{

            height:1024px;

        }

        .sidebar{

            height: 100%;

            padding:0;

        }

        .sidebar .top{

            height: 33px;

            margin-top: 20px;

            margin-bottom: 0;

            padding-left: 35px ;

            background-image: url('../image/section_1_top.jpg');

            background-repeat: no-repeat;

            background-position:center;

            background-size:100% auto;

        }

        .sidebar .mid{

            height: 5px;

            margin-top: 0;

            margin-bottom: 0;

            padding-left: 35px;

            background-image: url('../image/section_1_mid.jpg');

            background-repeat: no-repeat;

            background-position:center;

            background-size:100% auto;

        }

        .sidebar .bottom{

            height: 274px;

            margin-top: 0px;

            margin-bottom: 20px;;

            padding: 0;

            border: 0;

            border-bottom: 2px;

            border-style:dashed;

            padding-left: 35px ;

            background-image: url('../image/section_1_bottom.jpg');

            background-repeat: no-repeat;

            background-position:center;

            background-size:100% auto;

        }

        .news_container{

            height: 400px;

            margin-bottom: 20px;

            padding: 0;

            border: 0;

            border-bottom: 2px;

            border-style:dashed;

            padding-left: 35px ;

            display: flex;

            flex-direction: column; /* 将子元素垂直排列 */

        }

        .news{

            height:100px;

        }

        .news img {

            float: left;

            margin-right: 10px; /* 可选：增加图片与文本之间的间距 */

        }

        .news h3, .news .scroll-text {

            overflow: hidden; /* 清除浮动带来的布局问题 */

        }

        .main{

            height: 100%;

        }

        .welcome{

            height: 300px;

            border: 0;

            border-bottom: 2px;

            border-style: dashed;

            background-image: url('../image/section_3_bg.jpg');

            background-repeat: no-repeat;

            background-position:top 25px left 170px;

            background-size:auto;

        }

        .service{

            height: 400px;

            border: 0;

            border-bottom: 2px;

            border-style: dashed;

        }

        .grid_4.photo.alpha {

            display: grid;

            grid-template-columns: repeat(3, 1fr);

            grid-template-rows: repeat(2, 1fr);

            gap: 10px; /* 可以根据需要调整间距 */

            height: 260px;

            border: 0;

            border-right: 2px;

            border-style: dashed;

        }

        .grid_4.photo.alpha h2 {

            grid-column: span 3; /* 让段落跨越3列 */

            text-align: center; /* 居中对齐 */

            margin-bottom: 10px; /* 与图片之间的间距 */

        }

  

        .image-container {

            display: flex;

            justify-content: center;

            align-items: center;

            overflow: hidden;

        }

  

        .image-container img {

            max-width: 100%;

            max-height: 100%;

            object-fit: cover;

        }

  

        .contact{

            height: 260px;

        }

  

        .footer{

            height:88px;

            background-image: url('../image/footer_bg.jpg');

            background-repeat: repeat-x;

            background-position:center;

            background-size:100% auto;

            padding:20px;

            display: flex; /* 使用 Flexbox 布局 */

            justify-content: center; /* 水平居中 */

            align-items: center; /* 垂直居中 */

        }

        p ,h1, h2, h3{

            margin-top: 0.5em;

            margin-bottom: 0.5em;

        }

        .servie img{

            border-style: solid;

        }

    </style>

</head>

<body>

    <div class="container_12">

        <div class="grid_12 header">

            <div class="grid_1 alpha"></div>

            <div class="grid_10 just">

                <div class="push_1">

                    <h1 style="color:cornflowerblue;">JUST</h1>

                    <p>CSS Website Template</p>

                </div>

                <div class="nav">

                    <ul>

                        <li><a href="#">Home</a></li>

                        <li><a href="#">Portidolio</a></li>

                        <li><a href="#">Services</a></li>

                        <li><a href="#">Testimonial</a></li>

                        <li><a href="#">News & Events</a></li>

                        <li><a href="#">Contact</a></li>

                    </ul>

                </div>

                <div class="icon-container">

                    <div class="icon-row">

                        <img src="../image/icon_1.jpg" alt="Icon 1" class="icon">

                        <img src="../image/icon_2.jpg" alt="Icon 2" class="icon">

                        <img src="../image/icon_3.jpg" alt="Icon 3" class="icon">

                    </div>

                    <div class="icon-row">

                        <img src="../image/search.jpg" alt="Icon 4" class="icon first-icon">

                        <img src="../image/botton.jpg" alt="Icon 5" class="icon">

                    </div>

                </div>

            </div>

            <div class="grid_1 omega"></div>

        </div>

        <div class="grid_12 content">

            <div class="grid_4 sidebar omega">

                <div class="top">

                    <br />

                    <span class="one">

                        Testimonial

                    </span>

                    &nbsp;

                    <span class="two">

                        WHAT THAY SAY

                    </span>

                </div>

                <div class="mid">

  

                </div>

                <div class="bottom">

                    Nulla enim nibh, consectetuer sed, vestibulum elementum, sagittis nec, diam.      

                    <p></p>

                    Mauris blandit vehicula neque. Proin consectetuer. Donec venenatis. Cras urna metus, feugiat non, consectetuer quis, pretium quis, nunc.

                    <p></p>

                    Nullam pede purus, tempor a, imperdiet in, porttitor at, nulla. Aliquam elit risus, volutpat quis, mattis ac, elementum eget, mauris. In hac habitasse platea dictumst.      

                </div>

                <div class="news_container">

                    <h1>

                        News & Events

                    </h1>

                    <div class="news">

                        <img src="../image/menu_divider.jpg">

                        <h3>18 December 2020</h3>

                        <div class="scroll-text">

                            <marquee behavior="scroll" direction="up" onmouseover="this.stop();" onmouseout="this.start();">

                                <p>Pellen tesque dolor nulla, con gue vitae, frin gilla in, varius a, orci ma uris con.</p>

                            </marquee>

                        </div>

                    </div>

                    <div class="news">

                        <img src="../image/menu_divider.jpg">

                        <h3>22 December 2020</h3>

                        <div class="scroll-text">

                            <marquee behavior="scroll" direction="up" onmouseover="this.stop();" onmouseout="this.start();">

                                <p>Proin vel libero id erat venen atis accu msan. Nunc blan dit orci sit amet risus.</p>

                            </marquee>

                        </div>

                    </div>

                    <div class="news">

                        <img src="../image/menu_divider.jpg">

                        <h3>30 December 2020</h3>

                        <div class="scroll-text">

                            <marquee behavior="scroll" direction="up" onmouseover="this.stop();" onmouseout="this.start();">

                                <p>Duis pul vinar scele risque ante. Mor bit risti que, risus quis congue pul vinar.</p>

                            </marquee>

                        </div>

                    </div>

                </div>

            </div>

            <div class="grid_8 main alpha">

                <div class="welcome">

                    <h1>

                        Welcome

                    </h1>

                    <h1>

                        &nbsp;&nbsp;&nbsp;&nbsp;TO Creative IDEA

                    </h1>

                    <p>

                        This is a www.myweb.cn from www.myweb.cn. You may download, modify and apply this CSS layout for your

                        websites. Credit goes to full size for jQuery Full Size Image Plugin. Nunc blandit orci sit amet risus. Lorem ipsum

                        dolor sit amet, consectetuer adipiscing elit. Ut iaculis lacinia purus.

                    </p>

                    <p>

                        Aliquam magna. Phasellus id felis.Donec mollis aliquet ligula. Maecenas adipiscing elementum ipsum. Pellentesque vitae magna. Sed nec est. Suspendisse a nibh tristique justo rhoncus volutpat. Suspendisse vitae neque eget ante tristique vestibulum.

                    </p>

                </div>

                <div class="service">

                    <h1>Service</h1>

                    <div class="grid_3">

                        <img src="../image/img_1.jpg">

                        <h2>Creative Graphic Design</h2>

                        <p>

                            Aliquam sagittis molestie sapien. Nulla tellus risus, tincidunt vitae, sagittis vel, interdum at, erat. Duis vitae velit. Ut ultricies. Fusce sollicitudin nisl.

                        </p>

                    </div>

                    <div class="push_1 grid_3">

                        <img src="../image/img_2.jpg">

                        <h2>Special Web Design</h2>

                        <p>Phasellus tincidunt, tortor lacinia blandit commodo, nunc augue mattis eros, ut convallis est augue vel.</p>

                    </div>

                </div>

                    <div class="grid_4 photo alpha">

                        <h2>Photo Gallery</h2>

                        <div class="image-container">

                            <img src="../image/thumb_1.jpg" alt="Image 1">

                        </div>

                        <div class="image-container">

                            <img src="../image/thumb_2.jpg" alt="Image 2">

                        </div>

                        <div class="image-container">

                            <img src="../image/thumb_3.jpg" alt="Image 3">

                        </div>

                        <div class="image-container">

                            <img src="../image/thumb_4.jpg" alt="Image 4">

                        </div>

                        <div class="image-container">

                            <img src="../image/thumb_5.jpg" alt="Image 5">

                        </div>

                        <div class="image-container">

                            <img src="../image/thumb_6.jpg" alt="Image 6">

                        </div>

                    </div>

                <div class="grid_3 contact omega">

                    <h2>Contact Info.</h2>

                    <p>Pellentesque odio. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas</p>

                    <p>111/222 Lorem ipsum dolor sit,consectetuer adipiscing elit. Nunc quis sem nec, 10100</p>

                    <p>Tel : 010-100-0100</p>

                    <p>Fax : 020-200-0200</p>

                    <p>Email : info@yourcompany.com</p>

                </div>

            </div>        

        </div>

  

        <div class="grid_12 footer">

            <p>Copyright © 2020 Your Company Name | Designed by www.myweb.cn</p>

        </div>

    </div>

</body>

</html>
```
- # ==2021==
- ![[Pasted image 20241215232819.png]]
- ![[Pasted image 20241215232826.png]]

- ## index界面
```
<html>

    <head>

        <link href="css/960_12_col.css" rel="stylesheet">

        <style>

            body {

                background-color: darkslateblue;

            }

            .head {

                height: 150px;

            }

            .no1 {

                color: white;

            }

            .no2 {

                text-align: right;

                font-size: large;

            }

            .register {

                height: 250px;

                text-align: center;

            }

            .content {

                background-color: white;

                height: 500px;

            }

            .foot {

                height: 100px;

            }

            /* 水平导航栏样式 */

            .nav {

                list-style: none; /* 去掉默认的列表样式 */

                padding: 0; /* 去掉默认的内边距 */

                margin: 0; /* 去掉默认的外边距 */

                display: flex; /* 使用 Flexbox 布局 */

                justify-content: flex-end; /* 将导航栏靠右对齐 */

            }

            .nav li {

                margin-left: 5px; /* 为每个列表项添加左边距 */

            }

            a {

                color: white; /* 设置链接文字颜色 */

                text-decoration: none; /* 去掉链接的下划线 */

                padding: 5px; /* 为链接添加内边距 */

                display: block; /* 使链接成为块级元素 */

            }

            a:hover {

                background-color: rgba(255, 255, 255, 0.2); /* 鼠标悬停时的背景颜色 */

            }

            h1 ,h2{

                margin:0;

            }

            .no3{

                border-style:solid;

                border-color:white;

                height:30px;

                padding:10px;

                margin-top: 50px;

            }

            .no4 img{

                width:100%;

                height:auto;

                display: block;

                margin-bottom: 10px;

            }

            .no5 {

                margin-top:40px;

            }

        </style>

    </head>

    <body>

        <div class="container_12">

            <div class="grid_12 head">

                <div class="grid_4 push_1 no1">

                    <h1>STYLES</h1>

                    <h1>CONFERENCE</h1>

                </div>

                <div class="grid_4 push_2 no2">

                    <p style="color: aquamarine;">

                        August 24-26th——Chicago, IL

                    </p>

                    <ul class="nav">

                        <li>

                            <a href="#">HOME    </a>

                        </li>

                        <li>

                            <a href="#">SPEAKERS</a>

                        </li>

                        <li>

                            <a href="#">SCHEDULE</a>

                        </li>

                        <li>

                            <a href="#">VENUE</a>

                        </li>

                        <li>

                            <a href="register.html">REGISTER</a>

                        </li>

                    </ul>

                </div>

            </div>

            <div class="grid_12 register">

                <div class="grid_11 push_1">

                    <h2 style="color: aquamarine;">Dedicated to the Craft of Building Websites</h1>

                    <h2 style="color: aliceblue;">Every year the brightest web designers and front-end developers descend on </h1>

                    <h2 style="color: aliceblue;">Chicago to discuss the latest tech logies. Join us this August!</h1>

                    <div class="grid_2 push_4 no3">

                        <a href="register.html">REGISTER NOW</a>

                    </div>    

                </div>            

            </div>

            <div class="grid_12 content">

                <div class="grid_4 no4 alpha">

                   <h2>SPEAKERS</h2>

                   <img src="images/home/speakers.jpg" >

                   <h1>World-Class Speakers</h1>

                   <p>Joining us from all around the world are over twenty fantastic speakers, here to share their stories.</p>

  

                </div>

                <div class="grid_4 no4">

                    <h2>SCHEDULE</h2>

                   <img src="images/home/schedule.jpg" >

                   <h1>Three Inspiring Days</h1>

                   <p>Enjoy three inspiring and action-packed days of tals, gatherings, and all-around good times.</p>

                </div>

                <div class="grid_4 no4 omega">

                    <h2>VENUE</h2>

                   <img src="images/home/venue.jpg" >

                   <h1>The Chicago Theatre</h1>

                   <p>Within the heart of downtown Chicago, The Chicago Theatre will provide a beautiful conference venue.

                </p>

                </div>

            </div>

            <div class="grid_12 foot">

                <div class="grid_3 no5">

                   <h3>ⒸStyles Conference</h3>

                </div>

                <div class="grid_4 push_4 no5">

                    <ul class="nav">

                        <li>

                            <a href="#">HOME</a>

                        </li>

                        <li>

                            <a href="#">SPEAKERS</a>

                        </li>

                        <li>

                            <a href="#">SCHEDULE</a>

                        </li>

                        <li>

                            <a href="#">VENUE</a>

                        </li>

                        <li>

                            <a href="register.html">REGISTER</a>

                        </li>

                    </ul>

                </div>

  

            </div>

        </div>

    </body>

</html>
```
- ## register
```
<html>

    <head>

        <link href="css/960_12_col.css" rel="stylesheet">

        <style>

            body {

                background-color: darkslateblue;

            }

            .head {

                height: 150px;

            }

            .no1 {

                color: white;

            }

            .no2 {

                text-align: right;

                font-size: large;

            }

            .register {

                height: 250px;

                text-align: center;

                background:linear-gradient(to right, aquamarine, white);

            }

            .non3{

                margin-top:60px ;

            }

            .content {

                background-color: white;

                height: 500px;

            }

            .foot {

                height: 100px;

            }

            /* 水平导航栏样式 */

            .nav {

                list-style: none; /* 去掉默认的列表样式 */

                padding: 0; /* 去掉默认的内边距 */

                margin: 0; /* 去掉默认的外边距 */

                display: flex; /* 使用 Flexbox 布局 */

                justify-content: flex-end; /* 将导航栏靠右对齐 */

            }

            .nav li {

                margin-left: 5px; /* 为每个列表项添加左边距 */

            }

            a {

                color: white; /* 设置链接文字颜色 */

                text-decoration: none; /* 去掉链接的下划线 */

                padding: 5px; /* 为链接添加内边距 */

                display: block; /* 使链接成为块级元素 */

            }

            a:hover {

                background-color: rgba(255, 255, 255, 0.2); /* 鼠标悬停时的背景颜色 */

            }

            h1 ,h2, h3{

                margin:0;

            }

            .no5 {

                margin-top:40px;

            }

            label{

                display: block;

            }

            .form-group{

                margin-bottom: 50px;

            }

            button[type="submit"] {

                background-color: green; /* 设置提交按钮的背景颜色为绿色 */

                color: white; /* 设置提交按钮的文字颜色为白色 */

                padding: 10px 20px; /* 设置按钮的内边距 */

                border: none; /* 去掉按钮的边框 */

                border-radius: 5px; /* 设置按钮的圆角 */

                cursor: pointer; /* 设置按钮的鼠标指针样式 */

            }

            button[type="submit"]:hover {

                background-color: darkgreen; /* 鼠标悬停时按钮的背景颜色 */

            }

        </style>

    </head>

    <body>

        <div class="container_12">

            <div class="grid_12 head">

                <div class="grid_4 push_1 no1">

                    <h1>STYLES</h1>

                    <h1>CONFERENCE</h1>

                </div>

                <div class="grid_4 push_2 no2">

                    <p style="color: aquamarine;">

                        August 24-26th——Chicago, IL

                    </p>

                    <ul class="nav">

                        <li>

                            <a href="#">HOME    </a>

                        </li>

                        <li>

                            <a href="#">SPEAKERS</a>

                        </li>

                        <li>

                            <a href="#">SCHEDULE</a>

                        </li>

                        <li>

                            <a href="#">VENUE</a>

                        </li>

                        <li>

                            <a href="register.html">REGISTER</a>

                        </li>

                    </ul>

                </div>

            </div>

            <div class="grid_12 register">

                <div class="grid_11 non3">

                    <h2 style="color:darkgreen;">Register</h1>

                        <br \>

                    <h3 style="color:rgb(208, 203, 212);">Every year we aim to have an unbelievable time, and this year we'd love it for you to join us.</h1>

                    <h3 style="color:rgb(208, 203, 212);">Conference passes only cost $99, one of the best values you'll find.</h1>

                </div>            

            </div>

            <div class="grid_12 content">

                <div class="grid_6 push_1">

                    <h3 style="color: darkgreen;">Purchase a Conference Pass</h3>

                    <p style="color: rgb(114, 127, 127);">$99 PER PASS</p>

                    <p> Purchase your Styles Conference pass using the form to the right. Multiple passes may be purchased within the same order, so feel free to bring a friend or two along. Once your order is finished we’ll follow up and provide a receipt for your purchase. See you soon!</p>

                    <h3>Why Attend?</h3>

                    <ul>

                        <li>Over twenty world-class speakers</li>

                        <li>One full day of workshops and two full days of presentations</li>

                        <li>Hosted at The Chicago Theatre, a historical landmark</li>

                        <li>August in Chicago is simply amazing</li>

                    </ul>

                </div>

                <div class="grid_4 push_1">

                    <form>

                    <div class="form-group">

                        <label for="username">Name</label>

                        <input type="text" name="username" placeholder="Full name" required>

                    </div>

                    <div class="form-group">    

                        <label for="email">Email</label>

                        <input type="email" name="email" placeholder="Email address" required>

                    </div>

                    <div class="form-group">

                        <label for="number">Number of Passes</label>

                        <select name="number"required>

                            <option value="1">1</option>

                            <option value="2">2</option>

                            <option value="3">3</option>

                            <option value="4">4</option>

                            <option value="5">5</option>

                            <option value="6">6</option>

                            <option value="7">7</option>

                            <option value="8">8</option>

                            <option value="9">9</option>

                            <option value="10">10</option>

                        </select>

                    </div>

                    <div class="form-group">

                        <label for="comment">Comments</label>

                        <textarea name="comment" rows="6" required></textarea>

                    </div>

                    <div class="form-group">

                        <button type="submit">

                            PURCHASE

                        </button>

                    </div>

                </form>

                </div>

            </div>

            <div class="grid_12 foot">

                <div class="grid_3 no5">

                   <h3>ⒸStyles Conference</h3>

                </div>

                <div class="grid_4 push_4 no5">

                    <ul class="nav">

                        <li>

                            <a href="#">HOME</a>

                        </li>

                        <li>

                            <a href="#">SPEAKERS</a>

                        </li>

                        <li>

                            <a href="#">SCHEDULE</a>

                        </li>

                        <li>

                            <a href="#">VENUE</a>

                        </li>

                        <li>
                            <a href="register.html">REGISTER</a>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </body>
</html>
```

- # ==电影==
- ![[Pasted image 20241215233756.png]]
```
<!DOCTYPE html>

<html lang="zh-CN">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>电影推荐</title>

    <style>

        body {

            font-family: Arial, sans-serif;

            background-color:cornflowerblue;

            margin: 0;

            padding: 20px;

            color: aliceblue;

        }

        .container {

            display: flex;

            flex-wrap: wrap;

            justify-content: space-between;

            max-width: 1200px;

            margin: 0 auto;

        }

        .header {

            display: block;

            text-align: center;

        }

  

        .movie {

            flex: 0 0 calc(33.33% - 20px);

            margin-bottom: 20px;

            box-sizing: border-box;

            padding: 10px;

            background-color:violet;

            text-align: center;

            border: 1px solid #ddd;

            border-radius: 4px;

            transition: transform 0.3s, box-shadow 0.3s;

        }

        .movie:hover {

            transform: scale(1.05);

            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);

        }

        .movie img {

            width: 100%;

            height: auto;

            display: block;

            border-radius: 4px 4px 0 0;

            margin-bottom: 10px;

        }

        .movie h3 {

            font-size: 20px;

            margin: 10px 0;

        }

        a {

            text-decoration: none;

            color: aliceblue;

        }

    </style>

</head>

<body>

    <div class="header">

        <h1>3 Movies You Can't Miss</h1>

    </div>

    <div class="container">

        <div class="movie">

            <a href="https://movie.douban.com/subject/25932086/" target="_blank">  

                <img src="movie1.jpg" alt="电影 1">

                <h3>Who Am I - Kein System ist sicher</h3>

            </a>

            <p>本杰明是一个这样的人：三次元现实世界中，他是一个十足的屌丝&Loser，难以找到存在感，没有时尚感、没有朋友，也没有女朋友。但是二十五岁的他却是一个的电脑极客，拥有对数字技术不可思议的天

                赋。而影片中另一位主人公马克思是一个渴望“黑客世界”的潜在革命者，他注意到了本杰明在 网络方面的惊人才华，马克思、本杰明和神童斯蒂芬以及保罗私人组建了黑客组织CLAY，并且为了正义入侵国际安全系统。他们凭借高超黑客技术的所为引起了德国秘密警察组织、

                欧洲刑警组织的重视，并且一个邪恶的黑客将他们视作威胁，想要将他们除去。本杰明因此感觉到自己正在面临生死攸关的考验，并且他们的目标似乎不值得他付出如此大的代价……</p>

        </div>

        <div class="movie">

            <a href="https://movie.douban.com/subject/27060077/" target="_blank">  

                <img src="movie2.jpg" alt="电影 2">

                <h3>绿皮书</h3>

            </a>

            <p>　托尼（维果·莫腾森 Viggo Mortensen 饰）是一个吊儿郎当游手好闲的混混，在一家夜总会做侍者。这间夜总会因故要停业几个月，可托尼所要支付的房租和生活费不会因此取消，所以他的当务之急是去寻找另一份工作来填补这几个月的空缺。在这个节骨眼上，一位名叫唐雪莉（马赫沙拉·阿里 Mahershala Ali 饰）的黑人钢琴家提出雇佣托尼。

                　　唐雪莉即将开始为期八个星期的南下巡回演出，可是，那个时候南方对黑人的歧视非常的严重，于是托尼便成为了唐雪莉的司机兼保镖。一路上，两人迥异的性格使得他们之间产生了很多的矛盾，与此同时，唐雪莉在南方所遭受的种种不公平的对待也让托尼对种族歧视感到深恶痛绝。</p>

        </div>

        <div class="movie">

            <a href="https://movie.douban.com/subject/27605698/"  target="_blank">  

                <img src="movie3.jpg" alt="电影 3">

                <h3>西红柿首富</h3>

            </a>

            <p>西虹市丙级球队大翔队的守门员王多鱼（沈腾 饰）因比赛失利被教练开除，一筹莫展之际王多鱼突然收到神秘人士金老板（张晨光 饰）的邀请，被告知自己竟

                然是保险大亨王老太爷（李立群 饰）的唯一继承人，遗产高达百亿！但是王老太爷给出了一个非常奇葩的条件，那就是要求王多鱼在一个月内花光十亿，还不能告诉身边人，否则失去继承权。王多鱼毫不犹豫签下了“军令状”，与好友庄强（张一鸣 饰）以及财务夏竹（宋芸桦 饰）一起开启了“挥金之旅”，即将成为西虹市首富的王多鱼，第一次感受到了做富人的快乐，同时也发现想要挥金如土实在没有那么简单！</p>

        </div>

    </div>

</body>

</html>
```

- # ==固定宽度布局1==
- ![[Pasted image 20241215234140.png]]
```
<!DOCTYPE html>

<html lang="zh">

    <head>

        <meta charset="UTF-8">

        <title>固定宽度页面布局</title>

            <style>

            .header {

                position:relative;

                background-color: aquamarine;

                height: 100px;

                width:2000px;

                text-align: left;

                padding: 0px;

                margin:2.5px;

            }

            .navigation {

                position: relative;

                background-color: aquamarine;

                height: 70px;

                width:2000px;

                text-align: left;

                padding: 0px;

                margin:2.5px;

            }

            .main {

                position: relative;

                float:left;

                background-color:khaki;

                height: 500px;

                width:1300px;

                text-align: left;

                padding: 0px;

                margin:2.5px;

            }

            .right {

                position: relative;

                float:right;    

                background-color:lightsalmon;

                height: 500px;

                width:350px;

                text-align: left;

                padding: 0px;

                margin:2.5px;

            }

            .footer {

                position: relative;

                float: left;

                background-color:aquamarine;

                height: 100px;

                width:2000px;

                text-align: left;

                padding: 0px;

                margin:2.5px;

            }

  
  

        </style>

    </head>

    <body>

        <div class="header">

            <p>这是头部信息区</p>

        </div>

        <div class="navigation">

            <p>这是导航信息区</p>

        </div>

        <div class="main">

            <p>这是主体信息区</p>

        </div>

        <div class="right">

            <p>这是右侧信息区</p>

        </div>

  
  

        <div class="footer">

            <p>这是版权信息区</p>

        </div>

  
  

    </body>

  
  

</html>	
```

- # ==固定宽度页面布局2==
- ![[Pasted image 20241215234349.png]]
```
<!DOCTYPE html>

<html lang="zh">

<head>

    <meta charset="UTF-8">

    <title>固定宽度页面布局</title>

    <style>

        body {

            margin: 2.5px;

            font-family: Arial, sans-serif;

        }

        .header {

            background-color: #6CCFF6;

            height: 100px;

            text-align: left;

            padding: 10px;

            color: black;

        }

        .container {

            display: flex;

            flex-direction: row;

            height: 3000px;

        }

        .sidebar {

            background-color: #A2D5F2;

            width: 200px;

            padding: 10px;

            box-sizing: border-box;

        }

        .content {

            background-color: #B3E5FC;

            flex-grow: 1;

            padding: 10px;

            box-sizing: border-box;

        }

    </style>

</head>

<body>

    <div class="header">

        <p>这是头部信息区</p>

    </div>

    <div class="container">

        <div class="sidebar">

            <p>这是左侧边信息区</p>

        </div>

        <div class="content">

            <p>2列固定宽度左窄右宽型 + 头部</p>

        </div>

    </div>

</body>

</html>
```
- # ==弹性页面布局==
- ![[Pasted image 20241215234624.png]]
```
<!DOCTYPE html>

<html lang="zh">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>弹性页面布局</title>

    <style>

        html, body {

            height: 100%;

            margin: 0%;

            font-family: Arial, sans-serif;

        }

        header {

            background-color: #4CAF50;

            padding: 10px;

            text-align: center;

            height: 20%;

        }

        nav {

            background-color: #4CAF50;

            padding: 15px;

            height: 10%;

        }

        .container {

            display: flex;

            flex: 1;

            height: 55%;

        }

        .sidebar {

            background-color: #4CAF50;

            width: 200px;

            padding: 15px;

        }

        .main {

            flex: 1;

            background-color: #FFEB3B;

            padding: 15px;

        }

        footer {

            background-color: #4CAF50;

            text-align: center;

            padding: 10px;

            height: 15%;

        }

    </style>

</head>

<body>

  

<header>

    <h1>这是头部信息区</h1>

</header>

  

<nav>

    <h2>这是导航菜单区</h2>

</nav>

  

<div class="container">

    <div class="sidebar">

        <h3>这是左侧边信息区</h3>

    </div>

    <div class="main">

        <h3>2列左侧固定宽度右侧自适应宽度，指定高度+头部+导航+尾部</h3>

    </div>

</div>

  

<footer>

    <p>这是版权信息区</p>

</footer>

  

</body>

</html>
```
- # ==研讨会==
- ![[Pasted image 20241215234952.png]]
- 
```
<!DOCTYPE html>

<html lang="zh-CN">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>2015年CERNET华东北地区年会</title>

    <style>

        body {

            font-family: Arial, sans-serif;

            margin: 0;

            padding: 0;

            background-color: #f9f9f9;

        }

  

        header .banner {

            background-color: #5b2d86;

            color: #fff;

            text-align: center;

            padding: 20px;

        }

  

        ul {

            list-style-type: none;

            list-style-image:url('../web/屏幕截图\ 2024-11-28\ 112256.png') ;

        }

        nav ul {

            background-color: #4b2f5b;

            list-style: none;

            text-align: center;

            padding: auto;

            margin: 0;

            height: 50px;

            line-height: 50px;

        }

  

        nav ul li {

            display: inline;

            padding: 15px 30px;

        }

  

        nav ul li a {

            color: #fff;

            text-decoration: none;

        }

  

        main {

            display: flex;

            padding: 20px;

            max-width: 800px;

            margin: 20px auto;

            background-color: #fff;

            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);

        }

  

        .left, .right {

            flex: 1;

            margin: 10px;

        }

  

        h2 {

            color: #5b2d86;

        }

  

        footer {

            background-color: #4b2f5b;

            color: #fff;

            text-align: center;

            padding: 10px 0;

            width: 100%;

            bottom: 0;

        }

  

        img {

            max-width: 100%;

            height: auto;

        }

        a {

            text-decoration: none;

            color: black;

        }

    </style>

</head>

<body>

    <header>

        <div class="banner">

            <img src="../web/header23.png" alt="CERNET Logo">

        </div>

    </header>

  

    <nav>

        <ul>

            <li><a href="#">首&nbsp;&nbsp;&nbsp;页</a></li>

            <li><a href="#">会议介绍</a></li>

            <li><a href="#">潍坊介绍</a></li>

            <li><a href="#">日程安排</a></li>

            <li><a href="#">大会报告</a></li>

            <li><a href="#">宾馆交通</a></li>

            <li><a href="#">资料下载</a></li>

            <li><a href="#">会议注册</a></li>

            <li><a href="#">联系我们</a></li>

  
  

        </ul>

    </nav>

  

    <main>

        <div class="left">

            <h2>会议概要</h2>

            <p>

                2015年CERNET华东北地区教育信息化技术研讨大会

                <br /><br />

                时间：2015年4月22日至4月25日

                <br /><br />

                报到时间：2015年4月22日

                <br /><br />

                地点：山东省潍坊市

                <br /><br />

                会议主题：先进网络技术、信息化规划与学校信息化实践、信息技术推动教育教学变革、技术应用研讨及工作交流等。

                <br /><br />

                主办：CERNET华东北地区网络中心、CERNET安徽省网络中心、CERNET山东省网络中心、山东省教育技术与装备协会

                <br /><br />

                承办：潍坊医学院

                </p>

            </p>

            <h2>会议介绍</h2>

            <p>

                2015年CERNET华东北地区教育信息化技术研讨大会

                <br /><br />

                时间：2015年4月22日至4月25日

                <br /><br />

                报到时间：2015年4月22日

                <br /><br />

                地点：山东省潍坊市

                <br /><br />

                会议主题：先进网络技术、信息化规划与学校信息化实践、信息技术推动教育教学变革、技术应用研讨及工作交流等。

                <br /><br />

                主办：CERNET华东北地区网络中心、CERNET安徽省网络中心、CERNET山东省网络中心、山东省教育技术与装备协会

                <br /><br />

                承办：潍坊医学院

                </p>

            </p>

        </div>

  

        <div class="right">

            <h2>会议动态</h2>

            <ul>

                <li><a href="#"  style="color: red;">潍坊天气预报</a></li>

                <li><a href="#">在线注册</a></li>

                <li><a href="#">信息修改</a></li>

            </ul>

  

            <h2>宾馆地图</h2>

            <img src="../web/ditu.gif" alt="宾馆地图">

        </div>

    </main>

  

    <footer>

        <p>&copy; 2015 CERNET华东北地区年会. All rights reserved.</p>

    </footer>

</body>

</html>
```

- # ==简易画廊设计==
```
<!DOCTYPE html>

<html lang="zh-CN">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>简易灯箱画廊设计</title>

    <style>

        body {

            background-color: #59c4cc;

            text-align: center;

            font-family: 方正楷体_GB2312, 宋体;

        }

  

        .gallery {

            margin-top: 20px;

            display: flex;

            justify-content: center;

            gap: 0;

        }

  

        .gallery img {

            width: 100%;

            height: 100%;

            object-fit: cover;

            cursor: pointer;

            border: 2px solid #ccc;

            transition: border-color 0.3s;

        }

  

        .gallery img:hover {

            border-color: orange;

        }

  

        .large-image {

            margin-top: 20px;

            max-width: 80%;

            height: auto;

            border: 2px solid white;

        }

        .image-container {

        position: relative;

        height: 100px;

        width: 100px;

        }

  

    </style>

</head>

<body>

    <h1>简易灯箱画廊设计</h1>

    <div class="gallery">

        <div class="image-container">

            <div class="overlay-text">T1</div>

            <img src="../trees/t1.jpg" alt="T1" onclick="showImage(this)">

        </div>

        <div class="image-container">

            <div class="overlay-text">T2</div>

            <img src="../trees/t2.jpg" alt="T2" onclick="showImage(this)">

        </div>

        <div class="image-container">

            <div class="overlay-text">T3</div>

            <img src="../trees/t3.jpg" alt="T3" onclick="showImage(this)">

        </div>

        <div class="image-container">

            <div class="overlay-text">T4</div>

            <img src="../trees/t4.jpg" alt="T4" onclick="showImage(this)">

        </div>

        <div class="image-container">

            <div class="overlay-text">T5</div>

            <img src="../trees/t5.jpg" alt="T5" onclick="showImage(this)">

        </div>

        <div class="image-container">

            <div class="overlay-text">T6</div>

            <img src="../trees/t6.jpg" alt="T6" onclick="showImage(this)">

        </div>

    </div>

    <img id="largeImage" class="large-image" src="../trees/t1.jpg" alt="Large">

  

    <script>

        function showImage(element)

         {

            const largeImage = document.getElementById('largeImage');//获取大图元素(老师这是我自己写的注释不是AI哈)

            largeImage.src = element.src;

  

            const images = document.querySelectorAll('.gallery img');//获取所有图片元素(老师这是我自己写的注释不是AI哈)

            largeImage.src = element.src;

            images.forEach(img => img.style.borderColor = '#ccc');

            element.style.borderColor = 'red';

        }

    </script>

</body>

</html>
```

- # 多媒体
- ![[Pasted image 20241215235139.png]]
- 
```
<!DOCTYPE html>

<html lang="zh">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>明月几时有</title>

    <style>

        body {

            text-align: center;

            margin: 0;

            font-family: Arial, sans-serif;

        }

        header {

            background-color: #ffffff;

            padding: 10px;

            border-bottom: 5px solid #0000ff;

        }

        h1 {

            margin: 10px;

        }

        .lyrics {

            color: #000080;

            margin: 20px;

            line-height: 1.8;

        }

        .media-container {

            display: flex;

            justify-content: center;

            background-color: #c0ffb3;

            padding: 20px 0;

            border-top: 5px solid #ff0000;

            border-bottom: 5px solid #ff0000;

        }

        .media {

            margin: 0 20px;

        }

        footer {

            background-color: #00bfff;

            padding: 10px;

            font-size: 18px;

        }

    </style>

</head>

<body>

    <header>

        <h1>明月几时有</h1>

    </header>

    <div class="lyrics">

        <p>明月几时有？把酒问青天。<br>

        不知天上宫阙，今夕是何年。<br>

        我欲乘风归去，又恐琼楼玉宇，高处不胜寒，起舞弄清影，何似在人间。<br>

        转朱阁，抵绮户，照无眠。<br>

        不应有恨，何事偏向别时圆。<br>

        人有悲欢离合，月有阴晴圆缺，此事古难全。<br>

        但愿人长久，千里共婵娟。</p>

    </div>

    <div class="media-container">

        <div class="media">

            <audio controls>

                <source src="../embed/蔡琴明月几时有.mp3" type="audio/mp3">

                您的浏览器不支持音频播放。

            </audio>

        </div>

        <div class="media">

            <video width="320" height="240" controls>

                <source src="../embed/htmlexample.mp4" type="video/mp4">

                您的浏览器不支持视频播放。

            </video>

        </div>

    </div>

    <footer>

        欢迎来到我的多媒体世界！

    </footer>

</body>

</html>
```

- # ==导航栏==
- ![[Pasted image 20241215235433.png]]
```
<!DOCTYPE html>

<html lang="zh">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>网站导航</title>

    <style>

        .first-menu {

            border-bottom: 5px solid blue;

            padding: 10px;

            text-align: center;

            color: blue;

        }

        .second-menu ul {

            list-style-type: none; /* 去掉默认的列表样式 */

            margin: 0;

            padding: 0;

            overflow: hidden; /* 清除浮动 */

            background-color: #f1f1f1; /* 设置背景颜色 */

        }

        .second-menu li {

            float: left; /* 将列表项水平排列 */

        }

        .second-menu li a {

            display: block;

            color: blue;

            text-align: center;

            padding: 14px 16px;

            text-decoration: none;

        }

        .second-menu li a:hover {

            color: pink; /* 鼠标悬停时颜色变为粉红色 */

        }

  

        h1 {

            text-align: center;

            margin-top: 50px;

        }

    </style>

</head>

<body>

    <h1>使用段落标记和超链接实现网站导航</h1>

    <div class="first-menu">

        <a href="http://www.baidu.com/">百度</a>

        <a href="http://www.sina.com.cn/">新浪</a>

        <a href="http://www.qq.com/">腾讯</a>

        <a href="http://www.sohu.com/">搜狐</a>

        <a href="http://www.163.com/">网易</a>

        <a href="http://www.google.com.hk/">谷歌</a>

    </div>

    <h1>利用无序列表实现水平导航条</h1>

    <div class="second-menu">

        <ul>

            <li><a href="http://www.baidu.com/">百度</a></li>

            <li><a href="http://www.sina.com.cn/">新浪</a></li>

            <li><a href="http://www.qq.com/">腾讯</a></li>

            <li><a href="http://www.sohu.com/">搜狐</a></li>

            <li><a href="http://www.163.com/">网易</a></li>

            <li><a href="http://www.google.com.hk/">谷歌</a></li>

        </ul>

    </div>

</body>

</html>
```

- # 页面内超链接
- ![[Pasted image 20241215235632.png]]
```
<!DOCTYPE html>

<html lang="zh">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>专业课程导航</title>

    <style>

        body {

            font-family: Arial, sans-serif;

            margin: 20px;

        }

        h1 {

            text-align: center;

            margin-bottom: 30px;

        }

        .menu {

            margin-bottom: 20px;

        }

        .menu a {

            color: blue;

            text-decoration: none;

            margin-right: 15px;

        }

        .menu a:hover {

            color: red;

        }

        section {

            margin-bottom: 20px;

        }

        .link {

            color: blue;

            text-decoration: none;

        }

        .link:hover {

            color: red;

        }

    </style>

</head>

<body>

  

<h1>专业课程导航</h1>

  

<div class="menu">

    <a href="#english">英语</a>

    <a href="#math">高数</a>

    <a href="#physics">大学物理</a>

</div>

  

<section id="english">

    <h2>英语</h2>

    <p>

       &nbsp;&nbsp;&nbsp;&nbsp;基础英语、高级英语、报刊选读、视听、口语、英语写作、翻译理论与实践、语言理论、语言学概论、主要英语国家文学史及文学作品选读、主要英语国家国情等      

        <a href="#" class="link">返回</a>

    </p>

</section>

  

<section id="math">

    <h2>高数</h2>

    <p>

        &nbsp;&nbsp;&nbsp;&nbsp;高等数学》课程介绍随着科学技术的迅猛发展数学正日益成为各学科进行科学研究的重要手段和工具。高等数学是近代数学的基础是理科各专业和经济管理专业类学生的必修课也是在现代科学技术、经济管理、人文科学中应用最广泛的一门课程。因此学好这门课程对学生今后的发展是至关重要的。本课程是学生进入大学后学习的第一门重要的数学基础课。通过本课程的教学使学生掌握处理数学问题的思想和方法培养学生科学思维能力同时为后续课程的学习奠定良好的基础。

        <a href="#" class="link">返回</a>

    </p>

</section>

  

<section id="physics">

    <h2>大学物理</h2>

    <p>

        &nbsp;&nbsp;&nbsp;&nbsp;以物理学基础为内容的大学物理课程，是理工科个专业学生一门重要的通识性的必修基础课。大学物理课程既为学生打好必要的物理基础，又在培养学生科学的世界观，增强学生分析问题和解决问题的能力，培养学生的探索精神、创新意识等方面，具有其他课程不能替代的重要作用。

        <a href="#" class="link">返回</a>

    </p>

</section>

  

</body>

</html>
```

- # ==二级导航菜单==
- ![[Pasted image 20241216000116.png]]
```
<!DOCTYPE html>

<html lang="zh">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>带有二级菜单的导航栏</title>

    <style>

        body {

            font-family: Arial, sans-serif;

            margin: 0;

            padding: 0;

        }

        /* 导航栏样式 */

        .navbar {

            background-color: #333;

            overflow: hidden;

        }

  

        .navbar a {

            float: left;

            display: block;

            color: white;

            text-align: center;

            padding: 14px 16px;

            text-decoration: none;

            position: relative; /* 使二级菜单能够相对于它定位 */

        }

  

        .navbar a:hover {

            background-color: #ddd;

            color: black;

        }

  

        /* 二级菜单样式 */

        .dropdown {

            display: none; /* 默认隐藏 */

            position: absolute;

            background-color: #f9f9f9;

            min-width: 160px;

            z-index: 1;

        }

  

        .dropdown a {

            float: none;

            color: black;

            padding: 12px 16px;

            text-decoration: none;

            text-align: left;

        }

  

        .dropdown a:hover {

            background-color: #ddd;

        }

  

        /* 添加一个容器以包含链接 */

        .dropdown-content {

            float: left;

            overflow: hidden;

        }

  

        .dropdown-content:hover .dropdown {

            display: block; /* 显示下拉菜单 */

        }

    </style>

</head>

<body>

  

    <div class="navbar">

        <a href="#home">首页</a>

        <div class="dropdown-content">

            <a href="#about">关于我们</a>

            <div class="dropdown">

                <a href="#team">团队</a>

                <a href="#history">历史</a>

            </div>

        </div>

        <a href="#services">服务</a>

        <a href="#contact">联系</a>

    </div>

  

    <div style="padding:20px;">

  

        <h1>欢迎来到我的网页!</h1>

        <p>这里是内容区域。</p>

    </div>

  

</body>

</html>
```
- # ==表单==
- ![[Pasted image 20241216000211.png]]
```
<html>

    <head>

             </head>

    <body>

        <form action="#" method="post">

  

        </form>

        <p>username: <input type="text" name="username" maxlenth="12" size="20" required="required"></p>

        <p>password: <input type="password" name="password" maxlenth="12" size="20" /></p>

        <p>gender: <input type="radio" name="gender" id="m">

            <label for="m">Male</label>

            <input type="radio" id="f" name="gender"><label for="f">Female</label></p>

        <p>age: <input type="number" name="age" min="18" max="65"></p>

        <p>email: <input type="email" name="email" size="30"></p>

        <p>website: <input type="url" name="website" size="30"></p>

        <p>date: <input type="date" name="date"></p>

        <p>time: <input type="time" name="time"></p>

        <p>color: <input type="color" name="color"></p>

        <p>file: <input type="file" name="file"></p>

        <p>textarea: <textarea name="textarea" rows="5" cols="30"></textarea></p>

        <p>select: <select name="select">

            <option value="option1">Option 1</option>

            <option value="option2">Option 2</option>

            <option value="option3">Option 3</option>

        </select></p>

        <p>checkbox: <input type="checkbox" name="checkbox1">Checkbox 1

            <input type="checkbox" name="checkbox2">Checkbox 2

            <input type="checkbox" name="checkbox3">Checkbox 3

        </p>

        <p>radio: <input type="radio" name="radio1">Radio 1

            <input type="radio" name="radio2">Radio 2

            <input type="radio" name="radio3">Radio 3

        </p>

        <p>volume: <input type="range" name="volume" min="0" max="10"></p>

        <p>score: <input type="number" name="score" min="0" max="10" step="0.5"></p>

        <p>upload: <input type="file" name="upload"></p>

  
  
  
  
  

        <p>submit: <input type="submit" value="Submit"></p>

        <p>reset: <input type="reset" value="Reset"></p>

  

    </body>

</html>
```
