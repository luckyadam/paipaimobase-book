# cookie组件

> 用于对cookie的简易操作，提供了设置、获取、删除cookie的方法。

### 组件方法

| 方法名 | 描述 | 参数 | 返回值 |
| -- | -- | -- | -- |
| ``set`` | cookie的存操作 | @key ``String`` cookie的key<br >@value ``String`` cookie中key对应的值<br >@expires ``Number`` cookie过期时间<br >@path ``String`` 设置cookie的path<br >@domian ``String`` 设置cookie的domain<br >@secure ``Boolean`` 设置cookie是否只在安全连接https下起作用 | 无 |
| ``get`` | cookie的取操作 | @key ``String`` cookie的key| @value ``String`` 返回key对应的value，如果没有则返回``false`` |
| ``delete`` | 删除某一cookie | @key ``String`` cookie的key | @return ``Boolean`` 是否成功 |

### 使用方式

```javascript
/** 
 * 在某业务逻辑内部引用组件
 * 若在外部引用则是，PP.require
 */
var cookie = require('cookie');

/** 设置一个保留7天的名为test，值为1的cookie */
cookie.set('test', 1, 7);
/** 获取名为test的cookie */
cookie.get('test');
/** 删除名为test的cookie */
cookie.delete('test');
```