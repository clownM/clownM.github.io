---
title: Chrome下getImageData的跨域问题
date: 2018-01-05 12:04:24
tags: 
- javascript
- canvas

---

在用canvas写颜色取反demo时用到getImageData方法无法获取图片信息。代码如下：

```javascript
(function(){
    var canvas = document.getElementById("mycanvas");
    var ctx = canvas.getContext("2d");

    var img = new Image();
    img.src = "res/cat1.jpg";
    img.onload = function(){
        ctx.drawImage(img,10,10,300,300);
        var drawing = ctx.getImageData(10,10,300,300);
        console.log(drawing.data);
        for(var i = 0; i < drawing.data.length;i+=4){
             drawing.data[i] = 255 - drawing.data[i];
             drawing.data[i+1] = 255 - drawing.data[i+1];
             drawing.data[i+2] = 255 - drawing.data[i+2];
        };            
        ctx.putImageData(drawing,350,10);
    }    
})();
```

<!--more-->

当在Chrome下预览时控制台报错，错误信息如下`Uncaught DOMException: Failed to execute 'getImageData' on 'CanvasRenderingContext2D': The canvas has been tainted by cross-origin data. `，而在IE和Edge下就没有这种情况。

经过在网上查阅，错误原因是getImageData（）方法跨域问题。图片文件存储在本地，默认为没有域名，chrome浏览器判断为跨域才报错。（更深层次的原因还待挖掘）

解决方法：把demo放在apache服务器跑就不会报错。

结果图如下：[![tT6h9.png](https://s1.ax1x.com/2017/10/20/tT6h9.png)](https://imgchr.com/i/tT6h9)

注：图片素材来源为知乎网友，侵删。

