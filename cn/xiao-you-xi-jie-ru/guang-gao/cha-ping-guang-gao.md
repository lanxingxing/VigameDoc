# 插屏广告

> 目前QQ和字节跳动小游戏暂不支持插屏广告

## dnsdk.openInterstitial\(object\)

快捷打开插屏。

### 参数

object

| 属性 | 类型 | 是否必填 | 说明 |
| :--- | :--- | :--- | :--- |
| adUnitId | string | 否 | 插屏广告位标识，如果不填，会使用init传入的默认值。 |
| fail | function | 否 | 打开失败回调，平台sdk的onError会触发该方法 |
| success | function | 否 | 打开成功回调，平台sdk的onShow会触发该方法 |
| close | function | 否 | 关闭广告回调，平台sdk的onClose会触发该方法 |

### 返回值

InterstitialAd 广告组件

### 示例代码：

```text
dnsdk.openInterstitial({
    fail: function (err) {
        console.log("打开插屏失败 : " + JSON.stringify(err));
    },
    success: function () {
        console.log("打开插屏成功 ");
    },
    close: function () {
        console.log("插屏关闭");
    }
});
```

## dnsdk.destroyInterstitial\(\)

快捷销毁插屏。

