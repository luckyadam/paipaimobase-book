# 模块加载器

### 模块化

模块加载器是为了实现代码的模块化，打下工程化基础而存在的，在模块化以前，我们的代码结构松散，变量污染严重，非常不便于管理，因此我们需要借助一些工具来帮助我们规范我们的代码。

模块的英文名是**module**，一个模块应该是指一个具有完善功能的独立逻辑单元，原则上一文件一模块，比如页面中的一个列表，它的功能逻辑就属于比较独立的，所以可以把列表相关的逻辑抽成一个模块，当然，模块的拆分方法见仁见智，我们可以按照自己的想法去拆分模块，只要坚持这两个原则：

* 模块之间松耦合
* 模块的功能完善

### API

``module.js``中提供了一个模块加载器，它的设计思想借鉴了seajs的CMD规范，但是它的实现非常简单，与完整的CMD规范又有些不同。

加载器相关的方法都挂载在命名空间``PP``下，提供了如下API。

#### PP.define

使用``PP.define``来定义一个模块，它接受2个参数，第一个参数是模块id，第二个参数是模块方法。在基础组件库里面，模块id一般就是组件名，因为基础组件基本不会重名，但在编写业务逻辑模块时，模块id一般会是文件的相对路径，具体路径规则，需要结合业务代码结构，后面会补充完整。

使用方式如下

```javascript
/** 
 * 定义一个模块
 * 模块方法接受3个参数 require exports module
 * require方法用于同步引用其他模块
 * exports对象用于暴露模块需要暴露出得对外对象和方法
 * module指向当前模块，包含一些信息
 */
PP.define('module', function (require, exports, module) {
  // 同步引用一个模块
  var Pager = require('pager');
  var pager = new Pager();
  function People () {
  }

  People.prototype = {};
  // 对外暴露的方式
  // 挂载在exports上
  exports.People = People;

  // 直接return
  //return People;
  // 不建议覆写exports
});

```

#### require/PP.require

在模块定义内部可以使用参数``require``来同步引用模块（见定义模块），而在外部则可以使用``PP.require``来同步引用模块

```javascript
var Pager = PP.require('pager');
```

#### require.async

在模块定义内部可以通过``require.async``来异步加载模块，它支持同时加载多个模块，接受2个参数，第一个参数可以是模块id或是模块id数组，第二个参数是回调方法，它在接受模块id后会通过一些配置好的规则生成完整的文件绝对地址，然后动态创建标签，加载脚本。

```javascript
// 单独引用一个模块
require.async('module', function (module) {

});

// 引用多个模块
require.async(['module1', 'module2'], function (module1, module2) {

});
```

#### PP.use

通过``PP.use``方法来在外部使用模块，它支持同时加载多个模块，接受2个参数，第一个参数可以是模块id或是模块id数组，第二个参数是回调方法。如果要引用的模块已经存在，会是同步引用，反之，则会是异步加载。

```javascript
// 单独引用一个模块
PP.use('module', function (module) {

});

// 引用多个模块
PP.use(['module1', 'module2'], function (module1, module2) {

});
```

#### PP.addPathRule

如果全局的路径配置规则不满足需求，可以使用``PP.addPathRule``来增加异步请求路径规则。