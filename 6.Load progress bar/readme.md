## 展示效果
![](https://github.com/SUNNERCMS/CSS-CSS3-Animation-effects/blob/master/animation-gif/6.%E5%8A%A0%E8%BD%BD%E8%BF%9B%E5%BA%A6%E6%9D%A1.gif)
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
html结构相同  
下面是SCSS部分：
```SCSS
@import "compass/css3";

$speed: 2.5s;

* {
  margin: 0px;
  padding: 0px;
  border: 0px;
}

html, body {
  min-height:100%;
}

body {
  background: radial-gradient(red 10%,#444);//北京绚丽红
}

.loader {
  position: absolute;
  top: 0px;
  bottom: 0px;
  left: 0px;
  right: 0px;
  margin: auto;
  width: 175px;
  height: 100px;
  span {
    display: block;
    background: #ccc;
    width: 7px;
    height: 10%;
    border-radius: 14px;
    margin-right: 5px;
    float: left;
    margin-top: 25%;
    &:last-child {
      margin-right: 0px;
    }
    &:nth-child(1) {
      animation: load $speed 1.4s infinite linear;
    }
    &:nth-child(2) {
      animation: load $speed 1.2s infinite linear;
    }
    &:nth-child(3) {
      animation: load $speed 1s infinite linear;
    }
    &:nth-child(4) {
      animation: load $speed 0.8s infinite linear;
    }
    &:nth-child(5) {
      animation: load $speed 0.6s infinite linear;
    }
    &:nth-child(6) {
      animation: load $speed 0.4s infinite linear;
    }
    &:nth-child(7) {
      animation: load $speed 0.2s infinite linear;
    }
    &:nth-child(8) {
      animation: load $speed 0s infinite linear;
    }
    &:nth-child(9) {
      animation: load $speed 0.2s infinite linear;
    }
    &:nth-child(10) {
      animation: load $speed 0.4s infinite linear;
    }
    &:nth-child(11) {
      animation: load $speed 0.6s infinite linear;
    }
    &:nth-child(12) {
      animation: load $speed 0.8s infinite linear;
    }
    &:nth-child(13) {
      animation: load $speed 1s infinite linear;
    }
    &:nth-child(14) {
      animation: load $speed 1.2s infinite linear;
    }
    &:nth-child(15) {
      animation: load $speed 1.4s infinite linear;
    }
  }
}

@keyframes load {
  0% {
    background: #ccc;
    margin-top: 25%;
    height: 10%;
  }
  50% {
    background: #444;
    height: 100%;
    margin-top: 0%;
  }
  100% {
    background: #ccc;
    height: 10%;
    margin-top: 25%;
  }
}
```
### 代码解析及相关知识点： 
主要应用了SCSS语法和compass中的CSS3核心模块和layout模块  
（1）[compass中的CSS3核心模块](http://compass-style.org/reference/compass/css3/border_radius/)  
（2）[compass中的layout核心模块](http://compass-style.org/reference/compass/layout/stretching/)



