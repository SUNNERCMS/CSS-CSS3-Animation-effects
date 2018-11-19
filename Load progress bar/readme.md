## 展示效果
#### 代码部分：(使用了SCSS语法，和compass书写框架)
```HTML
<div class="loader">
  <span></span>
  <span></span>
  <span></span>
  <span></span>
  <span></span>
  <span></span>
  <span></span>
  <span></span>
  <span></span>
  <span></span>
  <span></span>
  <span></span>
  <span></span>
  <span></span>
  <span></span>
</div>
```
```scss
@import "compass/css3";
@import "compass/layout/stretching";
$speed:1.2s;
*{
  margin:0px;
  padding:0px;
  border:0px;
}
// 宽高定义宏
@mixin wh ($width,$height){
  width:$width;
  height:$height;
}
//动画制作定义宏
@mixin keyframes($background,$margin-top,$height){
  background:$background;
  margin-top:$margin-top;
  height:$height;
}
//动画定义宏
@mixin animation($delay){
  animation:load $speed $delay linear infinite alternate;
}

html,body{
  min-height:100%;
}
body{
  background:radial-gradient(red,#444);
}
.loader{
  @include stretch;//将loader元素撑满父容器
  margin:auto;
  @include wh(175px,100px);
  span{
    display:block;
    background:#ccc;
    @include wh(7px,10%);
    border-radius:14px;
    float:left;
    margin-right:5px;
    margin-top:25%;
    &:last-child{
      margin-right:0px;
    }
    &:nth-child(1){
      @include animation(1.4s);
    }
    &:nth-child(2){
      @include animation(1.2s);
    }
    &:nth-child(3){
      @include animation(1.0s);
    }
     &:nth-child(4){
      @include animation(0.8s);
    }
    &:nth-child(5){
      @include animation(0.6s);
    }
    &:nth-child(6){
      @include animation(0.4s);
    }
    &:nth-child(7){
      @include animation(0.2s);
    }
    &:nth-child(8){
      @include animation(0s);
    }
    &:nth-child(9){
      @include animation(0.2s);
    }   
    &:nth-child(10){
      @include animation(0.4s);
    }
     &:nth-child(11){
      @include animation(0.6s);
    }
    &:nth-child(12){
      @include animation(0.8s);
    }
    &:nth-child(13){
      @include animation(1.0s);
    }
    &:nth-child(14){
      @include animation(1.2s);
    }
    &:nth-child(15){
      @include animation(1.4s);
    }
  }
}
@keyframes load{
  0% {
    @include keyframes(#ccc,25%,10%);
  }
  100% {
    @include keyframes(#444,0%,100%);
  }
}
```
#### 未简化版本：
```HTML
```

