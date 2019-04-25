## ES5如何用prototype实现继承

下面是ES5仿class效果的最简化实现

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

用ES6实现继承，由于关键词更达意，代码显得简洁了很多。下面我们看看[经babel转换的ES5代码](https://babeljs.io/repl#?babili=false&browsers=&build=&builtIns=false&spec=false&loose=false&code_lz=MYGwhgzhAEAKCmAnCB7AdtA3gKGn6w6EALogK7DEqLQAUaYAtvAJRa76fEAWAlhADoGzaAF5ow-BzwBfadAjcUAdwByTeHTY5OnQmlQh4AkCgDmtHvyEaW8uXOyhIMAMJ8QAE2jwAHsXg0TxgEZHR2PSJSCioaeg0AGmgABzBEQOJ1Zm15TggyZKR47Nz8K0FU9LRMjTEUtIysqU45PKVlWAbqpq0I3Tx9Q2NTC3KBSsbbe2wZIA&debug=false&forceAllTransforms=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&timeTravel=false&sourceType=module&lineWrap=true&presets=es2015%2Creact%2Cstage-2&prettier=false&targets=&version=7.4.3&externalPlugins=)是什么。点开链接，看右边es5代码，不用怕多，其它不用看，我们只搜索Object.create(参考资料1)，就会发现生成的_inherits函数同样是用Object.create做了prototype绑定。

## ES6类继承缺陷

从上面例证我们得出，ES6的类继承同样是基于prototype的。那么，一个'类'有prototype就是这个'类'可被继承的必要条件。JS里大部分‘类’，都满足这个条件，比如Array、Map、Element，但也有例外，比如ES6的Proxy。可在浏览器控制台输入Proxy.prototype，结果将是undefined。尝试继承Proxy也将报错，如下图所示:
![1](https://user-gold-cdn.xitu.io/2019/4/25/16a51f382da63de9?w=736&h=141&f=png&s=28173)

ps：js并非一切皆Object

## 解决方案

1. 用组合代替继承（可参考：[踩坑案例](https://github.com/zzz945/write-vue3-from-scratch/commit/3d4b919252a98a9f6898329016a17aa1d6d2da70)）
2. 高阶函数代替继承（提示：js函数可以返回class）

## 参考资料

1. [Object/create官方文档](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/create)
2. [can-i-extend-proxy-with-an-es2015-class](https://stackoverflow.com/questions/37714787/can-i-extend-proxy-with-an-es2015-class)


## 作者其它文章链接

[用vue3公开的思路从0实现最简化的vue](https://juejin.im/post/5cbc7a06f265da03587bfad0)
