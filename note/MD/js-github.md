# https://github.com/mqyqingfeng/Blog/
# js的词法作用域：采用静态作用域
## 变量提升 函数提升
## 可执行代码 : 全局代码 函数代码 eval代码 
## 执行上下文 : 当执行的到一个函数时的准备工作     上下文栈
## 全局上下文 : 全局对象  顶层声明的所有变量将成为全局对象的属性
## 函数上下文 : 活动对象AO 表示 变量对象 。
    * 变量对象 : 在引擎上实现 不能再js环境中访问
    * 活动对象 : 执行上下文的变量对象被激活 活动对象的各个属性被访问
注意 : 变量声明不会改变 已经声明的相同的形式参数或函数

闭包 : 
    var data = [];

    for (var i = 0; i < 3; i++) {
      data[i] = function () {
        console.log(i);
      };
    }
    VS
    data[0]();
    data[1]();
    data[2]();

    var data = [];

    for (var i = 0; i < 3; i++) {
      data[i] = (function (i) {
            return function(){
                console.log(i);
            }
      })(i);
    }

    data[0]();
    data[1]();
    data[2]();
VS
var data = [];

for (var i = 0; i < 3; i++) {
    (data[i] = function () {
       console.log(arguments.callee.i) 
    }).i = i;
}

data[0]();
data[1]();
data[2]();

    ## 值传递和引用传递 
       参数如果是基本类型是按值传递，如果是引用类型 就是 按共享传递 是传递对象的引用的副本  但是因为拷贝副本也是一种值的拷贝，所以在高程中也直接认为是按值传递了

    ## 原来函数名.call(能实现功能的函数名[,参数])
    ## 利用bind返回的函数作为构造函数时,bind指定的this会失效。再new 
        *   var bindFoo = bar.bind(foo, 'daisy');//这时候的foo失效
            var obj = new bindFoo('18');
    ## arguments 由实参传入时会共享,没有传入不会共享，
    ## 构造函数 
        * new关键字调用
        * 函数内部this,默认返回this->新的实例对象.是五种简单的数据类型,仍然返回this.如果是return Object就返回值
