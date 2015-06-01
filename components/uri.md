# Uri组件

### 组件参数

| 参数名称 | 描述 | 类型 | 是否可选 | 默认值 |
| -- | -- | -- | -- | -- |
| ``url`` | 待处理的url | ``String`` | **否** | 无 |

### 组件方法

| 方法名 | 描述 | 参数 | 返回值 |
| -- | -- | -- | -- |
| ``getQueryParamValue`` | 获取某参数的值 | @param ``String`` 参数 | @value ``String`` 参数对应的值 |
| ``replaceQueryParam`` | 替换某参数的值 | @param ``String`` url参数<br> @value ``String`` 参数新的值| 无 |
| ``getKeyValue`` | 获取url的一些信息，比如``protocol`` ``host``等 | @key ``String`` | @value ``String`` |
| ``toString`` | 获取做了改变后的新的url | 无 | @url ``String`` |

### 使用方式

```javascript
/** 
 * 在某业务逻辑内部引用组件
 * 若在外部引用则是，PP.require
 */
var Uri = require('uri');

/** 实例化组件，传入参数 */
var uri = new Uri('http://www.jd.com/test?param1=aa&param2=bb');

/** 获取参数param1的值 */
var param1 = uri.getQueryParamValue('param1'); // 输出 aa

/** 替换param2的值 */
uri.replaceQueryParam('param2', 'vv');

/** 获取url的protocol */
var protocol = uri.getKeyValue('protocol'); // 输出 http

console.log(uri.toString()); // 输出 http://www.jd.com/test?param1=aa&param2=vv
```