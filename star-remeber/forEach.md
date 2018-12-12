### forEach不能使用 break return 等方式退出循环，只能抛出一个错误时退出
```js
  try{
    let arr = [1, 2, 3, 4, 5]
    arr.forEach(item => {
      if(item === 2){
        throw('finish')
      }
    })
  }catch(err){
    if(err != 'finish') console.log(error)
  }
```
### 为什么不能使用break return退出循环，内部机制
```js
  var arr = [1,2,3,4], len = 0
  for(var index = 0; len < arr.length; i++){
    const res = (function(){
      console.log(arr[index])
      // 使用return只能退出res中函数，不能退出循环
    })(arr[index])
  }
```
### 怎么办
for ... in (不推荐)
every, some
还有个奇怪的解决方法 
```js
  var arr = [1,2,3]
  arr.forEach((item, index) => {
    if(item === 2){
      // arr.splice改变原数组的引用，可以退出循环， 
      /* 
        * [1].concat([1,2,3].splice(1, 2)) 
        * [1].concat([2,3])
       */
      arr=arr.concat(arr.splice(index, arr.length-index))
    }
  })
```