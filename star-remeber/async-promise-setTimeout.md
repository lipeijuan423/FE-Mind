## 比较 async-await vs Promise vs setTimeout
  * 浏览器event-loop机制
  * 事件分类： 1. 同步和异步 
              2.宏任务和微任务（宏任务比微任务慢加入event-queue）
                * 宏任务： script setTimeout setInterval
                * 微任务： promise.then await
```js
  async function async1(){
      console.log('async1 start')
      await async2() // 得到一个Promise(resolve(undefined)),当同步执行完成，调用栈执行Promise,  resolve被放在下次微任务
      console.log('async1 end')
  }
  async function async2(){
      console.log('async2')
  }
  console.log('script start')
  setTimeout(function(){
      console.log('setTimeout') 
  },0)  
  async1();
  new Promise(function(resolve){
      console.log('promise1')
      resolve();
  }).then(function(){
      console.log('promise2')
  })
  console.log('script end')
```
## await 先执行右侧函数，再让出线程，等异步操作完成，再执行函数体内后面的语句