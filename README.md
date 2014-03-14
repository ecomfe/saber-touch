saber-touch
===

**目前该模块处于非稳定的开发状态，请勿在产品环境中使用！**

`saber-touch` 是 `saber` 框架默认的手势事件库。

API
---

### .config( config )

```javascript
var touch = require('saber-touch');

// 对事件库进行全局配置
touch.config({
    tap: true,              // tap类事件开关，默认为true
    doubleTap: true,        // doubleTap事件开关，默认为true
    hold: true,             // hold事件开关，默认为true
    holdTime: 650,          // hold时间长度
    swipe: true,            // swipe事件开关
    swipeTime: 300,         // 触发swipe事件的最大时长
    swipeMinDistance: 18,   // swipe移动最小距离
    swipeFactor: 5,         // 加速因子, 值越大变化速率越快
    drag: true,             // drag事件开关
    pinch: true             // pinch类事件开关
});
```

### .on(delegateElement, types, selector, callback )

绑定事件代理。

**参数：**

+ `delegateElement` `{HTMLElement|string}` 事件代理元素或选择器
+ `types` `{string}` 手势事件的类型，可接受多个事件以空格分开，支持原生事件的透传。目前支持的具体事件类型，详见 *手势事件类型*。
+ `selector` `{string}` 代理子元素选择器
+ `callback` `{Function}` 事件处理函数，如需了解手势库支持的新属性，详见 *事件对象*。

### .on( element, types, callback )

绑定事件。

**参数：**

+ `element` `{HTMLElement|string}` 事件绑定元素或选择器
+ `types` `{string}` 事件的类型, 可接受多个事件以空格分开，支持原生事件的透传
+ `callback` `{Function}` 事件处理函数

### .off( delegateElement, types, selector, callback )

解除某元素上的事件代理。

**参数：**

+ `delegateElement` `{HTMLElement|string}` 元素对象或选择器
+ `types` `{string}` 事件的类型
+ `selector` `{string}` 代理子元素选择器
+ `callback` `{Function}` 事件处理函数，移除函数与绑定函数必须为同一引用

### .off( element, types, callback )

解除事件绑定。

**参数：**

+ `element` `{HTMLElement|string}` 元素对象或选择器
+ `types` `{string}` 事件的类型
+ `callback` `{Function}` 事件处理函数，移除函数与绑定函数必须为同一引用

### .trigger( element, type [, object] )

触发某个元素上的事件。

**参数：**

+ `element` `{HTMLElement|string}` 元素对象或选择器
+ `type` `{string}` 事件的类型
+ `object` `{Object}` `(可选)` 传递的数据对象

手势事件类型
---

### 缩放

+ `pinchstart` 缩放手势起点
+ `pinchend` 缩放手势终点
+ `pinch` 缩放手势
+ `pinchin` 收缩
+ `pinchout` 放大

### 旋转

+ `rotateleft` 向左旋转
+ `rotateright` 向右旋转
+ `rotate` 旋转

### 滑动

+ `swipestart` 滑动手势起点
+ `swiping` 滑动中
+ `swipeend` 滑动手势终点
+ `swipeleft` 向左滑动
+ `swiperight` 向右滑动
+ `swipeup` 向上滑动
+ `swipedown` 向下滑动
+ `swipe` 滑动

### 拖动

+ `dragstart` 拖动开始
+ `drag` 拖动
+ `dragend` 拖动结束

### 长按

+ `hold` 长按屏幕

### 轻击

+ `tap` 单击屏幕
+ `doubletap` 双击屏幕

事件对象
---

事件处理函数的第一个参数为事件对象。

以下是除了原生属性之外，为手势新增的属性：

+ `originEvent` 触发某事件的原生对象
+ `type` 事件的名称
+ `rotation` 旋转角度
+ `scale` 缩放比例
+ `direction` 操作的方向属性
+ `fingersCount` 操作的手势数量
+ `position` 相关位置信息, 不同的操作产生不同的位置信息
+ `distance` swipe类两点之间的位移
+ `distanceX | x` 手势事件x方向的位移值, 向左移动时为负数
+ `distanceY | y` 手势事件y方向的位移值, 向上移动时为负数
+ `angle` rotate事件触发时旋转的角度
+ `duration` touchstart 与 touchend之间的时间戳
+ `factor` swipe事件加速度因子
+ `startRotate` 启动单指旋转方法，在某个元素的touchstart触发时调用

感谢
---

感谢 [**Clouda Team**](http://cloudajs.org) 开发的 [`touchjs`](http://code.baidu.com) 手势事件库。
`saber-touch` 是在其基础上演化的一个分支，没有 `touchjs` 就没有现在的 `saber-touch`。
