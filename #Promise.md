# Promise
```js
function promise(resolve, reject){
  if(/*异步成功*/){
    resolve()
  } else {
    reject(error)
  }
}
promise().then(function (value) {})
```
三个状态: Pending Fulfilled Rejected
# Iterator for...of循环
# generator函数 yield
```js
function* helloworld(){ // 没有规定*的位置
  yield 'hello'
  yield 'world'
  return 'ending'
}
let hw = helloworld()
hw.next() // {value: '', done: false/true}
```
# trunk函数 co模块
# async await
```js
async function f(){
  return await 123;
}
f().then(v => console.log(v))
```
# 异步generator 同 async
```js
// 异步generator函数执行器
async function takeAsync(asyncIterable, count=Infinity){
const result = []
const iterator = asyncIterable[Symbol.asyncIterator]();
while(result.length < count){
const {value, done} = await iterator.next()
if(done) break;
result.push(value)
}
return result
}
// 使用实例
async function f(){
async function* gen(){
yield 'a';
yield 'b';
yield 'c';
}
return await takeAsync(gen())
}
f().then(function (result){
console.log(result)
})
```
## 遍历接口
Symbol.asyncIterator  for await...of