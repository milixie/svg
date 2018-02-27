# SVG 

先把大神的文章贴过来哈 [超级强大的SVG SMIL animation动画详解](http://www.zhangxinxu.com/wordpress/2014/08/so-powerful-svg-smil-animation/)

也可以看比较官方的一些文档 [SVG教程](https://developer.mozilla.org/zh-CN/docs/Web/SVG/Tutorial)

自己跟着大神文章做练习做总结

### 入门

#### 基本要素

- `<svg>`根元素，相当于HTML里面的标签

- `<g>`元素，用来把若干个基本形状组成一个组

**注意**	

- SVG 属于XML语言，因为XML是区分大小写的，所以SVG的属性和元素必须按照标准规范书写

- SVG 的属性值必须使用引号引起来


### SVG 图

先看下这个例子

```
<svg version="1.1" 
	baseProfile="full" 
	width="300" 
	height="200"
	viewBox="0 0 300 200"
  xmlns="http://www.w3.org/2000/svg">
  <rect x="0" y="0" width="100%" height="100%" fill="blue"/>
  <circle cx="150" cy="100" r="80" fill="red"/>
  <text x="150" y="125" font-size="60" text-anchor="middle" fill="white">SVG</text>
</svg>
```

[查看效果](https://github.com/milixie/svg/blob/master/image/1.jpeg)

```
<svg width="200" height="250" version="1.1" xmlns="http://www.w3.org/2000/svg">

  <rect x="10" y="10" width="30" height="30" stroke="black" fill="transparent" stroke-width="5"/>
  <rect x="60" y="10" rx="10" ry="10" width="30" height="30" stroke="black" fill="transparent" stroke-width="5"/>

  <circle cx="25" cy="75" r="20" stroke="red" fill="transparent" stroke-width="5"/>
  <ellipse cx="75" cy="75" rx="20" ry="5" stroke="red" fill="transparent" stroke-width="5"/>

  <line x1="10" x2="50" y1="110" y2="150" stroke="orange" fill="transparent" stroke-width="5"/>
  <polyline points="60 110 65 120 70 115 75 130 80 125 85 140 90 135 95 150 100 145"
      stroke="orange" fill="transparent" stroke-width="5"/>

  <polygon points="50 160 55 180 70 180 60 190 65 205 50 195 35 205 40 190 30 180 45 180"
      stroke="green" fill="transparent" stroke-width="5"/>

  <path d="M20,230 Q40,205 50,230 T90,230" fill="none" stroke="blue" stroke-width="5"/>
</svg>
```

**解释**

1. `svg`根元素里面的 `version` 和 `baseProfile` 属性是必不可少的，供其它类型的验证方式确定SVG版本。

2. 绘制矩形图使用`rect`，需要对其设置宽width、高height，

	- `x` 表示距离左边边框的距离

	- `y` 表示距离顶部的距离 类似于css中的`left, top`属性

	- `rx` 圆角的x方位的半径

	- `ry` 圆角的y方位的半径


3. 绘制圆使用`circle`，需要对其设置半径r

	- `r` 表示半径

	- `cx` 圆心的x位置

	- `cy` 圆心的y位置

4. 绘制椭圆使用 `ellipse` -  是circle元素更通用的形式

	- `rx` x方向的半径

	- `ry` y方向的半径

	- `cx` 椭圆中心x的位置

	- `cy` 椭圆中心y的位置

5. 绘制直线使用 `line`

	- `x1` 起点的x位置

	- `y1` 起点的y位置

	- `x2` 终点的x位置

	- `y2` 终点的y位置

6. 绘制折线or多边形使用 `polyline`

- `points` 点集数列。每个数字用空白、逗号、终止命令符或者换行符分隔开。每个点必须包含2个数字，一个是x坐标，一个是y坐标。所以点列表 (0,0), (1,1) 和(2,2)可以写成这样：“0 0, 1 1, 2 2”，也可以写成 “0 0 1 1 2 2”。

7. 绘制路径使用`path` - 可以用path元素绘制矩形（直角矩形或者圆角矩形）、圆形、椭圆、折线形、多边形，以及一些其他的形状，例如贝塞尔曲线、2次曲线等曲线

	- `d`: 一个“命令+参数”的序列

直线：

- `M x y` or `m dx dy` 表示 Move to 可以用来表示起点，不会划线

- `H x` or `h dx` 表示画横线

- `V y` or `v dy` 表示画竖线

- `L x y` or `l dx dy` 表示line to，会在新位置和前面的旧位置画线

- `Z` or `z` 是闭合路径命令


曲线：

贝塞尔曲线

`C x1 y1, x2 y2, x y (or c dx1 dy1, dx2 dy2, dx dy)`

这里的最后一个坐标(x,y)表示的是曲线的终点，另外两个坐标是控制点，(x1,y1)是起点的控制点，(x2,y2)是终点的控制点

`<path d="M 100 500 C 200 600, 400 600, 500 500 Z" stroke="black" fill="transparent"/>`

可以使用多个C命令把不同的贝塞尔曲线连起来成一个曲线，也可以使用S命令简写

`<path d="M 100 300 S 600 100, 600 300" stroke="green" fill="transparent"/>`

二次贝塞尔曲线Q，只有一个控制点

`<path d="M 100 600 Q 350 300, 600 600" stroke="green" fill="transparent"/>`

二次贝塞尔曲线有一个差不多的T命令，可以通过更简短的参数，延长二次贝塞尔曲线

*注意*

T命令前面必须是一个Q命令，或者是另一个T命令，才能达到这种效果。如果T单独使用，那么控制点就会被认为和终点是同一个点，所以画出来的将是一条直线。

`<path d="M 100 700 Q 200 500, 500 700 T 800 700" stroke="blue" fill="transparent"/>`


写文字使用`text`

- `fill` 表示的是填充面颜色

- `stroke` 表示线颜色

- `svg` 里面的 `viewBox="0 0 300 200"` 定义了画布上可以显示的区域为 (0,0) -> (300,200)，如果这里定义的值小于svg里面的width/height，那么图会被相应的放大

### SVG 渐变

- 线性渐变

```
<svg version="1.1" width="1000" height="1000" xmlns="http://www.w3.org/2000/svg">
	<linearGradient id="gradient1">
		<stop offset="0%" stop-color="red"/>
		<stop offset="60%" stop-color="blue"/>
		<stop offset="80%" stop-color="yellow"/>
		<stop offset="100%" stop-color="lightblue"/>
	</linearGradient>

	<rect x="100" y="100" rx="20" ry="20" width="300" height="300" fill="url(#gradient1)"/>
</svg>
```

- 径向渐变

```
<radialGradient id="gradient2" cx="0.2" cy="0.5" r="0.5" fx="0.5" fy="0.25">
	<stop offset="0%" stop-color="yellow"/>
	<stop offset="40%" stop-color="blue"/>
	<stop offset="100%" stop-color="red"/>
</radialGradient>

<rect x="100" y="500" rx="20" ry="40" width="200" height="200" fill="url(#gradient2)"/>
```

- 图案

```
<pattern id="Pattern" x="0" y="0" width=".25" height=".25">
    <rect x="0" y="0" width="70" height="70" fill="skyblue"/>
    <rect x="0" y="0" width="20" height="20" fill="url(#gradient2)"/>
    <circle cx="40" cy="40" r="20" fill="url(#gradient1)" fill-opacity="0.5"/>
  </pattern>

  <rect fill="url(#Pattern)" stroke="black" x="500" y="100" width="400" height="400"/>
```


### SVG 变形




### SVG 动画 （SVG SMIL Animation）


SMIL: 同步多媒体集成语言

SMIL: 允许做以下事情：

- 动画元素的数值属性（X, Y, …）

- 动画属性变换（平移或旋转）

- 动画颜色属性

- 沿着运动路径运动
































