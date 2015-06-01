# Tab组件

### 代码示例
[codepen_embed height="252" theme_id="15631" slug_hash="GJreOV" default_tab="result" user="luckyadam"]See the Pen <a href='http://codepen.io/luckyadam/pen/GJreOV/'>GJreOV</a> by Li,Weitao (<a href='http://codepen.io/luckyadam'>@luckyadam</a>) on <a href='http://codepen.io'>CodePen</a>.[/codepen_embed]

### 组件参数

| 参数名称 | 描述 | 类型 | 是否可选 | 默认值 |
| -- | -- | -- | -- | -- |
| ``container`` | 指定tab容器 | ``String`` ``HTMLElement`` ``Zepto`` | **否** | ``null`` |
| ``head`` | tab的头部容器 | ``String`` ``HTMLElement`` ``Zepto`` | 是 | ``null`` |
| ``content`` | tab的内容容器 | ``String`` ``HTMLElement`` ``Zepto`` | 是 | ``null`` |
| ``startAt`` | 起始tab页 | ``String`` ``int`` | 是 | ``0`` |
| ``hash`` | 是否启用hash标记tab | ``Boolean`` | 是 | ``false`` |
| ``onBeforeSwitch`` | tab切换前触发的操作 | ``Function`` | 是 | ``function(){}`` |
| ``onAfterSwitch`` | tab切换后触发的操作 | ``Function`` | 是 | ``function(){}`` |
| ``onFirstShow`` | 每个tab首次show出来的时候触发的操作 | ``Function`` | 是 | ``function(){}`` |

### API

| 方法名 | 描述 | 参数 | 返回值 |
| -- | -- | -- | -- |
| ``setOption`` | 设置参数 | 同组件配置参数 | @this[``Object``]组件实例本身，方便链式调用 |
| ``switchTo`` | 切换tab | @index[``int`` ``String``]tab索引或是hash值 | @this[``Object``]组件实例本身，方便链式调用 |
| ``switchToNext`` | 切换到下一tab页 | 无 | @this[``Object``]组件实例本身，方便链式调用 |
| ``switchToPrev`` | 切换到上一tab页 | 无 | @this[``Object``]组件实例本身，方便链式调用 |
| ``destroy`` | 销毁组件，同时会解绑事件 | 无 | 无 |


### 使用方式

```javascript
/** 
 * 在某业务逻辑内部引用组件
 * 若在外部引用则是，PP.require
 */
var Tab = require('tab');

/** 实例化组件，传入参数 */
var tab = new Tab({
  container: $('.tab'),
  head: $('.tab_head'),
  content: $('.tab_content'),
  startAt: 0,
  hash: false,
  onBeforeSwitch: function () {},
  onAfterSwitch: function () {},
  onFirstShow: function () {}
});

```

### 组件HTML结构

```html
<!-- tab外层容器 -->
<div class="tab">
  <!-- tab头部容器 -->
  <div class="tab_head j_tab_head">
    <!-- 配置data-hash属性表示如果开启hash的话，hash将是它的值 -->
    <a href="javascript:;" class="tab_head_item j_tab_head_item" data-hash='aa'>tab1</a>
    <a href="javascript:;" class="tab_head_item j_tab_head_item" data-hash='bb'>tab2</a>
    <a href="javascript:;" class="tab_head_item j_tab_head_item" data-hash='ff'>tab3</a>
  </div>
  <!-- tab内容容器 -->
  <div class="tab_content j_tab_content">
    <div class="tab_content_item j_tab_content_item">1</div>
    <div class="tab_content_item j_tab_content_item">2</div>
    <div class="tab_content_item j_tab_content_item">3</div>
  </div>
</div>
```