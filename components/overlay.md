# Overlay组件

### 一个例子

### 组件参数

| 参数名称 | 描述 | 类型 | 是否必须 | 默认值 |
| -- | -- | -- | -- | -- |
| ``content`` | 遮罩层要包含的内容 | ``String`` ``HTMLElement`` ``Zepto`` | 否 | 空 |
| ``mask`` | 是否显示遮罩层 | ``Boolean`` | 否 | ``true`` |
| ``modal`` | 是否是模态的 | ``Boolean`` | 否 | ``true`` |

### 组件方法

| 方法名 | 描述 | 参数 | 返回值 |
| -- | -- | -- | -- |
| ``show`` | 显示遮罩层 | 无 | @this ``Object`` 组件实例本身，方便链式调用 |
| ``hide`` | 隐藏遮罩层 | 无 | @this ``Object`` 组件实例本身，方便链式调用 |
| ``on`` | 给遮罩层绑定事件 | 同``Zepto``中``$.fn.on``的参数 | @this ``Object`` 组件实例本身，方便链式调用 |
| ``off`` | 遮罩层事件解绑 | 同``Zepto``中``$.fn.off``的参数 | @this ``Object`` 组件实例本身，方便链式调用 |
| ``content`` | 获取/填充内容 | @content ``String`` ``HTMLElement`` ``Zepto`` 当content为空时是获取，否则是填充内容 | @this ``Object`` 填充内容时返货组件实例本身，方便链式调用<br> @content ``Zepto`` 获取时返回内容 |
| ``destroy`` | 销毁组件，同时会解绑事件 | 无 | 无 |

### 使用方式