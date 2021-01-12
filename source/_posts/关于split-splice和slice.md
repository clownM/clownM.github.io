---
title: '关于split,splice和slice'
date: 2018-03-09 20:21:41
tags: 原生js
---

1.split()方法是用于把一个字符串分割成字符串数组。

```
let str = "a+b+c+d";
let arr = str.split("");
console.log(arr)
let arr2 = str.split("+");
console.log(arr2)
```

程序运行的结果是

```
["a","+","b","+","c","+","d"]
["a","b","c","d"]
```

2.splice()方法向/从数组中添加/删除项目，然后返回被删除的项目。该方法会改变原始数组。

3.slice()方法可从已有的数组中返回选定的元素