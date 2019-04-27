### 动画效果：
![](https://github.com/SUNNERCMS/CSS-CSS3-Animation-effects/blob/master/animation-gif/8.button%20hover.gif)
### 代码部分：
```HTML
    <ul>
        <li>home</li>
        <li>address</li>
        <li>iphone</li>
        <li>Name</li>
    </ul>
```
```CSS
    <style>
        body{
            margin:0;
            height:100vh;
            display: flex;
            justify-content:center;
            align-items:center;
            background-color:lightgoldenrodyellow;
        }
        ul{
            padding:0;
            list-style-type:none;
        }
        li{
            font-size:25px;
            width:8em; /*这里的em是相对于上面的字体大小25px计算的，宽：200px*/
            height:2em;
            text-align:center;
            line-height:2em;
            font-family: sans-serif;
            text-transform:capitalize;
            position:relative;
            margin:0.8em;
        }
        /* 添加了左右两个圆点 */
        li::before,li::after{
            content:'';
            position:absolute;
            width:0.6em;
            height:0.6em;
            background-color:gainsboro;
            top:calc(50% - 0.3em);
            border-radius:50%;
            transition:0.5s cubic-bezier(0.5, -0.5, 0.25, 1.5);
        }
        li::before{left:0; z-index:-1;}
        li::after{right:0;z-index:-2;}
        /* 添加悬浮效果 */
        li:hover{
            color:white;
        }
        /* 给前后伪元素添加悬浮效果，注意先后顺序，先是hover后是伪元素 */
        li:hover::before,li:hover::after{
            width:100%;
            height:100%;
            border-radius:0;
            background-color:dodgerblue;
        }

        li:hover::before{
            top:0;
            left:-0.2em;
        }
        li:hover::after{
            right:-0.2em;
            filter:brightness(0.8);
        }

    </style>
```
