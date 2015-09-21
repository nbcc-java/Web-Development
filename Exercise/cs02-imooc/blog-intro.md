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
**注意：**intro特性介绍分成四个部分，每个部分交叉的显示灰色/白色背景，文字图背景位置交叉地以右侧/左侧的形式进行定位。制作方法类似，这里仅以第一个特性介绍为例，它由星星（Star），视频（Video）和右侧文字三个部分构成，因此，在构建HTML结构时放置了三个div区域。外层的idx-width用于控制整个外盒的尺寸和居中显示效果。bg-grey显示背景色效果。
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
整个背景采用纯灰色和白色交替形式，为方便，将灰色和白色背景分别定义`bg-grey`和`bg-white`类，有了他们，在需要相应背景的元素开始标签添加相应的类样式进行叠加即可。为便于搜索引擎搜索，元素提供了图片文字对应的文字版本，但这些文字不需要用户看到，这里使用`.hidden-text`样式来隐藏这些图片文字。
intro2~4的实现方式与此类似，在此不再赘述，下面给出完整CSS代码
```css
.intro2-wrap{
	height: 400px;
	position: relative;
}
.intro2-text{
	width: 512px;
	height: 70px;
	position: absolute;
	left: 105px;
	top: 165px;
	background:  url("../images/02-text.png") 0 0 no-repeat;
}
.intro2-computer{
	background:  url("../images/02-computer2.png") 0 0 no-repeat;
	position: absolute;
	top: -30px;
	width: 580px;
	height: 430px;
	right: 0;
}

.intro3-wrap{
	height: 400px;
	position: relative;
}
.intro3-calendar{
	background:  url("../images/03-calendar.png") 0 0 no-repeat;
	position: absolute;
	left: 0px;
	top:-31px;
	width: 581px;
	height: 431px;
	z-index: 1;
}
.intro3-text{
	position: absolute;
	right:165px ;
	width: 476px;
	height: 70px;
	top: 165px;
	background:  url("../images/03-text.png") 0 0 no-repeat;
}
.intro3-smoke{
	background:  url("../images/03-smoke.png") 0 0 no-repeat;
	position: absolute;
	left: 0px;
	top: -31px;
	width: 581px;
	height: 431px;
	z-index:2 ;
}
.intro3-rockets{
	background:  url("../images/03-rockets.png") 0 0 no-repeat;
	position: absolute;
	left: 0px;
	top: -46px;
	width: 581px;
	height: 431px;
	z-index:3 ;
}

.intro4-wrap{
	height: 400px;
	position: relative;
}
.intro4-text{
	background: url("../images/04-text.png") 0 0 no-repeat;
	height: 70px;
	width: 422px;
	position: absolute;
	left: 146px;
	top: 165px;
	z-index: 1;
}
.intro4-hand{
	background:  url("../images/04-hand.png") 0 0 no-repeat;
	height: 430px;
	width: 581px;
	right: 0;
	top: -30px;
	position: absolute;
	z-index: 5;
}
.intro4-icon{
	background: url("../images/04-icon.png") 0 0 no-repeat;
	height: 430px;
	width: 581px;
	right: 0;
	top: -30px;
	position: absolute;
	z-index: 10;
}
```