
* [].forEach(function(目标元素，位置index，整个数组){})  
    *对于稀疏数组会跳过
    *通过return跳出循环
    *IE9+
* [].map(callback[,thisArg]) thisArg是执行callback的this 
    *函数中return的值,返回新的数组
* [].reduce(function(prev之前的结果[,初始化，目标元素，位置index，整个数组]){})