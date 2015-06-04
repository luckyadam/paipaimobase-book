# GoTop组件

> 返回顶部组件，会在页面中插入一个返回顶部的按钮。

> 需要依赖Util库，因为[滚动页面的方法](http://labs.qiang.it/h5/paipaimo-base/guide/util/index.html#scrolltoposition)已经封装在Util中。

### 一个例子

[goTop](codepen://luckyadam/vOxaxQ)

### 组件参数

| 参数名称 | 描述 | 类型 | 是否必须 | 默认值 |
| -- | -- | -- | -- | -- |
| ``scrollScreens`` | 滚动多少屏出现返回顶部按钮 | ``Number`` | 否 | ``1`` |
| ``duration`` | 滚动动画持续时间，默认为0，即不带动画 | ``Number`` | 否 | ``0`` |

### 组件方法

| 方法名 | 描述 | 参数 | 返回值 |
| -- | -- | -- | -- |
| ``show`` | 展示返回顶部按钮 | 无 | @this ``Object`` 组件实例本身，方便链式调用 |
| ``hide`` | 隐藏返回顶部按钮 | 无 | @this ``Object`` 组件实例本身，方便链式调用 |
| ``destroy`` | 销毁组件，同时会解绑事件 | 无 | 无 |

### 使用方式

```javascript
/** 
 * 在某业务逻辑内部引用组件
 * 若在外部引用则是，PP.require
 */
var GoTop = require('go_top');

/** 实例化组件，传入参数 */
var goTop = new GoTop({
  scrollScreens: 0,
  duration: 200
});
```