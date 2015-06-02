# Toast组件

> Toast是一个简易的消息提示浮层，采用单例模式，功能非常单一，用于在屏幕中央显示一个定期消失的提示浮层

> Toast需要依赖Overlay组件

### 一个例子

[Toast](codepen://luckyadam/waJBvo)

### 组件参数

| 参数名称 | 描述 | 类型 | 是否必须 | 默认值 |
| -- | -- | -- | -- | -- |
| ``content`` | 提示信息内容 | ``String`` ``HTMLElement`` ``Zepto`` | 否 | 空 |
| ``duration`` | 持续时间 | ``int`` | 否 | ``3000`` |

注：可以只传一个 ``String`` 类型的参数，这样会将它直接作为内容进行设置。

### 组件方法

| 方法名 | 描述 | 参数 | 返回值 |
| -- | -- | -- | -- |
| ``show`` | 展现信息提示框 | 无 | @this ``Object`` 组件实例本身，方便链式调用 |
| ``hide`` | 隐藏信息提示框 | 无 | @this ``Object`` 组件实例本身，方便链式调用 |
| ``content`` | @content ``String`` ``HTMLElement`` ``Zepto`` 当content为空时是获取，否则是填充内容 | 无 | @content ``String`` 获取时返回内容 |

### 使用方式

```javascript
/** 
 * 在某业务逻辑内部引用组件
 * 若在外部引用则是，PP.require
 */
var Toast = require('toast');

/** 实例化组件，传入参数 */
/** 传入完整参数 */
var toast = new Toast({
  content: '成功了！',
  duration: 5000
});

/** 只传入字符串 */
var toast = new Toast('又成功了！');
```