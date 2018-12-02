* for in 遍历对象的属性  只要实例化对象 --> hasOwnProperty()
* for of 主要获取对象的属性值
    `for(var j of obj){console.log(j)}`  j是属性值
* Object.keys(必须是对象) 对象自身的属性，不包括原型的属性
* Object.keys(对象).forEach()
`
    var colors = ['red', 'green', 'blue'];
    colors.foo = 'hello';

    Object.keys(colors).forEach(function(elem, index) {
      console.log(colors[elem]); // red green blue hello
      console.log(colors[index]); // red green blue undefined
    });

    colors.forEach(function(elem, index) {
    console.log(elem); // red green blue
    console.log(index); // 0 1 2
})`