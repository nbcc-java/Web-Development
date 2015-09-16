## 9/15/2015 8:12:38 PM IMOOC首页构建 ##

###创建header导航###
>通过本小节的学习，掌握网站logo的常用技巧，深入掌握：
>display,overflow,white-space,text-indent的用法

先来看效果图
<img src="http://ww4.sinaimg.cn/large/6d025b55gw1ew4e35wqapj214k01nq33.jpg" />
观察可知，导航可由四个部分构成（课程logo，导航菜单条，搜索工具栏，登录窗口）
由此可以实现相关的HTML代码结构，具体如下：
```HTML
	<header>
		<div class="logo">
			<a href="#">慕课网</a>
		</div>
		<ul class="hd-nav">
			<li><a href="#">item1</a></li>
			<li><a href="#">item2</a></li>
			<li><a href="#">item3</a></li>
			<li><a href="#">item4</a></li>
		</ul>
		<div class="login-area">
			<ul>
				<li><a href="#">item1</a></li>
				<li><a href="#">item2</a></li>
			</ul>
		</div>
		<div class="app-down">
			<a href="#">慕课APP</a>
		</div>
		<div class="search-area">
			<input type="text" text="" />
		</div>
	</header>
```
对照效果图，下面针对该结构，使用CSS样式表实现最终的效果，具体步骤如下：

1.**重置CSS样式**，在网页文档的`<head>`标签位置引入外部reset.css样式链接

2.**引入logo**
```css
.logo{
	margin:0 20px;
	width: 140px;
}
.logo a{
	display: block;
	background: url(../images/logo.png) center center no-repeat;
	text-indent: 100%;
	overflow: hidden;
	white-space: nowrap;
	height: 60px;
	line-height: 60px;
}
```
这里根据logo图片大小指定div.logo盒子的大小（140px×60px），同时，指定左右20px的外边距。为了让logo可以点击，里面的a链接必须处理成块状结构（或者inline-block),从而可以通过width和height指定其大小，链接中的文字在效果图中并不需要显示，但这里还是添加了，主要为了出于辅助阅读（盲人阅读器），同时也便于搜索引擎访问。这里为了让文字不可见，通过样式代码text-indent:100%；当然也可以设置为-100%，这样就移出在盒子显示之外，但一旦超出盒子范围的时候，很多浏览器就会自动采用换行的方式进行显示，这里用white-space：nowrap属性禁止文字换行，这样露在盒子外边的链接文字还是不够美观，使用overflow:hidden彻底将其隐藏。最后，这里的图片在定位的时候采用center center的模式，将图片水平和垂直方向上都采用居中显示。
>这是引用的内容