#前端编码规范
------
##一.HTML 相关
------
>1.  文档类型统一使用HTML5 doctype；
>2. 根元素制定lang 属性<html lang="zh-CN">；
>3. 编码一律使用utf-8；
>4. 标签语义化；代码简洁化；必要的注释；适当考虑内容的重要程度来安排文档流的先后循序；
>5. 使用link dns-prefetch属性，减少dns查找；
```html
<!DOCTYPE HTML>
<html lang="zh-CN">
<head>
	<meta charset="UTF-8">
	<title></title>
	<meta name="description" content="">
	<meta name="keywords" content="">
	<link rel="dns-prefetch" href="//img1.ijinshan.com">
</head>
<body>
</body>
</html>
```
####合理引入js的方法
(1). 在head内使用动态创建script标签的方式引入js,实现异步加载
```html
<script type="text/javascript">
    var s=document.createElement('script'),
        h=document.getElementsByTagName("head")[0];
        s.type="text/javascript";
        s.async=true;
        s.src="*.js";
        h.appendChild(s);
</script>
```
(2). 在底部</body>前使用同步加载的方式；
```html
<script type="text/javascript" src="http://****.js?v=20150501"></script>
```
##二.CSS相关
1. 使用统一的 reset,请查看[reset.css](reset.css);
2. 在文档头部，使用link标签引入css文件,避免使用@import ,与link 标签相比，@import指令要慢很多，（通过sass 预处理器将多个css文件编译为一个文件）；
3. 以组件为单位组织代码块；使用规范的注释；
* 文件顶部注释；
```css
* @description: xxxxx中文说明
* @author: zhangpan
* @update: 2015-05-01 10:00
```
*  模块注释
```css
/*module1:module descript*/
/*module2:module descript*/
```
#### 书写规范：
1. class、id 命名中，一律采用小写加中划线的方式，不允许使用当谢字母或_;
2. 命名注意缩写，但不能盲目的使用缩写，
3. 尽可能提高代码模块的复用，样式尽量使用组合的方式；
4. 避免直接给标签设置样式；
5. 注意属性的书写顺序；
6. 清除浮动:[建议] 当元素需要撑起高度已包含内部的浮动元素时，通过对伪类设置clear 或触发BFC的方式clearflix.
7. 将z-index进行分层，对文档流绝对丁文的元素的视觉层级进行管理（避免z-index值得滥用）;
8. 使用图片精灵，合并需要的图标；
9. Hack,尽量避免使用hack，下面是常见的hack;
```css
padding:10px;
padding:9px\9; /*IE*/
padding:8px\0; /*IE8-IE9*/
*padding:5px; /*IE6-IE7*/
_padding:4px; /*IE6*/
```