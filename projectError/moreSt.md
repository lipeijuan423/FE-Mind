- [] 两种标题的写法
## 记录问题
### 滚动条的重写

h1
====
* 找到写代码的插件 -- "pre标签"
* 放全部代码的标签
<pre>
    啊
    <span>我想是</span>
    () => {
        function () {
            // 我是注释
        }
    }
</pre>
```
    <p>我要高亮</p>
```
```js
    window.addEventListener('load', function() {
        console.log('window loaded');
    });
```
> 表示引用
>> 我表示嵌套
#
<br>[学习markdown]: (http://xianbai.me/learn-md/article/syntax/blockquotes.html)
* 行内式![GitHub](https://avatars2.githubusercontent.com/u/3265208?v=3&s=100 "GitHub,Social Coding")
* 参考式：![GitHub][github]

[github]: https://avatars2.githubusercontent.com/u/3265208?v=3&s=100 "GitHub,Social Coding"
* 这是用来 *演示* 的 _文本 _ <有空格则不会实现>
* ~~删除线~~

| left | center | right |
| :--- | :----: | ----: |
| aaaa | bbbbbb | ccccc |
| a    | b      | c     |

- [1] Eat
- [2] Code
  - [2.1] HTML
  - [x] CSS
  - [x] JavaScript
- [ ] Sleep