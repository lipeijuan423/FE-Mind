## 深拷贝和浅拷贝
* 概念：当拷贝对象有引用类型时区分
* 浅拷贝： 对象不同，数据类型不同，引用类型相同
* 深拷贝： 对象不同，数据类型不同，引用类型不同
```js
  function shallowCopy(obj){
    let target = Array.isArray(obj) ? [] : {};
    for(let key in obj){
      if(!obj.hasOwnProperty(obj[key])){
        target[key] = obj[key]
      }
    }
    // 如果是数组
    target = obj.slice()
  }
  function deepCopy(obj){
    let target = Array.isArray(obj) ? [] : {};
    for(let key in obj){
      if(typeof obj[key] === 'object'){
        deepCopy(obj[key])
      } else {
        target[key] = obj[key]
      }
    }
    // 如果不拷贝函数和原型成员
    target = JSON.stringify(JSON.parse(obj))
  }
```