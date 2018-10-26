## 效果展示：
#### 代码部分：
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
