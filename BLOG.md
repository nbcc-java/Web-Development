## 9/14/2015 8:12:38 PM 扁平化BLOG页面构建 ##
###构建带图片的文档预览效果###
**HTML部分**
			
```html
    <section class="gray-section">
		<div class="article-preview">
			<div class="image-section"><img src="images/pic01.jpg" alt="" /></div>
			<div class="text-section">
				<h2>又一个标题</h2>
				<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Incidunt et illum quaerat laborum voluptatem alias eveniet distinctio at nisi dolorum nulla nostrum soluta, ipsum beatae officiis, praesentium autem. </p>
			</div>
		</div>
```
**CSS部分**
```css
.image-section{
	width: 45%;
}
.image-section img{
	width:100%;
}
……
```

由于父标签div.image-section，只占据半行空间（width:45%)。此时，其子元素图片img标签，必须指定其图片宽度属性（width：100%），如果不加指定，图片将显示原有图片尺寸。

###制作更多的图片预览文档###
复制完成的article-preview section部分代码，以快速完成其余代码部分。此时，会发现两个相邻article-preview section之间有一个缝隙。（如图所示）他不是margin,也不是padding，更不是height导致的。而是由font-size导致的，可以将article-preview的font-size重置为0，以清除该缝隙。
