# 插屏广告

> 目前QQ和字节跳动小游戏暂不支持插屏广告

### dnsdk.openInterstitial\(\)

快捷打开插屏。

> 需确保sdk初始化时已传入广告配置，否则无效。

#### 返回值

InterstitialAd 广告组件

### dnsdk.destroyInterstitial\(\)

快捷销毁插屏。

### dnsdk.createInterstitialAd\(object\)

创建插屏广告组件，每次调用该方法创建插屏广告都会返回一个全新的实例。

> 插屏广告实例不能复用，每次需要重新加载时要重新create

#### 参数

object

| 属性 | 类型 | 是否必填 | 说明 |
| :--- | :--- | :--- | :--- |
| adUnitId | string | 是 | 插屏广告位标识 |

#### 返回值

InterstitialAd 广告组件

### InterstitialAd

#### InterstitialAd.show\(\)

显示插屏广告。

#### InterstitialAd.load\(\)

加载插屏广告。

> 插屏广告组件是自动拉取广告并进行更新的，即在调用createInterstitialAd之后会立马触发一次load。在组件创建后会拉取一次广告，用户关闭广告后会去拉取下一条广告，即在用户关闭广告之后，会立马触发一次load。

#### InterstitialAd.onClose\(function callback\)

监听插屏广告关闭事件。

#### InterstitialAd.offClose\(function callback\)

取消监听插屏广告关闭事件

#### InterstitialAd.onLoad\(function callback\)

监听插屏广告加载事件

#### InterstitialAd.offLoad\(function callback\)

取消监听插屏广告加载事件

#### InterstitialAd.onError\(function callback\)

监听插屏错误事件。

**Object res**

| 属性 | 类型 | 说明 |
| :--- | :--- | :--- |
| errMsg | string | 错误信息 |
| errCode | number | 错误码 |

> 错误原因需参照具体平台的文档

#### InterstitialAd.offError\(function callback\)

取消监听插屏错误事件

#### InterstitialAd.destroy\(\)

销毁插屏广告实例

