# seajs
    1. 引入sea-debug.js
    2. 遵循CMD的开发模式
# 基本配置
    seajs.config({
        base:'', //默认为sea-debug.js当前的位置
        alias:{}, //当路径较长，直接设置别名
        paths:{}, //可设置目录,便于目录下文档的调用
        vars:{} //单独设置变量的路径,在使用中{变量名}就可以使用路径
    })
# require("路径")的解析
    1. 路径值为相对于sea-debug,直接在目录中一层层寻找
    2. 路径值为alias下的别名,先要设置base中的值,别名里的路径再相对于base路径
        *注意 : alias别名的值在使用时，需要单独使用
    3. 路径值为path的变量名,基于base路径设置,在使用时在其后面增加目标值路径
# require() seajs.use() require.async()的使用场景
        1. js模块编译后无define()的包裹下,而页面需要执行js模块,只能用seajs.use('字符串或变量'),seajs.use()解析路径是相对于当前页面,原理上只用来在页面中加载模块
        2. 编译后(fis),有define()函数包裹下
            *使用require()引入js模块,返回的是一个函数或执行结果。注意:在require('只能用字符串的形式')
            *require.async()主要是动态依赖,异步加载模块。例:当一个模块静态同时依赖两个不同的模块,就需要使用require.async('字符串或变量')
            *解析路径是相对于当前模块
# define自动编译或使用的格式
 define([],function(require,exports,module){
    module.exports={}
    exports.add=function(){} 
})
