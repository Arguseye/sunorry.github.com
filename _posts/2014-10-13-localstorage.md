---

layout: post
title: localstorage
categories: [learn]

---

##cookies
**缺点**
* http请求头都会带着（三次握手，请求回报...）
* 大小 4K
* 主 Domain 污染（主域名下，所有子域名也有）

##localstorage && sessionstorage
永久存储，永不失效，除非手动删除，5M，子域名不能不能共享，需借助 HTML5 postmessage
**API**
* getItem
* setItem
* removeItem
* key
* clear
可以存储：数组，json，图片，脚本，样式文件（有些得序列化）
存图片见自己的 github 
**注意**
* 需要异常处理，避免超出容量抛错(LRU,FIFO)
* key 唯一
* 避免把敏感信息存本地
* server端如何取代？（ajax请求）

1. 利用本地数据，减少网络传输
2. 弱网络环境下，高延迟，地宽带，尽量把数据本地化

##indexedDB database
一种能在浏览器中持久地存储结构化数据的**数据库**， 并且为 web 应用提供了丰富的**查询**能力
