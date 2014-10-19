---

layout: post
title: jQuery Observer Pattern
categories: [learn]

---

##jQuery 中的观察者模式（Observer Pattern）

### on & trigger

```js
$(function() {
  $('body').on('someclick', function() {
    console.log('ops, clicked!');
  });
  $('body').trigger('someclick');
});
```

当然，自定义事件的名称可以按照**“命名空间.自定义事件名称”**的形式来写，比如 `app.someclick` ，这在大型项目中尤其有用，这样可以有效避免自定义事件名称冲突。

如果从“发布订阅”的角度来看，on 方法相当于订阅者、观察者，trigger 方法相当于发布者。

###从“异步获取 json 数据”来体验 jQuery 观察者模式

如果用一个全局变量来接收异步获取的 json 数据:
```js
$(function(){
  var data;
  $.getJSON('data.json', function(results) {
    data = results;
  });
  console.log(data);
});
```
我们得到的结果是 undefined 。因为异步的原因。

**如何解决这个问题？**
如果在$.getJSON方法之外先定义好需要执行的方法，然后在$.getJSON方法的回调函数里真正触发这个方法，不就解决了吗？
```js
$.getJSON('data.json', function(results) {
  $(document).trigger('app.myevent', results); //相当于发布
});
$(document).on('app.myevent', function(e, results) { //相当于订阅
  console.log(results);
});
```
以上，on 方法就像一个订阅者，它订阅了自定义事件 app.myevent ；而 trigger 方法就像一个发布者，它发布事件和参数后，才真正让订阅者方法得以执行。

###jQuery 观察者模式的扩展方法
```js
(function($) {
  var o = $({}); //自定义事件对象
  $.each({
    trigger: 'publish',
    on: 'subscribe',
    off: 'unsubscribe'
  }, function(key, val) {
    jQuery[val] = function() {
      o[key].apply(o, arguments);
    }
  });
})(jQuery);
```
以上，定义了全局的publish和subscribe方法，我们在任何时候都可以调用。

```
$(function () {
  $.getJSON('data.json', function (results) {
    $.publish('app.myevent', results);
  });
  $.subscribe('app.myevent', function(e, results) {
    $('body').html(
        results.one
    );
  });
});

**总结：jQuery的观察者模式，实际上是让on方法绑定的自定义事件先不执行，直到使用trigger方法来触发事件。使用jQuery的观察者模式的好处是：一次发布，多次订阅。**