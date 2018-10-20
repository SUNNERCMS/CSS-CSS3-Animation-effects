## 热气球浮动效果
#### 演示效果：
![](https://github.com/SUNNERCMS/CSS-CSS3-Animation-effects/blob/master/animation-gif/2%E7%83%AD%E6%B0%94%E7%90%83.gif) 
#### 代码部分：
```html
<figure class="balloon">
  <div class="envelope">
    <span></span>
    <span></span>
  </div>
  <div class="basket">
    <span></span>
    <span></span>
    <span></span>
    <span></span>
  </div>
</figure>
```
```css
body{
  margin:0px;
  height:100vh;
  display:flex;  /*垂直水平居中:父元素上设置，子元素上生效*/
  justify-content:center;
  align-items:center;
  background:linear-gradient(deepskyblue,skyblue,lightblue 20%);/*从上至下依次渐变，没有20%时，三色平分视口区域，20%：代表最后一种颜色从视口的20%处开始*/
}
/*纵向居中布局*/
.balloon{
  font-size:16px;
  width:12em;
  height:19em;
  display:flex;
  flex-direction:column;/*主轴线设置为了垂直方向，那么侧轴线就是水平方向*/
  align-items:center;/*使得垂直排列的元素，在侧轴线线上居中对齐*/
 animation:drift 2s infinite alternate;/*名为drift的动画 在两秒内完成一次；执行次数无限次 正反运动往返执行*/ */
}
@keyframes drift{
  to {
    transform:translateY(-10%);/*提升的距离是自身元素高度的30%*/
  }
}
.envelope {
    position: relative;
    width: inherit;
    height: 16em;/*高度不够，用来将盖子下面的倒三角截成倒梯形*/
    overflow: hidden;
}
/*伞盖的形状是上端为球形，下端为圆锥形,所以我们先在上部画一个圆，再在下部画一个三角形。
先画上部的圆：*/
.envelope span {
    position: absolute;
    width: inherit;
    height: 12em;
    border-radius: 50%;
    color: orange;
    background-color: currentColor;
}
/*再用伪元素画出下部的等腰三角形：*/
 .envelope span::before {
    content: '';
    position: absolute;
    width: 0;
    height: 0;
    border-width: 10em 5.5em 0 5.5em;
    border-style: solid;
    border-color: currentColor transparent transparent transparent;
    left: calc(50% - 5.5em);/*动态计算长度值*/
    top: 8.45em;
}
.envelope span:nth-child(2){/*这里的两个span元素其实是重叠的相同的图案，这里将第二个span元素进行压缩和变色，是为了形成两幅图案的色彩叠加效果*/
  transform:scaleX(0.4);
  filter:brightness(0.85) contrast(1.4);/*滤镜效果：前者调整明亮程度；后者是对比度设置*/
}
/*定义吊篮的尺寸：*/
.basket {
    position: relative;
    width: 2em;
    height: 3em;
}
/*用 ::before 伪元素画出篮子：*/
.basket::before{
  content:'';
  position:absolute;
  width:inherit;
  height:1.6em;
  background-color:peru;/*秘鲁色：明度稍高的褐色*/
  bottom:0px;
  border-radius:0 0 0.5em 0.5em;/*圆角边框设置*/
}
/*用 ::after 伪元素画出篮子的顶边：*/
.basket::after{
  content:'';
  position:absolute;
  width:105%;
  height:0.3em;
  background-color:saddlebrown;
  top:1.3em;
  left:calc((100% - 105%)/2);/*用于将篮边居中对齐*/
  border-radius:0.3em;
}
/*定位缆绳，并倾斜不同的角度：*/
.basket span{
  position:absolute;
  width:0.1em;
  height:1.5em;
  background-color:burlywood;
  left:calc((var(--n) - 1) * 0.6em);
  transform:rotate(calc(var(--r) * 7deg));
  trasnform-origin:bottom;
}
.basket span:nth-child(1){--n: 1; --r: -2;}/*对每一个span元素都应用上面的span设置，相当于调用类*/
.basket span:nth-child(2){--n: 2; --r: -1;}
.basket span:nth-child(3){--n: 3; --r: 1;}
.basket span:nth-child(4){--n: 4; --r: 2}


```
#### 涉及知识点
- 1.HTML5之figure标签：
> `<figure>` 标签规定独立的流内容（图像、图表、照片、代码等等）。figure 元素的内容应该与主内容相关，但如果被删除，则不应对文档流产生影响。  
`<figcaption>` 标签为 `<figure>` 元素定义标题。  
`<figcaption>` 元素应该被置于 `<figure>` 元素的第一个或最后一个子元素的位置。  
注意：当给figure中的image图片做标题时，使用figcaption要比使用p标签的行间距要小，显示效果变现的更加紧凑.
- 2.animation(动画):animation: name/duration/timing-function/delay/iteration-count/direction/fill-mode/play-state;  
常用的属性值设置：  
`animation-name`	指定要绑定到选择器的关键帧的名称    
`animation-duration`	动画指定需要多少秒或毫秒完成  
`animation-timing-function`	设置动画将如何完成一个周期  
&nbsp;&nbsp; (1)linear:动画从头到尾的速度是相同的。  
&nbsp;&nbsp; (2)ease:默认。动画以低速开始，然后加快，在结束前变慢。	  
&nbsp;&nbsp; (3)ease-in:动画以低速开始。	  
&nbsp;&nbsp; (4)ease-out:动画以低速结束。	  
&nbsp;&nbsp; (5)ease-in-out:动画以低速开始和结束。
`animation-delay`	设置动画在启动前的延迟间隔。  
`animation-iteration-count`	定义动画的播放次数。  
`animation-direction`	指定是否应该轮流反向播放动画。  
&nbsp;&nbsp;（1）normal:默认值。动画按正常播放。  
&nbsp;&nbsp;（2）reverse:动画反向播放。    
&nbsp;&nbsp;（3）alternate:动画在奇数次（1、3、5...）正向播放，在偶数次（2、4、6...）反向播放。  
&nbsp;&nbsp;（4）alternate-reverse:动画在奇数次（1、3、5...）反向播放，在偶数次（2、4、6...）正向播放。   
`animation-fill-mode`	规定当动画不播放时（当动画完成时，或当动画有一个延迟未开始播放时），要应用到元素的样式。  
&nbsp;&nbsp; (1)forwards：在动画结束后（由 animation-iteration-count 决定），动画将应用该属性值。也即是：停留在动画结束时的位置  
`animation-play-state`	指定动画是否正在运行或已暂停。  
&nbsp;&nbsp; (1)paused：指定暂停动画  
&nbsp;&nbsp; (2)running：指定正在运行的动画
- 3.calc() 函数用于动态计算长度值。  
-- 需要注意的是，运算符前后都需要保留一个空格，例如：width: calc(100% - 10px)；  
-- 任何长度值都可以使用calc()函数进行计算；  
-- calc()函数支持 "+", "-", "*", "/" 运算；  
-- calc()函数使用标准的数学运算优先级规则；  
- 4.CSS3 filter(滤镜) 属性  
&nbsp;&nbsp; (1)brightness(%):给图片应用一种线性乘法，使其看起来更亮或更暗。如果值是0%，图像会全黑。值是100%，则图像无变化。其他的值对应线性乘数效果。值超过100%也是可以的，图像会比原来更亮。如果没有设定值，默认是1。  
&nbsp;&nbsp; (2)contrast(%):调整图像的对比度。值是0%的话，图像会全黑。值是100%，图像不变。值可以超过100%，意味着会运用更低的对比。若没有设置值，默认是1。
- 5.[伪元素的使用](https://segmentfault.com/bookmark/1230000016613724)
