# 组件库

> 在我们平时开发的过程中会发现有很多的功能是通用的，为了实现同样的功能我们可能会到处去找之前的代码，引用或是直接拷贝，这就会造成代码冗余、结构混乱。所以我们需要将这些通用功能进行梳理，基于统一的规范，构建出一个能持续发展的组件库，在降低我们的开发时间、提升我们的开发效率之余为我们的开发工作提供更流畅的开发体验。

## 开始

组件库是基于拍拍无线基础库中的模块加载器之上构建出来的，将分为**UI组件**和**功能性组件**两部分，定义组件的基本形式如下

```javascript
/**
 * 定义一个的tab组件
 * 多例，返回类
 */
PP.define('tab', function (require) {
  var Tab = _.Class.extend({
    // 组件类静态成员
    statics: {
    },
		
    // 构造函数
    construct: function (options) {
    },
		
    // 切换tab 
    switchTo: function (index) {
      
    }
  });
  return Tab;
});

/**
 * 定义一个的cookie操作组件
 * 单例，允许直接返回一个对象
 */
PP.define('cookie', function (require) {
  function setCookie () {

  }
  function getCookie () {

  }
  function deleteCookie () {

  }
  return {
    set: setCookie,
    get: getCookie,
    delete: deleteCookie
  };
});
```
我们将按照如下的方式来使用组件

```javascript
// 某业务逻辑内部调用tab
var Tab = require('tab');
var tab = new Tab({

});
// 切换到第二个tab
tab.switchTo(1);

// 调用cookie组件
var cookie = require('cookie');
// 设置一个保留7天的名为test，值为1的cookie
cookie.set('test', 1, 7);
// 获取名为test的cookie
cookie.get('test');
// 删除名为test的cookie
cookie.delete('test');
```
虽然基础已提供了模块异步加载的方式，但目前基础组件将使用合并打包成一个文件的方式来同步调用，一是因为基础目前项目路径没有确定，二是基础组件目前本身不大，后续若组件库持续增加，则会通过定义路径规则，来让组件支持异步调用的形式。

## 分类

### 功能性组件

 - URL参数的相关操作
 - 翻页组件 pager
 - 延迟加载 lazyload

### UI组件 

 - 遮罩层 Overlay
 - 弹窗 Dialog
 - Tab
 - 区域内滚动 Scoller
 - 轮播 Carousel
 - 回到顶部 GoTop
 - 加载动画loading
 - 下拉刷新 pullrefresh
 - 上拉加载 loader

## 更新日志

**2015·5·22**

*增加URL处理组件*， 这是一个提供了快速操作url参数的功能性组件，在平时的开发中我们有时会需要获取某个url的参数，修改它，然后写回，这个组件提供了非常方便的接口让我们来处理这些操作。[查看示例](http://labs.qiang.it/h5/paipaimo-base/guide/components/uri.html)

*增加tab组件*， tab在web中非常常见，这个组件就是提供了tab功能，但同时它还有一些扩展，比如增加了hash功能，支持页面hash，而且支持初始化定位tab，功能比较完善。[查看示例](http://labs.qiang.it/h5/paipaimo-base/guide/components/tab.html)

**2015.5.29**

*增加遮罩层overlay组件*， 这个组件的主要功能就是生成一个覆盖在页面上的遮罩层，提供了一些初始化选项。它接受一个参数`content`来给遮罩层设置内容，目前仅支持让内容居中显示，后续可以支持提供位置选择。[查看示例](http://labs.qiang.it/h5/paipaimo-base/guide/components/overlay.html)

*增加对话框组件dialog*， 对话框应该是web中非常常见的功能了，到处都可以见到各种各样的提示框，这里提供了一个基础的对话框类`Dialog`，它需要引用`overlay`组件，适用于开发过程中的扩展需求，同时基于`Dialog`提供了`Alert` `Confirm`两个非常常用的封装。[查看示例](http://labs.qiang.it/h5/paipaimo-base/guide/components/dialog.html)

*增加简易提示框toast*，toast是一个简易的消息提示浮层，在设计中属于单例，功能也非常单一，用于在屏幕中央显示一个定期消失的提示浮层。[查看示例](http://labs.qiang.it/h5/paipaimo-base/guide/components/toast.html)
