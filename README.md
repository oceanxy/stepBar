#  stepBar
## 分布式进度导航条

点击查看 [demo](http://www.xieyangogo.cn/stepBar)

---

#### 注意事项：
* 发现bug或技术上的交流请发邮件到：[xyzsyx@163.com]()
* 本插件依赖jQuery库
* 本demo为本人早起所写，可能写法不适用于现在的框架页面，这里只是提供思路和效果
* 本插件根据 dom 结构自动初始化插件，未通过解析 json 数据的方式

-----
#### 使用方法：

1. 导入样式表
```HTML
    <link rel="stylesheet" type="text/css" href="./styles/index.css"></link>
```



2. 导入jquery库文件和autoTime.js
```HTML
	<script src="http://code.jquery.com/jquery-1.9.1.min.js"></script>
    <script src="./scripts/index.js"></script>
```



3. DOM
```HTML
    <div id='stepBar' class='ui-stepBar-wrap'>
      <div class='ui-stepBar'>
        <div class='ui-stepProcess'></div>
      </div>
      <div class='ui-stepInfo-wrap'>
        <table class='ui-stepLayout' border='0' cellpadding='0' cellspacing='0'>
          <tr>
            <td class='ui-stepInfo'>
              <a class='ui-stepSequence'>1</a>
              <p class='ui-stepName'>注册</p>
            </td>
            <td class='ui-stepInfo'>
              <a class='ui-stepSequence'>2</a>
              <p class='ui-stepName'>填写验证信息</p>
            </td>
            <td class='ui-stepInfo'>
              <a class='ui-stepSequence'>3</a>
              <p class='ui-stepName'>填写基本信息</p>
            </td>
            <td class='ui-stepInfo'>
              <a class='ui-stepSequence'>4</a>
              <p class='ui-stepName'>填写安全信息</p>
            </td>
            <td class='ui-stepInfo'>
              <a class='ui-stepSequence'>5</a>
              <p class='ui-stepName'>激活账户</p>
            </td>
            <td class='ui-stepInfo'>
              <a class='ui-stepSequence'>6</a>
              <p class='ui-stepName'>完成注册</p>
            </td>
          </tr>
        </table>
      </div>
    </div>
```

4. 调用 / 初始化
```javaScript
	stepBar.init('stepBar', {
      step: 0,
      change: true,
      animation: true
    })
```

---

 * 初始化调用方法  在js的onload事件或jq的$(document).ready()里面调用stepBar.init(id, option)即可。
 * 第一个参数为stepBar容器的id，必填，允许传入的值包括如下：
 *     jQuery对象
 *     javascript对象
 *     DOM元素（可转化为ID的字符串，如 “stepBar” || “#stepBar”） 纠错：误把jQuery对象的“#”写成“.”也同样能识别出来，但是必须保证此参数能转化成元素ID
 * 第二个参数为一个对象直接量，选填，包含如下的零个或多个
 *     step                string number   目标进度  默认为1（第一步），选填
 *     change              boolean    设置插件是否可被操作，选填  默认false
 *     animation           boolean    设置插件是否采用动画形式（前提stepBar.change为true），选填  默认false
 *     speed               number     动画速度（前提，change和animation为true） 选填   默认1000ms
 *     stepEasingForward   string     从当前步数往前过渡动画（前提，change和animation为true） 选填  默认 "easeOutExpo"  更多参数请参照 jquery.easing.js
 *     stepEasingBackward  string     从当前步数往后过渡动画（前提，change和animation为true） 选填  默认 "easeOutElastic"  更多参数请参照 jquery.easing.js
 *
 *     PS：不合法的参数将强行使用默认值
