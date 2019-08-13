# 1.组件
    1.1父子组件的关系:组件A在它模板中使用了组件B 
    1.2父组件通过props向下传递数据给子组件,子组件通过evetns给父组件发送消息
    1.3单项数据流
        * 处理prop希望将它作为局部数据
            *定义一个局部变量,用prop的值初始化
        * 将prop处理成其他数据输出
            *定义一个计算属性,处理prop的值

            this.someObject = Object.assign({}, this.someObject, { a: 1, b: 2 })
             terminal 指令
             双向过滤器
# 2.
    el data methods template props params
    component filter extend 
    slot prop event