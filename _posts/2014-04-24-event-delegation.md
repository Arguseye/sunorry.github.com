---

layout: post
title: event delegation
categories: [learn]

---

不具教学意义，只供自己回顾

JS 事件委托

依靠事件冒泡将事件加到父元素上，然后用

```javascript

      var e = e || window.event;
      var target = e.target || ev.srcElement;
      target.nodeName.toUpperCase() == "LI"

```

这样就可以绑定到具体的元素上了。

好处：

1. 节约资源，不用给所有元素都添加事件;
2. 新添加的元素也有事件。


会遇到的情况：

```javascript
  <ul id="parent-list">
      <li id="post-1"><span>Item 1</span></li>
      <li id="post-2"><span>Item 2</span></li>
  </ul>
```

> 此时浏览器捕获到 click 事件的目标对象变为 span，所以如果我们希望获得 span 父元素 li 的 id 时需要通过 e.target.parentNode.id 来获得。

详情见(也是参考)：
[Javascript - 事件委托是怎么工作的？](http://blog.segmentfault.com/stephenlee/1190000000473293) <br>
[妙味课堂BBS](miaov.com/bbs)
