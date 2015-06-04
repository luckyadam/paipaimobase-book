# Dialog组件

>  对话框应该是web中非常常见的功能了，到处都可以见到各种各样的提示框，这里提供了一个基础的对话框类Dialog，它需要引用overlay组件，适用于开发过程中的扩展需求，同时基于Dialog提供了[Alert](#alert%E7%BB%84%E4%BB%B6)和[Confirm](#confirm%E7%BB%84%E4%BB%B6)两个非常实用的封装。

### 一个例子
[dialog](codepen://luckyadam/gpmbgw?height=360)

### 组件参数

| 参数名称 | 描述 | 类型 | 是否必须 | 默认值 |
| -- | -- | -- | -- | -- |
| ``title`` | 标题 | ``String`` | 否 | 空 |
| ``message`` | 简单信息 | ``String`` | 否 | 空 |
| ``content`` | 对话框主体内容 | ``String`` ``HTMLElement`` ``Zepto`` | 否 | 空 |
| ``btnDirection`` | 按钮排列的方向，支持两种方向，水平horizontal和垂直vertical | ``String`` | 否 | ``horizontal`` |
| ``mask`` | 是否展现遮罩层 | ``Boolean`` | 否 | ``true`` |
| ``modal`` | 对话框是否是模态的 | ``Boolean`` | 否 | ``true`` |

### 组件方法

| 方法名 | 描述 | 参数 | 返回值 |
| -- | -- | -- | -- |
| ``show`` | 展示对话框 | 无 | @this ``Object`` 组件实例本身，方便链式调用 |
| ``hide`` | 隐藏对话框 | 无 | @this ``Object`` 组件实例本身，方便链式调用 |
| ``addBtn`` | 为对话框增加按钮 | @options.text ``String`` 按钮文案<br>@options.onClick ``Function`` 按钮点击后动作<br >@options.isDefault ``Boolean`` 是否是默认按钮，默认按钮会有额外的样式展现<br >@options.isDisabled ``Boolean`` 是否禁用 <br >@options.destroyOnClick ``Boolean`` 点击后是否销毁 | @this ``Object`` 组件实例本身，方便链式调用 |
| ``on`` | 给对话框绑定事件 | 同Zepto中``$.fn.on``的参数 | @this ``Object`` 组件实例本身，方便链式调用 |
| ``off`` | 解绑对话框事件 | 同Zepto中``$.fn.off``的参数 | @this ``Object`` 组件实例本身，方便链式调用 |
| ``setTitle`` | 设置标题 | @title ``String`` 标题 | @this ``Object`` 组件实例本身，方便链式调用 |
| ``setMessage`` | 设置简单消息内容 | @messgae ``String`` 简单消息 | @this ``Object`` 组件实例本身，方便链式调用 |
| ``content`` | 获取/填充内容 | @content ``String`` ``HTMLElement`` ``Zepto`` 当content为空时是获取，否则是填充内容 | @this ``Object`` 填充内容时返货组件实例本身，方便链式调用<br >@content ``String`` 获取时返回内容 |
| ``destroy`` | 销毁组件，同时会解绑事件 | 无 | @this ``Object`` 组件实例本身，方便链式调用 |

### 使用方式

```javascript
/** 
 * 在某业务逻辑内部引用组件
 * 若在外部引用则是，PP.require
 */
var Dialog = require('dialog');

/** 实例化组件，传入参数 */
var dialog = new Dialog({
  title: '标题',
  message: '一些信息，只能是string',
  content: '<strong>提示</strong>这里是内容，可以写html'，
  btnDirection: 'horizontal',
  mask: true,
  modal: true
});
dialog.addBtn({
  text: '法师',
  isDefault: true
}).addBtn({
  text: '战士'
}).addBtn({
  text: '道士'
});
```

## Alert组件

> Alert是一个警告框组件，通常情况下它只有一个按钮，Alert是基于Dialog组件的，是对Dialog的一层封装。

### 一个例子
[alert](codepen://luckyadam/MwpYEq?height=360)

### 组件参数

| 参数名称 | 描述 | 类型 | 是否必须 | 默认值 |
| -- | -- | -- | -- | -- |
| ``title`` | 标题 | ``String`` | 否 | 空 |
| ``message`` | 简单信息 | ``String`` | 否 | 空 |
| ``okBtnText`` | ok按钮的文案 | ``String`` | 否 | 确定 |
| ``onOk`` | 点击ok按钮后要做的操作 | ``String`` | 否 | ``function () {}`` |

### 组件方法

无

### 使用方式

```javascript
/** 
 * 在某业务逻辑内部引用组件
 * 若在外部引用则是，PP.require
 */
var Alert = require('alert');

/** 实例化组件，传入参数 */
var alert = new Alert({
  title: '标题',
  message: '一些信息，只能是string'
});
```

## Confirm组件

> Confirm是一个确认框组件，通常情况下它有二个按钮，Confirm是基于Dialog组件的，是对Dialog的一层封装。

### 一个例子
[confirm](codepen://luckyadam/jPBEaz?height=360)

### 组件参数

| 参数名称 | 描述 | 类型 | 是否必须 | 默认值 |
| -- | -- | -- | -- | -- |
| ``title`` | 标题 | ``String`` | 否 | 空 |
| ``message`` | 简单信息 | ``String`` | 否 | 空 |
| ``okBtnText`` | ok按钮的文案 | ``String`` | 否 | 确定 |
| ``cancelBtnText`` | cancel按钮的文案 | ``String`` | 否 | 取消 |
| ``onOk`` | 点击ok按钮后要做的操作 | ``String`` | 否 | ``function () {}`` |
| ``onCancel`` | 点击cancel按钮后要做的操作 | ``String`` | 否 | ``function () {}`` |

### 组件方法

无

### 使用方式

```javascript
/** 
 * 在某业务逻辑内部引用组件
 * 若在外部引用则是，PP.require
 */
var Confirm = require('confirm');

/** 实例化组件，传入参数 */
var confirm = new Confirm({
  title: '标题',
  message: '一些信息，只能是string'
});
```