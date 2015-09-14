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
