1.display:none visibility:hidden opacity:0 type:hidden的区别

2.$()理解DOM对象和jQuery对象(通常是以$为前缀)

3.document.getElementById('')和document.querySelectorAll("选择器")后者是一个数组 list[i].style.border="1px solid red"
$("选择器").css("border","1px solid red")
$("选择器").css({borderTopLeftRadius:4驼峰式})
记住:.btn-group>li:not(:last-child){}//删除除最后一个li之外
    .btn-group>li:first-child与.btn-group>li:first一样
    :not(.one) div:even偶数 div:odd奇数 div:eq() div:lt() div:gt()
    css:table>tbody>tr:nth-child(odd){background:#afa;}
    jquery:$('table>tbody>tr:even').css('background','#afa')
    $("body div") $("body>div") $(".one+div"):class为one的下一个兄弟 $("#two~div"):id为two的元素后面的所有兄弟
    $('#two,span')所有span和id为two的元素
4.$('.dropdown').mouseover(function(){
	$('.dropdown>.dropdown-meun').addClass("in");
})
5.jQuery中的获取内容
    $('选择器').html() --> txt=document.createElement('p'); txt.innerHTML=''
    $('选择器').text()
    $('选择器').val()
    (
        * 设置内容
        * 回调函数function(i,origText){}//i是当前元素的下表 origText是原始值
    )
6.属性
    $('选择器').attr() -->elem.getAttribute();
    (
        * 一个参数 获取属性值
        * 两个参数 修改属性的值
            *值 
            *回调函数function(i,origValue){}
        * {同时修改多个值}
        
    )
  $('选择器').prop() [一般用于DOM元素的动态状态]
7.操作DOM
    添加元素 DOM  
        接受无限量的元素 参数
        1.$('选择器').append('');//被选中元素的结尾
        2.$('选择器').prepend('');//被选中元素的开头
        3.$('选择器').before('');//
        4.$('选择器').after('');//
        区别:
        append() & prepend()实在元素内插入内容（该内容变成该元素的子元素或节点），
        after() & before()是在元素的外面插入内容（其内容变成元素的兄弟节点）。
    删除元素 DOM
        1.$('选择器').remove();//删除被选中元素及子元素
            * $('选择器').remove("元素");//删除有 元素 的选择器
        2.$('选择器').empty();//删除被选元素的子元素
9.操作CSS
    添加CSS  
        * $('选择器').addClass();//向不同的元素添加Class属性 可以选取多个元素
    删除CSS
        * $('选择器').removeClass();//在不同的元素中删除指定的Class属性
    添加和删除自动切换
        * $('选择器').toggleClass();//对被选中元素进行添加和删除类的切换
    设置或返回被选中元素的一个或多个样式 属性
        * $('选择器').css('属性名')  一个参数 返回指定CSS的值
        * $('选择器').css('属性名','属性值') ({多个})
10.遍历
    祖先
        * $('选择器').parent() //被选元素的直接父元素
        * $('选择器').parents() //被选元素的所有祖先元素
            *参数可用作选择 固定的父级元素
        * $('选择器').parentsUntil('选择元素') //选择两个元素之间的祖先元素
    后代
        可根据后面的参数元素，选择
        * $('选择器').children() //返回元素的所有直接子元素 
        * $('选择器').find() //返回元素的所有后代字元素
    同胞
        * $('选择器').siblings(); //所有同胞元素
        * $('选择器').next(); //被选元素的下一个 只返回一个元素
        * $('选择器').nextAll(); //被选元素的后面同胞元素
        * $('选择器').nextUntil(); //两个参数之间的所有同胞元素
        * prev() prevAll() prevUntil()
    过滤
        * $('选择器1 选择器2').first(); //首个选择器1的首个选择器2
        * .last()
        * .eq()
        * .filter()
        * .not()
11.Ajax方法的封装
    load() //从服务器加载数据，并返回数据放入被选元素中
        $("button").click(function(){
          $("#div1").load("demo_test.txt",function(responseTxt,statusTxt,xhr){
            if(statusTxt=="success")
              alert("外部内容加载成功!");
            if(statusTxt=="error")
              alert("Error: "+xhr.status+": "+xhr.statusText);
          });
        });
        responseTxt - 包含调用成功时的结果内容
        statusTXT - 包含调用的状态
        xhr - 包含 XMLHttpRequest 对象