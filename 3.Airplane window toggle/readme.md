## 效果展示：
#### 代码部分：
```html
<!--在 dom 中增加表示云朵的 .clouds 元素，其中的 5 个 <span> 子元素分别表示 1 朵白云： -->
<input type="checkbox" class="toggle">
<figure class="window">
  <div class="curtain"></div>
  <div class="clouds">
    <span></span>
    <span></span>
    <span></span>
    <span></span>
    <span></span>
  </div>
</figure>
```
```CSS
body{
  margin:0px;
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  background-color:skyblue;
}
.window{
  position:relative;
  box-sizing:border-box;/*怪异盒模型*/
  width:25em;/*窗户内视图宽是125px,不包括外面由box-shadow画的外边框*/
  height:35em;/*窗户内视图高是125px*/
  font-size:5px;
  background-color:#d9d9d9;
  border-radius:5em;
  box-shadow:
    inset 0 0 8em rgba(0,0,0,0.2),/*0,0,0是黑色*/
    0 0 0 0.4em #808080,/*深灰色的边缘线*/
    0 0 0 4em whitesmoke,
    0 0 0 4.4em #808080, /*深灰色的边缘线*/
    0 2em 4em 4em rgba(0,0,0,0.1);/*阴影的原始尺寸由第四个参数决定，边界到whitesmoke*/
  overflow:hidden;/*这里的hidden是为了使下面的curtain定位时：top:-5%，可以将溢出的部分截掉*/
}
/*窗户的盖（窗帘） 设置窗帘样式，和窗口尺寸一样，但不拉到底*/
.window .curtain{
  position:absolute;
  left:0;
  top:-5%;/*相对于窗户内视图的高为计算依据，175*0.05=8.75，向上移动距离为9px*/
  width:inherit;
  height:inherit;
  border-radius:5em;
  background-color:whitesmoke;
  box-shadow:0 0 0 0.5em #808080,/*给盖子加上边框，0.5em比上面的0.4em大点，目的是能够盖住原来的0.4em的边框*/
             0 0 3em rgba(0,0,0,0.4);
  transition: top 0.5s ease-in-out;/*给top元素加上过渡效果*/
  z-index:2;
}
.toggle:checked ~ .window .curtain{
  top:-90%;
}
/*用伪元素在窗帘上画出指示灯的长条灰色区域*/
.window .curtain::before{
  content:'';
  position:absolute;
  width:40%;
  height:0.8em;
  background-color:#808080;
  left:30%;
  bottom:1.6em;
  border-radius:0.4em;
}
/*用伪元素在窗帘上画出径向渐变的指示灯*/
.window .curtain::after{
  content:'';
  position:absolute;
  width:1.6em;
  height:0.8em;
  background-image:radial-gradient(orange,orangered);
  bottom:1.6em;
  left:calc((100% - 1.6em)/2);/*100%是指窗户视图的宽-指示灯的宽度，然后将剩余距离分成两份进行居中*/
  border-radius:0.4em;
}
.toggle:checked ~ .window .curtain::after{
  background-image:radial-gradient(lightgreen,limegreen);
}
/*隐藏 checkbox，用 opacity(0) 可以使元素在不可见的状态下仍可交互，把它的尺寸设置得到舷窗一样大，并且图层在舷窗之上，得到的效果就是点击舷窗时实际是点击了 checkbox：*/
.toggle{
  position:absolute;
  width:25em;
  height:35em;
  font-size:5px;
  z-index:3;
  cursor:pointer;
  filter:opacity(0%);
}
/*用云朵容器画出窗外的蓝天：*/
.window .clouds{
  position:relative;
  width:20em;
  height:30em;
  background-color:deepskyblue;
  left:calc((100% - 20em)/2);
  top:calc((100% - 30em)/2);
  border-radius:7em;
  box-shadow: 0 0 0 0.4em #808080;
  overflow:hidden;
}
/*每朵云由 3 部分组成，先画面积最大的部分：*/
.clouds span{
  position:absolute;
  width:10em;
  height:4em;
  background-color:white;
  border-radius:4em;
  top:20%;
  animation: move 4s linear infinite;

}
@keyframes move {
    from {
        left: -150%;
    }
    to {
        left:150%;
    }
}
/*用伪元素画 2 个突起的圆弧*/
.clouds span::before ,
.clouds span::after{
  content:'';
  position:absolute;
  width:4em;
  height:4em;
  background-color:white;
  border-radius:50%;
}
.clouds span::before{
  top:-2em;
  left:2em;
}
.clouds span::after{
  top:-1em;
  right:1em;
}
/*使用伪类，将每朵云的大小、位置有一些变化：*/
.clouds span:nth-child(2){
  top:40%;
  animation-delay:-1s;
}
.clouds span:nth-child(3){
  top:60%;
  animation-delay:-0.5s;
}
.clouds span:nth-child(4){
  top:20%;
  transform:scale(2);
  animation-delay:-1.5s;
}
.clouds span:nth-child(5){
  top:70%;
  transform:scale(1.5);
  animation-delay:-3s;
}
```
##### 代码部分解读：
> 当舷窗打开时，.curtain 要向上移动，并且指示灯亮绿色光，这里的波浪号暂时还不知道是哪里的知识点，目前的理解是“满足选中时的执行跳转”：当类为toggle的input输入框被选中时，跳转执行->波浪号后面的样式
```CSS
.window .curtain {
    transition: 0.5s ease-in-out;
}

.toggle:checked ~ .window .curtain {
    top: -90%;
}

.toggle:checked ~ .window .curtain::after {
    background-image: radial-gradient(lightgreen, limegreen);
}
```
```CSS
.toggle{ /*input 的开关控制：窗帘打开或关上*/
  z-index:3;/*将input的点击层放在在最上面，放在舷窗的上面，这样点击时，input才能被选中*/
  cursor:pointer;
  filter:opacity(0%);
}
/*窗户的盖（窗帘） 设置窗帘样式，和窗口尺寸一样，但不拉到底*/
.window .curtain{
  z-index:2;/*舷窗应该在窗外白云之上，但是在input之下，这样可以做到既能点击产生动作，又能覆盖住窗户中的白云*/
}
```
#### 涉及知识点：
- 1.[background-image](http://www.w3school.com.cn/cssref/pr_background-image.asp) 属性为元素设置背景图像。  
&nbsp;&nbsp; 元素的背景占据了元素的全部尺寸，包括内边距，但不包括外边距。  
&nbsp;&nbsp; 默认地，背景图像位于元素的左上角，并在水平和垂直方向上重复。  
&nbsp;&nbsp; 提示：请设置一种可用的背景颜色，这样的话，假如背景图像不可用，页面也可获得良好的视觉效果。  
&nbsp;&nbsp;参数：  
&nbsp;&nbsp;（1）url('URL')	指向图像的路径。  
&nbsp;&nbsp;（2）none	默认值。不显示背景图像。  
&nbsp;&nbsp;（3）inherit	规定应该从父元素继承 background-image 属性的设置。  
&nbsp;&nbsp;补充：常和[ background-repeat](http://www.w3school.com.cn/cssref/pr_background-repeat.asp)设置是否及如何重复背景图像。[background-position](http://www.w3school.com.cn/cssref/pr_background-position.asp)设置背景图像的起始位置。[background-attachment](http://www.w3school.com.cn/cssref/pr_background-attachment.asp)设置背景图像是否固定或者随着页面的其余部分滚动。  
- 2.[radial-gradient](http://www.runoob.com/cssref/func-radial-gradient.html)用径向渐变创建 "图像"。  
&nbsp;&nbsp;background-image:  radial-gradient(orange, orangered);由中心点向外定义，由圆心向外分别是橘色，橘红色；  
- 3.filter 属性定义了元素(通常是<img>)的可视效果(例如：模糊与饱和度)。  
`filter: opacity(0%);` :用 opacity(0%) 可以使元素在不可见的状态下仍可交互,该函数与已有的opacity属性很相似，不同之处在于通过filter，一些浏览器为了提升性能会提供硬件加速。filter: opacity(0%):值为0%则是完全透明，值为100%则图像无变化;opacity属性：opacity:0;完全透明(0-1:完全透明到不透明）
- 4.[transtion](http://www.w3school.com.cn/cssref/pr_transition.asp)给指定属性增加过渡效果；
