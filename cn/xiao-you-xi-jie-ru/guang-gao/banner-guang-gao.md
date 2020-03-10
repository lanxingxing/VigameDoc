# Banner广告

### dnsdk.openBanner\(\)

快捷打开banner，banner位于底部。如需自定义广告位置，请使用createBannerAd接口。

> 需确保sdk初始化时已传入广告配置，否则无效。

#### 返回值

BannerAd 广告组件

### dnsdk.destroyBanner\(\)

快捷销毁banner。

### dnsdk.createBannerAd\(object\)

创建 Banner 广告组件，每次调用该方法创建 banner 广告都会返回一个全新的实例。

> 提示 每个广告实例只会与一条固定的广告素材绑定。开发者如果想要展示另一条广告，需要创建一个新的 bannerAd 实例。

#### 参数

object

| 属性 | 类型 | 是否必填 | 说明 |
| :--- | :--- | :--- | :--- |
| adUnitId | string | 是 | banner广告位标识 |
| adIntervals | number | 否 | 广告自动刷新的间隔时间，单位为秒，参数值必须大于等于30（该参数不传入时 Banner 广告不会自动刷新） |
| style | object | 否 | banner广告组件的样式 |

**object.style 的属性**

| 属性 | 类型 | 是否必填 | 说明 |
| :--- | :--- | :--- | :--- |
| left | number | 是 | 定义 banner 左上角距离屏幕左边的距离 |
| top | number | 是 | 定义 banner 左上角距离屏幕上边的距离 |
| width | number | 是 | 定义 banner 展示的宽度 |
| heiht | number | 是 | 定义 banner 展示的高度 |

#### 返回值

BannerAd 广告组件

### BannerAd

#### BannerAd.style

| 属性 | 类型 | 说明 |
| :--- | :--- | :--- |
| left | number | 定义 banner 左上角距离屏幕左边的距离 |
| top | number | 定义 banner 左上角距离屏幕上边的距离 |
| width | number | 定义 banner 展示的宽度 |
| heiht | number | 定义 banner 展示的高度 |

#### BannerAd.show\(\)

显示banner广告

#### BannerAd.hide\(\)

隐藏 banner广告

#### BannerAd.destroy\(\)

销毁 banner 广告。

#### BannerAd.onResize\(function callback\)

监听 banner 广告尺寸变化事件。

代码示例：

```text
bannerAd.onResize(function(obj) {
  console.log('banner 宽度：' + obj.width + ', banner 高度：' + obj.height)
})
```

#### BannerAd.offResize\(function callback\)

取消监听 banner 广告尺寸变化事件

#### BannerAd.onLoad\(function callback\)

监听 banner 广告加载事件。 代码示例：

```text
bannerAd.onLoad(function() {
  console.log('banner 广告加载成功')
})
```

#### BannerAd.offLoad\(function callback\)

取消监听 banner 广告加载事件

#### BannerAd.onError\(function callback\)

监听 banner 广告错误事件。  
代码示例：

```text
bannerAd.onError(function(err) {
  console.log(err)
})
```

#### BannerAd.offError\(function callback\)

取消监听 banner 广告错误事件。

