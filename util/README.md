# Util

> Util部分包括一些工具性质的方法

### scrollToPosition

``scrollToPosition(selector, [callback], [delay], [duration])``

滚动页面到某一位置，接受4个参数，后三个参数为可选参数。

*selector* 必选，可以是选择器、Dom或Zepto对象，这时表示将滚动到这一元素的位置；还可以是数字，表示将滚动页面到Y轴上这一位置

*callback* 可选，滚动完成后的回调操作

*delay* 可选，滚动开始前的延时

*duration* 可选，滚动动画的持续时间
