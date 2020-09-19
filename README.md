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
## 9.live-pusher（实时音视频录制。）
  - tip: live-pusher 组件是由客户端创建的原生组件，它的层级是最高的，不能通过 z-index 控制层级。可使用 cover-view cover-image覆盖在上面。
  - live-pusher   ios上面不支持点击事件,所以要设置在cover-view上面
  - tip: 请勿在 scroll-view、swiper、picker-view、movable-view 中使用 live-pusher 组件。
  - tip: css 动画对 live-pusher 组件无效。
## 9.小程序限制
### 1.文件大小限制
源代码打包后大小限制为2M,单次通过 wx.request传输的数据最大也是1M。
### 2.数据传输长度最大限制
解决不要挂载在page/data下，在page外面设置全局变量，在page直接写变量名引入
在page里面设置局部变量
## 10小程序组件化思想
其核心思想：
- 1、组件页面	，依赖组件的页面<import>
- 2、@import组件样式
- 3、组件逻辑：	
在子组件中,把数据/组件事件/调用方法，统一在复制放入一个函数当前页的实例中，改变this 的指向
数据要多嵌套一层，避免跟父组件冲突，并统一命名方便后续解构赋值
暴露函数名
在父组件中引入js，css，wxml(注:wxml引入需要用到import的组件样式)
子组件设置name父组件设置is一致并在后面data设置解构赋值
- 4、组件通信：	
父传子 直接修改就可以，因为已经把指针合并了，所以this的指向相同，不信哈，你可你console的啊
子传夫 同理
## 11小程序的更新机制
小程序不像比的开发，每次开发迭代，在引入js/css时候在后面就参数就可以完美的结局跟新上线
小程序迭代的比较快，每次发布了新的代码，都	更新不及时，着急的时候，得删除了重新搜索才可以。觉得很		 麻烦，就查了一些方法。

## 12 mpvue实现vue开发
## 13关于小程序 scroll-view 左右横向滑动没有效果（无法滑动）问题
小程序组件 scroll-view 中分别有上下竖向滑动和左右横向滑动之分，在这次项目中刚好需要用到横向滑动，但在测试过程中发现横向滑动没有了效果（静止在那里没移动过），经调试发现：
- 1.scroll-view 中的需要滑动的元素不可以用 float 浮动；
- 2.scroll-view 中的包裹需要滑动的元素的大盒子用 display:flex; 是没有作用的；
- 3.scroll-view 中的需要滑动的元素要用 dislay:inline-block; 进行元素的横向编排；
- 4.包裹 scroll-view 的大盒子有明确的宽和加上样式-->  overflow:hidden;white-space:nowrap;
## 微信小程序wx.uploadFile的两个坑

var data = JSON.parse(res.data)　　//坑2：与wx.request不同，wx.uploadFile返回的是[字符串]，需要自己转为JSON格式
