---
layout: post
title: "python下的lambda递归包装"
date: 2013-04-11 10:33:50 +0100
comments: true
categories: 
---

一直觉得python是一个c语系向lisp语系的妥协（比如行内for/if），这也把python的语法搞得复杂了许多，不过函数式思想渗透的依然不够彻底，主要表现在lambda函数不能进行递归调用（当然lisp也是不支持直接调用的），这样限制python下的lambda成为了一个鸡肋的语法糖，我在<a href="http://htedsv.com:8880/?id=3">笔记</a>的意义中也提到了。其实解决起来倒也简单——加一个包装，比如我定义为函数`g(func, args)`
```
g = lambda func, *args:  func(func, *args)
```

然后就可以写自递归函数了，例如经典的求阶乘

```
f = lambda self, n: 1 if n == 1 else n*self(self, n-1)
g(f, 10)
```