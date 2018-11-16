# 简单的滚动
* 1.使用于现代浏览器
 ```
    window.scrollTo({ "behavior": "smooth", "top": body.offsetHeight - footer.offsetHeight });
 ```
* 2. 循环定时器setInterval
 ```
  let Timer = setInterval(() => {
      let body = document.documentElement
      let bottom = body.offsetHeight - body.scrollTop
      let speed = bottom / 10
      if(body.offsetHeight !== footer.offsetTop){
          body.scrollTop+=speed
      }
      if(body.offsetHeight > footer.offsetTop){
          clearInterval(Timer)
      }
  }, 30)
 ```
 * 3. 一次性定时器 setTimeOut 兼容ie9
 ```
     var body = (document.compatMode && document.compatMode === 'CSS1Compat') ? document.documentElement : document.body;
        var partner = document.getElementsByClassName('become-partner')[0];
        function TimerFun() {
            let bodyHeight
            if (!!window.ActiveXObject || 'ActiveXObject' in window) {
                bodyHeight = body.scrollHeight
            } else {
                bodyHeight = body.offsetHeight
            }
            let bottom = bodyHeight - body.scrollTop
            let speed = bottom / 10
            if (body.scrollTop < partner.offsetTop) {
                body.scrollTop += speed
                setTimeout(() => {
                    TimerFun()
                }, 30)
            }
        }
        TimerFun()
 ```
* 4. 指定位置 
``` function scrollTo(element){
    var body = (document.compatMode && document.compatMode === 'CSS1Compat') ? document.documentElement : document.body;
    function TimerFun() {
        let bodyHeight
        if (!!window.ActiveXObject || 'ActiveXObject' in window) {
            bodyHeight = body.scrollHeight
        } else {
            bodyHeight = body.offsetHeight
        }
        let bottom = bodyHeight - body.scrollTop
        let speed = bottom / 10
        if (body.scrollTop < elements.offsetTop) {
            body.scrollTop += speed
            setTimeout(() => {
                TimerFun()
            }, 30)
        }
    }
    TimerFun()
}
```