# login组件

> 判断判断手Q/wx/H5中登录状态，在这些环境中跳转登录页

### 组件方法

| 方法名 | 描述 | 参数 | 返回值 |
| -- | -- | -- | -- |
| ``isLogin`` | 判断是否登录 | 无 | @return ``Boolean`` 是否登录 |
| ``go`` | 去登录页 | @rurl ``String`` 登录回调url| 无 |

### 使用方式

```javascript
/** 
 * 在某业务逻辑内部引用组件
 * 若在外部引用则是，PP.require
 */
var loginHelper = require('login');

/** 如果米有登录则跳转到登录页 */
if (!loginHelper.isLogin()) {
  loginHelper.go(rurl);
}
```