## ES5如何用prototype实现继承
```js
// 1.Person类的构造函数
function Person (name) {
  this.name = name
  console.log('Person')
}

// 2.Person类的方法showName
Person.prototype.showName  = function showName () {
  console.log(this.name)
}

// 3.Child类的构造函数
function Child (name, parentName) {
  // 4.调用Person类的构造函数
  Person.call(this, name)
  this.parentName = parentName
  console.log('Child')
}

/**
* 5.创建Child.prototype并使Child.prototype.prototype＝Person.prototype
*/
Child.prototype = Object.create(Person.prototype)

// 6.Child类的方法showParentName
Child.prototype.showParentName = function showParentName () {
  console.log(this.parentName)
}

const child = new Child('xiao ming', 'lao ming') // 7.输出：Person Child

/**
* 8.在Child类的实例上调用Person类的的方法
* js引擎会walk on prototype chain, 依次在Child.prototype -> Person.prototype（是Child.prototype.prototype，见5）上找搜索，最终在Person.prototype上找到showName方法后完成调用
*/
child.showName() // 输出：xiao ming
```
## 用ES6 class实现继承

```js
class Person {
    constructor (name) {
        this.name = name
    }
    showName () {
        console.log(this.name)
    }
}

class Child extends Person {
    constructor (name, parentName) {
        super(name)
        this.parentName = parentName
    }
    showParentName () {
        console.log(this.parentName)
    }
}
```

用ES6实现继承，由于关键词更达意，代码显得简洁了很多。下面我们看看[经babel转换的ES5代码](https://babeljs.io/repl#?babili=false&browsers=&build=&builtIns=false&spec=false&loose=false&code_lz=MYGwhgzhAEAKCmAnCB7AdtA3gKGn6w6EALogK7DEqLQAUaYAtvAJRa76fEAWAlhADoGzaAF5ow-BzwBfadAjcUAdwByTeHTY5OnQmlQh4AkCgDmtHvyEaW8uXOyhIMAMJ8QAE2jwAHsXg0TxgEZHR2PSJSCioaeg0AGmgABzBEQOJ1Zm15TggyZKR47Nz8K0FU9LRMjTEUtIysqU45PKVlWAbqpq0I3Tx9Q2NTC3KBSsbbe2wZIA&debug=false&forceAllTransforms=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&timeTravel=false&sourceType=module&lineWrap=true&presets=es2015%2Creact%2Cstage-2&prettier=false&targets=&version=7.4.3&externalPlugins=)是什么。不用怕多，其它不用看，我们只搜索Object.create，就会发现_inherits函数同样是用Object.create做了prototype绑定。
```
"use strict";

function _typeof(obj) { if (typeof Symbol === "function" && typeof Symbol.iterator === "symbol") { _typeof = function _typeof(obj) { return typeof obj; }; } else { _typeof = function _typeof(obj) { return obj && typeof Symbol === "function" && obj.constructor === Symbol && obj !== Symbol.prototype ? "symbol" : typeof obj; }; } return _typeof(obj); }

function _possibleConstructorReturn(self, call) { if (call && (_typeof(call) === "object" || typeof call === "function")) { return call; } return _assertThisInitialized(self); }

function _assertThisInitialized(self) { if (self === void 0) { throw new ReferenceError("this hasn't been initialised - super() hasn't been called"); } return self; }

function _getPrototypeOf(o) { _getPrototypeOf = Object.setPrototypeOf ? Object.getPrototypeOf : function _getPrototypeOf(o) { return o.__proto__ || Object.getPrototypeOf(o); }; return _getPrototypeOf(o); }

function _inherits(subClass, superClass) { if (typeof superClass !== "function" && superClass !== null) { throw new TypeError("Super expression must either be null or a function"); } subClass.prototype = Object.create(superClass && superClass.prototype, { constructor: { value: subClass, writable: true, configurable: true } }); if (superClass) _setPrototypeOf(subClass, superClass); }

function _setPrototypeOf(o, p) { _setPrototypeOf = Object.setPrototypeOf || function _setPrototypeOf(o, p) { o.__proto__ = p; return o; }; return _setPrototypeOf(o, p); }

function _instanceof(left, right) { if (right != null && typeof Symbol !== "undefined" && right[Symbol.hasInstance]) { return right[Symbol.hasInstance](left); } else { return left instanceof right; } }

function _classCallCheck(instance, Constructor) { if (!_instanceof(instance, Constructor)) { throw new TypeError("Cannot call a class as a function"); } }

function _defineProperties(target, props) { for (var i = 0; i < props.length; i++) { var descriptor = props[i]; descriptor.enumerable = descriptor.enumerable || false; descriptor.configurable = true; if ("value" in descriptor) descriptor.writable = true; Object.defineProperty(target, descriptor.key, descriptor); } }

function _createClass(Constructor, protoProps, staticProps) { if (protoProps) _defineProperties(Constructor.prototype, protoProps); if (staticProps) _defineProperties(Constructor, staticProps); return Constructor; }

var Person =
/*#__PURE__*/
function () {
  function Person(name) {
    _classCallCheck(this, Person);

    this.name = name;
  }

  _createClass(Person, [{
    key: "showName",
    value: function showName() {
      console.log(this.name);
    }
  }]);

  return Person;
}();

var Child =
/*#__PURE__*/
function (_Person) {
  _inherits(Child, _Person);

  function Child(name, parentName) {
    var _this;

    _classCallCheck(this, Child);

    _this = _possibleConstructorReturn(this, _getPrototypeOf(Child).call(this, name));
    _this.parentName = parentName;
    return _this;
  }

  _createClass(Child, [{
    key: "showParentName",
    value: function showParentName() {
      console.log(this.parentName);
    }
  }]);

  return Child;
}(Person);
```
## ES6类继承缺陷

从上面例证我们得出，ES6的类继承同样基于prototype的。那么，有prototype就是一个类可被继承的必要条件。JS里大部分‘类’，都满足这个条件，比如Array、Map、Element，但也有例外，比如Proxy。可在浏览器控制台输入Proxy.prototype，结果将是undefined。下面代码将报错:
```js
class Sub extends Proxy {}
// Uncaught TypeError: Class extends value does not have valid prototype property undefined
```

## 解决方案

1. 用组合代替继承（可参考：[踩坑案例](https://github.com/zzz945/write-vue3-from-scratch/commit/3d4b919252a98a9f6898329016a17aa1d6d2da70)）
2. 高阶函数代替继承（提示：js函数可以返回class）

## 作者其它文章链接

[用vue3公开的思路从0实现最简化的vue](https://github.com/zzz945/write-vue3-from-scratch)
