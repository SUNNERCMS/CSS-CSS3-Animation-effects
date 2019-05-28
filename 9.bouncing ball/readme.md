## 效果演示
![](https://github.com/SUNNERCMS/CSS-CSS3-Animation-effects/blob/master/animation-gif/9.bouncing%20ball.gif)
### 代码部分
```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>bouncing ball</title>
    <style>
        body{
            margin:0;
            height:100vh;
            display:flex;
            align-items:center;
            justify-content:center;
            background:linear-gradient(#666,#333);
        }
        .box{
            position:relative;
            font-size:10px;
            width:30em;
            height:20em;
            background-color:steelblue;
            border:0.5em solid #222;
        }
        .box::before{
            content:'';
            position:absolute;
            width:2em;
            height:2em;
            border-radius:50%;
            background-color:silver;
            box-shadow:inset -0.3em -0.3em 0.5em rgba(0,0,0,0.6);
            animation: moveX 2s linear infinite alternate,
                        moveY 2.5s linear infinite alternate;
        }
        @keyframes moveX{
            from{
                left:0;
                }
                /* 下面的30em - 20em:(1)calc计算属性计算符号要有间隔（2）box的盒宽度减去小球的宽度，就是小球在盒内的移动距离值 */
            to{
                left:calc(30em - 2em);
            }
        }
        @keyframes moveY{
            from{
                top:0;
            }
            to{
                top:calc(20em - 2em);
            }
        }
    </style>
</head>
<body>
    <div class="box"></div>
</body>
</html>
<!-- 原理：物理的速度合成，用动画的移动方向和速度表示 -->
```
