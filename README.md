# mina_question
小程序爬坑指南
## 1图片问题
小程序没法在wxss（css）中设置背景图的相对路径，`必须改成网址或者base64格式`，或者在wxml（html）中显示
## 2.onLoad和onShow的区别
onload可以看成进入页面初次事件加载，onshow的可以当作页面发生变化进行事件加载`（最主要的是，退出小程序，再次进入页面逻辑进行更改）`，onHide指退出前出发事件
## 3.跳转导航
wx.navigateTo      保留当前页面，跳转到应用内的某个页面,可以返回到原页面，路径不销毁
wx.redirectTo         关闭当前页面，跳转到应用内的某个页面
wx.navigateBack 关闭当前页面，返回上一页面或多级页面
`小程序目前页面路径最多只能十`
## 4.挂载数据和获取数据
区别于vue：挂载数据用到this.setData({"name":"jack"}) 获取数据this.data.name
区别react: 哈哈，木的区别
## 5.传参
父传子：在父级url挂在数据，在子级loading中，可以设置形参获取
## 6.跨域即白名单
在请求后端接口是可以`详情勾选不设置合法域名解决跨域`，也可以在小程序后台设置白名单（每月5次）
## 7.wxml问题
text                  只能嵌套text
textarea       设置maxlength="-1"不限制最大长度
scroll-view    可现实下拉加载
input                调起键盘遮住内容：？
## 8.事件
冒泡事件：当一个组件上的事件被触发后，该事件会向父节点传递。
非冒泡事件：当一个组件上的事件被触发后，该事件不会向父节点传递 。  
常用事件bindtap catchtap  dataset
bind事件绑定不会阻止冒泡事件向上冒泡，catch事件绑定可以阻止冒泡事件向上冒泡。
dataset在组件中可以定义数据，这些数据将会通过事件传递给 SERVICE。
