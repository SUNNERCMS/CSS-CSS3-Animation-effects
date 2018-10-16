## 演示效果
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
