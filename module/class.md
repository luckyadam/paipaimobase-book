# 类生成器

**JavaScript**一直以来都没有类的概念，这一囧境知道**ES6**中才得以改善，目前我们实现类的方式主要是通过构造函数+prototype来实现，这种方式太过简陋，而且在团队协作中，会出现写法各异的情况，所以我们需要一个类生成器来约束类的实现方式，统一风格。

``class.js``就是一个类生成器，提供一个``extend``方法来生成需要的类，``_.Class``默认是所有类的基类，其他的类都是从它继承出来，目前提供的功能比较简单，但是能起到一定的约束作用，使用方式如下

```
// 构建类
var People = _.Class.extend({
	// 类静态成员
	statics: {
		
	},
	
	// 构造函数，若不需要可缺省
	construct: function (name) {
		this.name = name;
	},
	
	talk: function () {
		console.log('My name is ' + this.name + '!');
	}
	
	// 其他成员方法
	...

});

// 继承People
var Man = People.extend({

	construct: function (name, age) {
		// 执行父类的方法
		this.super.call(this, arguments);
	},
	
	walk: function () {
		console.log('I am ' + this.age + ' years old, I can walk!');
	}
	
	// 其他成员方法
	...
});

// 使用
var luckyadam = new Man('luckyadam', 23);
luckyadam.talk();
luckyadam.walk();
```