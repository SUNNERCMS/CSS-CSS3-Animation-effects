### 动画效果：
![](https://github.com/SUNNERCMS/CSS-CSS3-Animation-effects/blob/master/animation-gif/7.bouncing.gif)
### 代码部分：
```HTML
  <div class="top"></div>
  <div class="bottom"></div>
```
```CSS
//设置body内元素垂直水平居中 
body{
  margin:0;
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  background-color:dimgray;/*暗灰色*/
}
// 以$size作为基准大小,SCSS定义变量的方式
$size:50px;
// 用来设置底部基座
.bottom{
  position:relative;
  width:2*$size;
  height:$size;
  background-color:peru;//秘鲁色
  border-radius:0.1*$size;
  animation:rotate 2s ease-in-out infinite;
}
// 用来设置顶部小球的样式
.top{
  position:relative;
  left:1.5*$size;//相对于上面小球是平躺时的定位，后面动画改变时只是进行了旋转，定位还是相对于平躺位置。
  top:-1*$size;
  width:$size;
  height:$size;
  box-shadow:0 3px 3px 0 #666;//小球底部设置一个阴影
  border-radius:0.5*$size;
  background-color:burlywood;//原木色
  animation:bouncing 2s ease-in-out infinite;
}
//底部基座的旋转动画
@keyframes rotate{
  50%{
    transform:rotate(90deg);//当基座在50%时，旋转90度，耗时1s，基座立起
  }
  100%{
    transform:rotate(180deg);
  }
}
//小球的弹跳动画
@keyframes bouncing{
  0%,100%{
    top:-1*$size;
  }
  40%,80%{
    top:-3*$size;
  }
  50%{
    top:-1.5*$size;//小球在50%时，刚好位于立起的基座上面，耗时也是1s
  }
}
```
