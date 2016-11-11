---
title: es6定义对象class编译到es5代码解读
---

## es6定义对象class编译到es5代码解读

###### 1.es6代码：

```
class one {
  say() {
    console.log("hello world");
  }
}
```



上面使用es6的class定义一个简单的类，使用`babel`编译到es5的代码是什么样子？

###### 2. es5代码如下：

```
'use strict';
//1.定义拷贝函数
var _createClass = function () {
  function defineProperties(target, props) {
    for (var i = 0; i < props.length; i++) {
      var descriptor = props[i];
      descriptor.enumerable = descriptor.enumerable || false;
      descriptor.configurable = true;
      if ("value" in descriptor) descriptor.writable = true;
      Object.defineProperty(target, descriptor.key, descriptor);
    }
  }
  return function (Constructor, protoProps, staticProps) {
    if (protoProps) defineProperties(Constructor.prototype, protoProps);
    if (staticProps) defineProperties(Constructor, staticProps);
    return Constructor;
  };
}();

//2. 检查构造函数
function _classCallCheck(instance, Constructor) {
  if (!(instance instanceof Constructor)) {
    throw new TypeError("Cannot call a class as a function");
  }
}

//3. 定义对象函数
var one = function () {
  function one() {
    _classCallCheck(this, one);
  }

  _createClass(one, [{
    key: 'say',
    value: function say() {
      console.log('hello world');
    }
  }]);

  return one;
}();
```

###### 3. 解读es5代码

编译后的代码分共三个函数。

1）

定义_createClass = 一个立即执行匿名函数。匿名函数内部定义`definProperties`函数将属性循环拷贝到目标对象上； 然后返回一个函数有三个参数`(Constructor, protoProps, staticProps)`, 内部调用`definProperties` 分别将原型属性拷贝到构造函数的原型，静态属性拷贝到构造函数本身，并返回此构造函数。

2）

定义类型检查报错函数`_classCallCheck`,如果instance不是构造函数的实例，抛出错误：不能将类当做函数调用？

3）

定义我们写的es6代码中的类`one`,也是一个立即函数，定义一个空函数，调用`_createClass`将es6中class定义的函数以键值对的形式组合成数组对象传递进去。

###### 4. 总结

es6的class转换为es5代码实际就是创建一个与class类名相同的构造函数，并将class中的属性方法绑定到同名构造函数的原型上的过程。要调用one的属性方法还需要`new`实例化。