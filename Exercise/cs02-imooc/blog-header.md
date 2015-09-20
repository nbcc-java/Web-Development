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
			<li><a href="#">课程</a></li>
			<li><a href="#">计划</a></li>
			<li><a href="#">分享</a></li>
			<li><a href="#">社区</a></li>
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
			<input type="text" value="请输入想搜索的内容..."  class="search-input" />
			<input type="button" class="btn-search" />
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

3.**制作导航菜单样式**
>导航菜单的制作需要重点掌握链接文字在块状显示中的水平居中，垂直居中的实现技巧。

观察效果图，导航菜单和logo处于同一行中，这就需要为logo和导航菜单区块设置浮动效果。此外，无序列表形成的4个菜单，每个菜单60px，所以需要指定hd-nav的宽度为240px；菜单项li采用向左浮动效果，每个链接通过text-align:center样式属性实现水平居中效果,通过指定line-height为60px（与整个nav高度一致），利用元素内容在块状盒中默认采用垂直居中的特点，实现菜单文字的垂直居中显示效果。

4.**制作登录区域样式**

登录区域采用浮动到右侧的样式，而构成其选项的无序列表，其元素采用向左浮动形式，每个选项宽度高度为60x60；这里需要注意的是，为实现QQ头像，不能使用背景图方式，必须使用img标签，并使用border-radius进行圆角处理。为此，要将img标签头像垂直居中，需将其显示属性设置为inline-block,并指定其Vertical-align为middle,而不能采用block形式。
>延伸阅读：[CSS vertical-align](http://www.zhangxinxu.com/wordpress/2010/05/%E6%88%91%E5%AF%B9css-vertical-align%E7%9A%84%E4%B8%80%E4%BA%9B%E7%90%86%E8%A7%A3%E4%B8%8E%E8%AE%A4%E8%AF%86%EF%BC%88%E4%B8%80%EF%BC%89/)

最后，修改.hd-nav li a:hover样式选择器为 header li a:hover以适配这里的所有选项菜单链接情况。

5.**制作app-down区域和搜索栏**

**相关CSS**
```
.r{
	float:right;
}
.l{
	float:left;
}
.app-down{
	width: 87px;
	height: 60px;
}
.app-down a{
	display: block;
	height: 60px;
	color:#656e73;
	line-height: 60px;
	padding: 0 8px;
	font-size: 14px;
	white-space: nowrap;
}
.app-down a:hover .app-icon{
	background-position: 0px -16px;
}

.app-icon{
	background: url("../images/head-app-icon.png") no-repeat top left ;
	display: inline-block;
	width: 11px;
	height: 16px;
	vertical-align: -3px;
	margin-right: 5px;
}
```
上述代码中，使用雪碧图head-app-icon.png实现鼠标悬浮效果。即鼠标处于hover时，改变背景图的坐标（background-position）以显示悬停的图片效果。app-down区域的链接a采用block块状显示，使用line-height:60px致使其中的文字处于垂直居中，使用padding-left，以腾出左侧图标显示区域，marin-right:5px用于控制图标和文字的显示间隔。Vertical-align用于图标控制垂直的位置。

需要额外说明的是，为了更灵活地控制左右浮动效果，采用了自定义类`l和r`，在应用时使用类样式的叠加。

在处理文本框时，去除文本框自带的边框效果，并使用自定义背景色和前景色。指定padding和line-height；并为文本框获取焦点时设置相应的背景效果。