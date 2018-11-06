## 效果演示
![](https://github.com/SUNNERCMS/CSS-CSS3-Animation-effects/blob/master/animation-gif/4.%E6%BB%91%E5%8A%A8%E5%88%87%E6%8D%A2%E5%BC%80%E5%85%B3.gif)
#### 代码部分
```html
<input type="checkbox" class="toggle">
<div class="switch">
  <div class="inner">
    <div class="disc"></div>
  </div>
</div>
  
```
```CSS
body{
  margin:0;
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  background-color:darkseagreen;
}
:root{
  --font-size:20px;
}
/*这是最外面的椭圆*/
.switch{
  position:absolute;
  width:10em;
  height:5em;
  background:linear-gradient(silver,whitesmoke);
  border-radius:2.5em;
  display:flex;
  justify-content:center;
  align-items:center;
}
/*内椭圆，即：按钮滑动部分的背景*/
.switch .inner{
  position:absolute;
  width:8em;
  height:3.5em;
  background:linear-gradient(dimgray,silver);
  border-radius:2em;
  box-shadow:0 0 1.5em rgba(0,0,0,0.5),inset;
}
/*按钮的底层*/
.switch .inner .disc{
  position:absolute;
  left:0px;
  width:3.5em;
  height:3.5em;
  background:linear-gradient(to top,silver,whitesmoke);
  border-radius:50%;
  box-shadow:0 0.4em 0.6em rgba(0,0,0,0.2);
  display:flex;
  justify-content:center;
  align-items:center;
  transition:left 0.5s ease-in-out;
}
/*按钮的上层，比这一层小点，然后通过反转颜色进行渐变，造成视觉立体化*/
.switch .inner .disc::before{
  content:"OFF";
  font-family:sans-serif;
  color:gray;
  text-align:center;/*实现字体的垂直水平居中*/
  line-height:calc(3.5em * 0.8);
  width:80%;
  height:80%;
  background:linear-gradient(silver,whitesmoke);
  border-radius:50%;
}
.toggle{
  width:10em;
  height:5em;
  font-size:var(--font-size);
  z-index:2;
  margin:0px;
  cursor:pointer;
  filter:opacity(0%);
}
.toggle:checked ~ .switch .inner{
  background:linear-gradient(green,limegreen);
}
.toggle:checked ~ .switch .inner .disc{
  left:60%;
}
.toggle:checked ~ .switch .inner .disc::before{
  content:"ON";
  color:limegreen;
}
```
#### 涉及知识点
> 这里的按钮:采用了多元素层叠，每一层都渐变，然后利用上层覆盖下层，形成了边框和立体化效果；另外一种，可以利用box-shadow画出边框，代码详见：https://blog.csdn.net/qq_39207948/article/details/83627620


