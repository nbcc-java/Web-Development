##2015-09-20 14:53:23 构建Banner##
###效果图###
<img src="http://ww4.sinaimg.cn/large/6d025b55gw1ew8yhjx6k1j21f30gvtas.jpg" />

###构建HTML结构###
```html
	<div class="banner">
		<div class="banner-content">
			<div class="inner"><a href="#" class="more">了解更多</a></div>
		</div>
	</div>

###构建相应CSS###
```css
/*banner*/
.banner{
	width: 100%;
	height: 600px;
	background: url("../images/banner2.jpg") no-repeat center center;
	overflow: hidden;
}
.banner-content{
	width: 1200px;
	margin:0 auto;
	position: relative;
}

.inner .more{
	font-size: 14px;
	font-weight: bold;
	color:#000;
	line-height: 14px;
	position: absolute;
	right:80px;
	top:360px;
	padding-left: 21px;
	background: url("../images/banner_sprite.png") -120px 0 no-repeat;
}
```
这里将banner的盒子指定600px高度，以显示图片内容，图片实际尺寸（2000x600)超出了显示尺寸(1477x600),为此，采用背景图居中的方式（center，center）加载banner，并对额外部分进行隐藏（overflow:hidden)；为使内部链接便于定位，其所在父容器（banner-content)采用相对定位方式，使得所有banner-content的子元素可以采用相对于它的方式进行绝对定位。这里的more链接就采用绝对定位方式，并指定right和top绝对值坐标。此外，链接前需要显示一个链接图标，而且需要和链接保持一致的可点击效果，为实现这一目的，采用padding-left:21px，使得左侧腾出21px的内部边距以显示图标，而图标是由一张banner-sprite雪碧图构成，通过定位坐标值(-120px 0)显示指定的图标。

###characters效果图###
<img src="http://ww4.sinaimg.cn/large/6d025b55gw1ew8zt8nlwmj211v08c74j.jpg" />
###构建HTML结构###
```html
	<div class="characters">
		<div class="idx-width">
			<div class="characters-wrap">
				<span class="icon-1 hidden-text">专注IT学习</span>
				<span class="icon-2 hidden-text">聚焦实战开发</span>
				<span class="icon-3 hidden-text">课程完全免费</span>
			</div>
		</div>
	</div>
```
###构建相应CSS###
```CSS
.characters{
	background-color: #fff;
	min-width:1200px;
}
.idx-width{
	width:1200px;
	margin: 0 auto;
}
.characters-wrap{
	padding: 50px 120px;
	height: 183px;
	position: relative;
}
.icon-1,.icon-2,.icon-3{
	position: absolute;
	display: block;
	top: 50px;

}
.icon-1{
	background: url("../images/char-icon1.png") no-repeat left top;
	width: 135px;
	height: 183px;	
	left: 120px;
}
.icon-2{
	background: url("../images/char-icon2.png") no-repeat left top;
	width: 180px;
	height: 181px;
	left: 50%;
	margin-left: -90px;
}
.icon-3{
	background: url("../images/char-icon3.png") no-repeat left top;
	width: 166px;
	height: 181px;
	right: 120px;
}
.hidden-text{
	text-indent: 100%;
	white-space: nowrap;
	overflow: hidden;
}
```
三个span图标，以绝对定位的方式定位在父容器中，因此父容器设置position:relative;icon-1采用left:120px;而相应的icon-3采用right：120px;居中的icon-2采用left:50%,再向左移动自身宽度一半的方式（margin-left:-90px)