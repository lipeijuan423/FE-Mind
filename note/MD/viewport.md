# 基本的名词
    1. 物理屏幕(设备像素) : 移动设备的尺寸大小 screen.width
   <!--  2. css像素(设备独立像素dips) : 抽象单位，在不同设备不同环境会相对应不同的物理像素 -->
    3. css像素(设备独立像素dips 逻辑像素) : 实际物理像素 / 倍率，两个屏幕只要逻辑像素相同，那么显示的效果也相同
    4. device-width 
    5. 视口 : 浏览器窗口，所有的css百分比推算的根源
    6. 布局视口(layout viewport) : 整个页面布局的大小----document.documentElement.clientWidth
    7. 视觉视口(vistual viewport) : 用户正在看到的网页的区域，是浏览器默认的宽度,大小是屏幕中CSS像素的数量。----window.innerWidth/Height
    8. 理想视口(ideal viewport) :手机厂商定义好，开发者使用。就是把布局视口的宽度改为屏幕的宽度 ----screen.width/height
        *`<meta name="viewport" content="width=device-width">`

# 对width="device-width"的理解
    1. 为什么要有device-width
        *为了页面在不同的移动设备上显示相同的效果
    2. 值的取决条件(计算的结果就是逻辑像素)
        *移动设备的物理像素
        *手机的倍率
    *注意 : 如果不使用device-width，h5页面在iOS和android的浏览器默认值。visual viewport会默认为980px
# 对initial-scale的理解
    1. 为什么要使用
        *兼容性,大多数浏览器支持两个属性
    2. 对页面做了什么事
        *根据ideal viewport生成visual viewport宽度,在讲visual viewport的宽度设为layout viewport的宽度
        *缩放比例=ideal viewport的宽度(device-width) / vistual viewport的宽度(浏览器默认值)
    3. 为什么使用content="width=device-width"和initial-scale=1的效果一样
        *initial-scale是基于ideal viewport计算的缩放比例
    4. 注意在iphone和ipad上,无论给viewport的值设置为多少，在没设置initial-scale的情况下，浏览器自动设置缩放比,达到不出现横条
# 对设备像素比 devicePixelRatio 的理解
    1. 条件 : 缩放程度为100%
    2. 计算公式 : window.devicePixelRatio=物理像素 / css像素 
    3. 目的 : 
        *页面在不同的设备显示相同的效果
        *让图片等在不同的设备上显示更好的效果
# 单位
    1. 百分比
    2. rem
        *font-size
        *计算方式 : 布局图的宽度 / 设计图的宽度 = 布局图的rem值 / 设计图的rem

# 例子
    1. 定义一个border为1px的线
        *物理屏幕375px和750px,倍率1x和2x 
        *css像素375px
        *在倍率为2x的情况,将border:0.5px ..;
    2. 字体大小的设置
        *一个750px的设计图，将设计图中字体为28px放入device-width=375px的页面中，font-size:14px;
    3. 图片对应的放置问题(宁愿裁剪,也不要放大图片)
        *在无倍率的，相应的物理像素点对应css像素点。在2x的设备中，1个css像素点对应2个物理像素。
        *有一张10px 10px的放入对应设备浏览器中，无倍率的合适，但是2x的则需要20 px 20px的图片，用来将css像素对应设备的物理像素
# 补充 理解设备的宽高
    1. document.documentElement.offsetWidth/Height显示<html>的大小
    2. screen.width/height是物理屏幕的完整大小,是显示器的特征,不会因为缩放而改变
    3. window.innerWidth/Height 包含滚动条的浏览器完整尺寸,供css布局使用
    4. window.pageX/YOffset定义了页面相对于窗口原点水平,垂直位移。可用来计算用户滚动了多少距离
    5. 视窗viewport主要是用来控制`<html>`元素,viewport等于浏览器窗口
    6. document.docuemntElement.clientWidth/Height是viewport的尺寸,(对角线),不包含滚动条。
    7. IE不支持window.innerWidth/Height.
    8. documentElement.offsetWidth/Height(具有兼用性)表示`<html>`,IE用来表示viewport的尺寸
    9. pageX/Y `<html>`的原点到事件 event.pageX/Y.IE使用document. scrollLeft/Top
    10. clientX/Y viewport
    11. screenX/Y 用户显示器
    12. layout viewport的尺寸是document.documentElement.clientX/Y
    13. virtual viewport的尺寸是widow,innerWidth/Height.IE使用document. documentElement.offsetWidh/Height


# 在不同的情况下,相对应的设置
    ## 在视觉稿基于iphone5 (dpr=2)为750px,某个元素字体是28px
        1. 设置width=device-width
|dpr|物理像素|device-width|inital-scale|css像素|font-size|
| --|--------|------------|------------|-------|---------|
|  3|  1136px|  375px     |      1     | 375px |  14px   |
|  2|  750px |  375px     |      1     | 375px |  14px   |
|  1|  375px |  375px     |      1     | 375px |  14px   |
|  1|  750px |  750px     |      1     | 750px |  14px   |
        2. 不设置width=width-decive,设置inital-scale  (flexible框架)-->目的:为了让物理像素和css像素相同,在不同的移动设备下,显示相同的效果
  dpr |  物理像素  | device-width  |  inital-scale  |  css像素  | font-size  
------|------------|---------------|----------------|-----------|----------
  3   |  1136px    |  375px        |       0.33     |  1136px   |  42px     
  2   |   750px    |  375px        |       0.5      |   750px   |  28px     
  1   |   375px    |  375px        |       1        |   375px   |  14px     
  1   |   750px    |  750px        |       1        |   750px   |  14px     


