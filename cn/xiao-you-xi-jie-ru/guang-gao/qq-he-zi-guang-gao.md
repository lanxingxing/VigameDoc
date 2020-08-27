---
description: 目前只在QQ、Oppo小游戏平台有效
---

# 盒子广告

## dnsdk.openBoxAd\(object\)

快捷打开盒子广告。

### 参数

object

| 属性 | 类型 | 是否必填 | 说明 |
| :--- | :--- | :--- | :--- |
| adUnitId | string | 否 | 广告位标识，如果不填，会使用init传入的默认值。 |
| fail | function | 否 | 打开失败回调，平台sdk的onError会触发该方法 |
| success | function | 否 | 打开成功回调，平台sdk的onShow会触发该方法 |
| close | function | 否 | 关闭广告回调，平台sdk的onClose会触发该方法 |

### 返回值

BoxAd广告组件

### 示例代码：

```text
dnsdk.openBoxAd({
    fail: function (err) {
        console.log("盒子打开失败 : " + JSON.stringify(err));
    },
    success: function () {
        console.log("盒子打开成功 ");
    },
    close: function () {
        console.log("盒子关闭");
    }
});
```



