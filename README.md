# baidumap-lushu

百度地图路书扩展，在行进途中增加**特殊中断点**来修改路书的动作行为，详见[样例](./lushu-test.html)。

## 更新
> 2018-03-02更新，修正路书图标在水平方向移动时的位置偏离

## 代码说明
```javascript
// 1. 准备路线点
var route = [];
route.push(new BMap.Point(1, 2));
route.push(new BMap.Point(1, 2));
route.push(new BMap.Point(1, 2));

// 增加特殊中断点
route.push({
    // 路书动画的中断时长，以毫秒计时
    timeout : 2000,
    // 中断时的行为函数
    // 参数说明：
    //     map 路书所属的百度地图对象
    //     lushu 路书自身对象
    //     marker 路书的marker对象，可用于访问图标标记
    behavior : function(map, lushu, marker)
    {
        // 为路书的图标增加跳跃动画
        marker.setAnimation(BMAP_ANIMATION_BOUNCE);
    },
    // 中断超时结束时触发
    // 参数与behavior函数相同
    clear : function(map, lushu, marker)
    {
        // 将图标动画清除掉
        marker.setAnimation(null);
    }
});

var lushu = new BMapLib.LuShu(/*...*/);
lushu.start();

```
