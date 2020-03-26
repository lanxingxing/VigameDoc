# Banner广告

### dnsdk.openBanner\(object\)

快捷打开banner，banner位于底部。如需自定义广告位置，请使用createBannerAd接口。

#### 参数

object

| 属性 | 类型 | 是否必填 | 说明 |
| :--- | :--- | :--- | :--- |
| adUnitId | string | 否 | banner广告位标识。如果不填，会使用init传入的默认值。 |
| adIntervals | number | 否 | 广告自动刷新的间隔时间，单位为秒，参数值必须大于等于30（该参数不传入时 Banner 广告默认30秒刷新一次） |
| style | object | 否 | banner广告组件的样式 |
| fail | function | 否 | 打开失败回调，平台sdk的onError会触发该方法 |
| success | function | 否 | 打开成功回调，平台sdk的onShow会触发该方法 |

**object.style 的属性**

| 属性 | 类型 | 是否必填 | 说明 |
| :--- | :--- | :--- | :--- |
| left | number | 是 | 定义 banner 左上角距离屏幕左边的距离 |
| top | number | 是 | 定义 banner 左上角距离屏幕上边的距离 |
| width | number | 是 | 定义 banner 展示的宽度 |
| heiht | number | 是 | 定义 banner 展示的高度 |

#### 返回值

BannerAd 广告组件

#### 示例代码：

```
        dnsdk.openBanner({
            fail:function (err) {
                console.log("打开banner失败 : " + JSON.stringify(err));
            },
            success :function () {
                console.log("打开banner成功 ");
            }
        });
```



### dnsdk.destroyBanner\(\)

快捷销毁banner。