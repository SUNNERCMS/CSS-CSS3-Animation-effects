## 演示效果  
![](https://github.com/SUNNERCMS/CSS-CSS3-Animation-effects/blob/master/animation-gif/5.%E4%B9%92%E4%B9%93.gif)  
#### 代码部分：
```html
<div class="court">
  <div class="left-paddle"></div>
  <div class="ball"></div>
  <div class="right-paddle"></div>
</div>
```
```css
body{
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  background:linear-gradient(silver,dimgray);
}
*{
  box-sizing:border-box;
}
/*球案*/
.court{
  position:relative;
  width:30em;/*浏览器默认值是16px,这里的宽是320px*/
  height:20em;
  color:white;
  border:1em solid currentColor;
  transform:rotate(90deg);
}
/*左拍*/
.court .left-paddle{
  position:absolute;
  left:1em;
  top:1em;
  width:1em;
  height:calc(50% - 1em);/*左拍的大小，等于球案的一半减去顶部的距离1em*/
  background-color:currentColor;
  animation: left-moving 1s linear infinite alternate;
}
@keyframes left-moving{
  to {
    transform:translateY(100%);
  }
}
/*右拍*/
.court .right-paddle{
  position:absolute;
  right:1em;
  bottom:1em;
  width:1em;
  height:calc(50% - 1em);
  background-color:currentColor;
  animation: right-moving 1s infinite alternate;
}
@keyframes right-moving{
  to {
    transform:translateY(-100%);
  }
}
/*画出小球*/
.court .ball{
  position:absolute;
  left:2em;
  top: calc(50% - 1.5em);/*注意这里不要和left-paddle的height值混淆，这里是top,top距离顶部的距离是（50%-1.5em）*/
  width:1em;
  height:1em;
  background-color:currentColor;
  animation:ball-moving 1s linear infinite alternate;
}
@keyframes ball-moving{
  to {
    left:calc(100% - 3em);/*小球最终要移动到右边的距离：刚好是整个球桌宽度减去右边的间隙1em,球拍宽度1em，小球占据的宽度1em*/
  }
}
```
#### 涉及知识点：
1.animation动画的常用参数设置  
(1)动画的名字  
(2)动画完成所需要的时间  
(3)动画的速度曲线:animation-timing-function:value;  
&nbsp;&nbsp; value值可以是：linear动画从头到尾速度相同；默认：（低速->加快->低速）；ease-in-out：动画以低速开始和结束；  
(4)动画是否延时开始，可以设置延时的时间  
(5)动画的播放次数：n动画播放次数的数值；infinite：无限次播放；  
(6)是否轮流反向播放动画：默认值normal；alternate:轮流反向播放；
