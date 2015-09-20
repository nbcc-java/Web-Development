## Building intro blocks##
###效果图###
<img src="http://ww1.sinaimg.cn/large/6d025b55gw1ew907zym7sj20ym18cjy0.jpg" />

###构建HTML结构###
```html
	<div class="intros">
		<div class="intro bg-grey ">
			<div class="idx-width intro1-wrap">
				<div class="intro1-star"></div>
				<div class="intro1-video"></div>
				<div class="intro1-text hidden-text">精心制作的视频课程。老师都技术大牛实战派。课程内容接地气，实际工作用得着。</div>
			</div>
		</div>
		……
	</div>
```
###构建相应CSS###
```css
.hidden-text{
	text-indent: 100%;
	white-space: nowrap;
	overflow: hidden;
}

.bg-grey{
	background-color: #eef1f2;
}
.bg-white{
	background-color: #fff;
}
.intro1-wrap{
	height: 400px;
	position: relative;
}
.intro1-star{
	position: absolute;
	left: -15px;
	top: -20px;
	background: url("../images/01-star.png") no-repeat top left;
	width: 581px;
	height: 431px;
	z-index: 10;
}
.intro1-video{
	position: absolute;
	width: 581px;
	height: 431px;
	background: url("../images/01-video.png") 0 0 no-repeat;
	left: -15px;
	bottom: 0px;
	z-index: 5;
}
.intro1-text{
	position: absolute;
	width: 493px;
	height: 70px;
	right: 105px;
	top: 164px;
	background: url("../images/01-text.png") 0 0 no-repeat;
}
```
整个背景采用纯灰色和白色交替形式，为方便，将灰色和白色背景分别定义`bg-grey`和`bg-white`类，有了他们，在需要该样式的元素开始标签添加类样式进行叠加。为便于搜索引擎搜索，元素提供了图片文字的文字版本，为让他们不可见，使用`.hidden-text`样式隐藏图片文字。