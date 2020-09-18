# mina_question
小程序爬坑指南
## 1图片问题
小程序没法在wxss（css）中设置背景图的相对路径，`必须改成网址或者base64格式`，或者在wxml（html）中显示
## 2.onLoad和onShow的区别
onload可以看成进入页面初次事件加载，onshow的可以当作页面发生变化进行事件加载`（最主要的是，退出小程序，再次进入页面逻辑进行更改）`，onHide指退出前出发事件
