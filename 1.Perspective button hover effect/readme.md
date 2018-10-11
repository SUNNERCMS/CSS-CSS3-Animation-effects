## 透视按钮悬停效果
![](https://github.com/SUNNERCMS/CSS-CSS3-Animation-effects/blob/master/animation-gif/1.%E9%80%8F%E8%A7%86%E6%8C%89%E9%92%AE%E6%82%AC%E5%81%9C%E6%95%88%E6%9E%9C.gif)  
- 代码部分：  
```html
<ul>
  <li>home</li>
  <li>products</li>
  <li>services</li>
  <li>contact</li>
</ul>
```
```css
body {
    margin: 0;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background: cornsilk; 
}

ul {
    padding: 0;
    list-style-type: none; /*去掉无序列表的默认样式*/
}

ul li {
    box-sizing: border-box;
    width: 15em;
    height: 3em;
    font-size: 20px;
    border-radius: 0.5em;
    margin: 0.5em;
    box-shadow: 0 0 1em rgba(0,0,0,0.2);
    color: white;
    font-family: sans-serif;
    text-transform: capitalize;
    line-height: 3em;
    transition: 0.3s;
    cursor: pointer;
}

ul li:nth-child(odd) {
    background: linear-gradient(to right, orange, tomato);
    text-align: left;
    padding-left: 10%;
    transform: perspective(500px) rotateY(45deg);
}

ul li:nth-child(even) {
    background: linear-gradient(to left, orange, tomato);
    text-align: right;
    padding-right: 10%;
    transform: perspective(500px) rotateY(-45deg);
}

ul li:nth-child(odd):hover {
    transform: perspective(200px) rotateY(45deg);
    padding-left: 5%;
}

ul li:nth-child(even):hover {
    transform: perspective(200px) rotateY(-45deg);
    padding-right: 5%;
}

```
- 涉及知识点：
1.颜色设置：background: cornsilk;英文翻译是康丝兰等价于background: #FFF8DC;  
2.新接触的vh单位  
说明：  相对于视口的高度。视口被均分为100单位的vh  
示例代码：  
h1 {
    font-size: 8vh;  
}  
如果视口的高度是200mm，那么上述代码中h1元素的字号将为16mm，即(8x200)/100
rgb(0,0,0):黑色  
rgb(255,255,255):白色
rgba(0,0,0,.2):透明度0-1-->逐渐不透明，为1时不透明，为0时全透明  
box-shadow: h-shadow v-shadow blur spread color inset;   
box-shadow 向框添加一个或多个阴影。  
h-shadow	必需。水平阴影的位置。允许负值。
v-shadow	必需。垂直阴影的位置。允许负值。
blur	可选。模糊距离。
spread	可选。阴影的尺寸。	
color	可选。阴影的颜色。
inset	可选。将外部阴影 (outset) 改为内部阴影。    
渐变色设置：  
background: linear-gradient(direction, color-stop1, color-stop2, ...);   
衬线字体/非衬线字体


 
