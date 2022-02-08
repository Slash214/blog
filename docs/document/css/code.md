# 日常开发 CSS CODE

### 初始化CSS代码  

> 在开发页面之前都应先重置CSS代码保证书写的CSS代码在每一个浏览器的一致性
```
a,abbr,acronym,address,applet,area,article,aside,audio,b,base,basefont,bdi,bdo,big,blockquote,
body,br,button,canvas,caption,center,cite,code,col,colgroup,datalist,dd,del,details,dir,
div,dfn,dialog,dl,dt,em,embed,fieldset,figcaption,figure,font,footer,form,frame,frameset,
h1,h2,h3,h4,h5,h6,head,header,hr,html,i,iframe,img,input,ins,isindex,kbd,keygen,label,legend,
li,link,map,mark,menu,menuitem,meta,meter,nav,noscript,object,ol,optgroup,option,output,p,param,
pre,progress,q,rp,rt,ruby,s,samp,script,section,select,small,source,span,strike,strong,style,sub,
summary,sup,table,tbody,td,textarea,tfoot,th,thead,time,title,tr,track,tt,u,ul,var,video,wbr,xmp {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

*::before,
*::after {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font: 14px/1 "PingFang SC", "Microsoft YaHei", sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}

img {
    display: block;
    border: none;
}

dl,
li,
menu,
ol,
ul {
    list-style: none;
}

button,
input,
select,
textarea {
    box-sizing: border-box;
    outline: none;
}

a,
a:link,
a:visited,
a:hover,
a:active {
    text-decoration: none;
}

/* 浮动方式 */
.fl {
    float: left;
}

.fr {
    float: right;
}

.cl:after {
	content: "";
	display: block;
	overflow:hidden;
	visibility:hidden;
	height: 0;
	clear: both;
}
.cl {
	zoom: 1;
}

```
### 图片未加载前自动撑开元素高度

> 在移动端开发中，有一些元素是根据图片高度来自动撑开的 ，高度不能写死（如轮播图的外层元素）。在网络较慢的情况下，图片加载需要一些时间，此时该元素的高度没有被撑开，在网页布局上会有一些不想看到的效果。 这种情况我们可以设置如下样式来设置该元素的高度：

```
.wrapper
  overflow hidden
  width 100%
  height 0
  padding-bottom 26.66% // 这个数值是图片的高宽比，即 高/宽
  background #eee
```

### 文本溢出隐藏 
> 单行本隐藏
```
{
    width: 200px; // 文本宽度
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}
```

> 多文本隐藏
```
{
    width: 200px;  // 文本宽度
    overflow : hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 2;  // 显示超过几行时隐藏
    -webkit-box-orient: vertical;
}
```

