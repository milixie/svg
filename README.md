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
  xmlns="http://www.w3.org/2000/svg">
  <rect width="100%" height="100%" fill="blue"/>
  <circle cx="150" cy="100" r="80" fill="red"/>
  <text x="150" y="125" font-size="60" text-anchor="middle" fill="white">SVG</text>
</svg>
```

![查看效果](https://github.com/milixie/svg/image/1.jpeg)


### SVG 动画 （SVG SMIL Animation）


SMIL: 同步多媒体集成语言

SMIL: 允许做以下事情：

- 动画元素的数值属性（X, Y, …）

- 动画属性变换（平移或旋转）

- 动画颜色属性

- 沿着运动路径运动
































