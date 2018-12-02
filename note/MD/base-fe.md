# 1.xml和json的区别
     Extensible Markup Language xml
     JavaScript Object Notation Json
     同：可读性 可扩展性
     异：
        1.xml比json难于编写
        2.服务器端和客户端需要花费大量代码解析xml;json易于解析，客户端通过eval()读取，服务器端可以利用php的对象，数组直接生成json格式
        3.xml客户端不同浏览器之间解析xml的方式不一致，Json能直接为服务器代码使用


        4.解码难度，xml解析会考虑节点
        5.json可以更好的数据交互

        json构建两种结构：key/value
        xml:dom+sax 
        轻/重量级的区别：
            json只提供整体解析方案，使用与解析较少数据
            xml对大规模数据的逐步解析，随时可以终止，适用于大量数据的解析处理
# 2.html5的新特性
   主要是语义化标签，音频(video)，视频(audio)，绘画（canvas,svg），拖动api，表单控件，，存储(sessionStorage,localStorage)，多任务，webworkder,websockt
# 3.实现浏览器内多个标签之间的通信
    localStorage cookies 本地存储
# 4.作用域链 
    作用域简单来说是指变量与函数的可访问范围，js中作用域分为全局 作用域和局部作用域。
    因为js中，一切都是对象，函数有一个内部属性[scope],而作用域链是该内部函数被创建作用域中对象的集合，它决定了哪些数据能被函数访问。当一个函数创建后，它的作用域链会被创建此函数的作用域中可访问的数据对象填充。
    执行环境中的变量和函数的总称叫做变量对象，但不能反映代码的动态性，区别普通变量对象，创造了活动对象
    活动对象：
        当打开浏览器时已经存在一个全局的执行环境，这个全局执行环境属于浏览器，js里浏览器被称为window对象，会储存全局的变量和函数。调用函数时，又会创建一个执行环境B,是在运行和执行代码的时候才存在。（根据函数的scope属性将变量对象放入B环境中）
        所以：变量对象包括活动对象，活动对象就是作用域链上正在被执行和引用的变量对象（执行，运行，激活）。
        arguments对象：保存函数中参数的值
    变量对象：执行环境中包含所有变量和函数的对象
# 5.原型链
    原型链的存在主要是继承
    _proto_:在创建对象时，内置属性_proto_用于指向它的函数对象的prototype,原型对象也有proto，在不断指向中，形成原型链
    new的执行有：
        var o={} //创建一个实例对像
        o._proto_=F.prototype //实例对象的_proto_属性指向函数的原型对象
        F.call(o) //
# 闭包
    经典闭包面试题
    问题:大概是在闭包中，i值会是最后一个
    解决：
    1.在内部函数外直接(i)
    2.使用this.i    ()再立即执行
    3.let es6
    4.由Function 或 New Function方法（
    使用了 new 即 Function 函数充当构造器,由 JS 解析器生产一个新的对象,构造器内的 this 指向该新对象;
            不实用 new 即 Function 函数依旧是函数,由函数内部自己生产一个实例返回.）
    arguments.callee -->参数对象所属函数
    1.闭包就是能够读取其他函数内部变量的函数，本质上，闭包是将函数内部和函数外部连接起来的一座桥梁
    注意:闭包中函数的变量会被保存在内存，内存消耗大，滥用闭包会造成网页性能问题，在IE中可能导致内存泄露。将不用的局部变量全部删除
    最大的用处：1.可以读取函数内部的变量
                2.将这些变量的值始终保存在内存中
一种函数嵌套
# 6.继承
    1.构造继承
        核心：使用父级的构造函数来增强子类型实例，等于复制父类的实例属性给子类（没用原型）
        解决：子类实例共享父类引用属性问题
                创建子类实例可以向父类传递参数
        缺点：
            实例并不是父类的实例，只是子类的实例
            只能继承父类的实例属性和方法，不能继承原型属性和方法
            无法实现函数复用，每个子类都有父类实例函数的副本，影响性能
    2.原型继承
        核心：将父类的实例作为子类的原型
        缺点：
            来自原型对象的引用属性是所有实例共享的
            创建子类型无法向父级构造函数传参
    3.实例继承
        核心：为父类实例添加新特性，作为子类实例返回
        缺点：实例是父类的实例，不是子类的实例cat instancef Cat //false
    4.拷贝继承
        效率低占用内存高
    5.组合继承
        核心：调用父类构造函数，继承父类的属性保留传参，通过将父类实例作为子类型原型，实现函数复用
        function Cat(name){
          Animal.call(this);
          this.name = name || 'Tom';
        }
        Cat.prototype = new Animal();
        // Test Code
        var cat = new Cat();
        console.log(cat.name);
        console.log(cat.sleep());
        console.log(cat instanceof Animal); // true
        console.log(cat instanceof Cat); // true
        缺点：调用两次父类构造函数，生成两份实例，多消耗内存
    6.寄生组合继承
        核心：通过寄生方式，砍掉父类的实例属性，这样，在调用两次父类的构造的时候，就不会初始化两次实例方法/属性，避免的组合继承的缺点
        function Cat(name){
          Animal.call(this);
          this.name = name || 'Tom';
        }
        (function(){
          // 创建一个没有实例方法的类
          var Super = function(){};
          Super.prototype = Animal.prototype;
          //将实例作为子类的原型
          Cat.prototype = new Super();
        })();

# 7.ajax的get和post的区别
    1.get请求会将参数跟在url后，post请求时作为http实体内容发送
    2.get请求的数据会被浏览器缓存，严重的安全问题
    3.服务器使用Request.QueryString获取参数（get）,Request.Form获取参数（post）

    若符合下列任一情况，则用POST方法：
    * 请求的结果有持续性的副作用，例如，数据库内添加新的数据行。
    - 若使用GET方法，则表单上收集的数据可能让URL过长。
    - 要传送的数据不是采用7位的ASCII编码。

    若符合下列任一情况，则用GET方法：
    - 请求是为了查找资源，HTML表单数据仅用来帮助搜索。
    - 请求结果无持续性的副作用。
    - 收集的``数据及HTML表单内的输入字段名称的总长不超过1024个字符。
    `
# 8.common.js和amd/cmd的区别
    CommonJS是主要为了JS在后端的表现制定的，他是不适合前端的，AMD(异步模块定义)出现了，它就主要为前端JS的表现制定规范。

    1.commonJs -- 同步加载
        NodeJs，webpack是commonJs的形式书写
        CommonJS定义的模块分为:{模块引用(require)} {模块定义(exports)} {模块标识(module)}。
        require()用来引入外部模块；exports对象用于导出当前模块的方法或变量，唯一的导出口；module对象就代表模块本身。
        （不适用于浏览器环境）
    2.AMD -- 异步加载 异步模块定义 
        预执行模块
        requireJs--require([module],callback)
        1.浏览器端的模块加载器，也想成为node、rhino等环境的模块加载器
        2.让第三方类库修改自身
        3.不重视调试
        4.采用源码中预留接口的形式，插件类型单一
    3.CMD -- 通用模块定义
        懒执行
        seajs
        1.专注于web浏览器端，node可扩展
        2.自主封装
        3.重视调试
        4.通用事件机制，插件类型丰富
# 9.window.load window.onload $(document).ready()区别
 window.onload 
    1.必须等到页面包括所有图片的所有元素加载完毕才能执行
    2.不能同时编写多个，只会执行一个
    window.onload=function(){}
 $(document).ready()
    1.DOM结构绘制完毕后就执行，不必等到加载完毕
    2.可以同时编写多个，并都可以执行
    $(document).ready(function(){})-->可以简写
    $(function(){})
    Jquery:$(window).load(function(){})==window.onload=function(){}
    load()方法是如果绑定到window对象，则会在所有内容（包括窗口，框架，对象，图像等），加载完毕后触发，如果处理函数绑定在元素上，则会在元素内容加载完毕后触发


