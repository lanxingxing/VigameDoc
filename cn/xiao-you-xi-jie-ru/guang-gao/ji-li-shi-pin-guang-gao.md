# 激励视频广告

### dnsdk.openRewardedVideo\(object)

快捷打开视频。

#### 参数

object

| 属性     | 类型     | 是否必填 | 说明                                                         |
| :------- | :------- | :------- | :----------------------------------------------------------- |
| adUnitId | string   | 否       | banner广告位标识。如果不填，会使用init传入的默认值           |
| fail     | function | 否       | 打开失败回调，平台sdk的onError会触发该方法                   |
| success  | function | 否       | 打开成功回调，平台sdk的onShow会触发该方法                    |
| close    | function | 否       | 关闭广告回调，平台sdk的onClose会触发该方法，通常在该方法内根据isEnded参数进行道具下发判断 |

#### 返回值

RewardedVideoAd 广告组件

#### 示例代码：

```
        dnsdk.openRewardedVideo({
            fail:function (err) {
                console.log("打开视频失败 : " + JSON.stringify(err));
            },
            success :function () {
                console.log("打开视频成功 ");
            },
            close : function (res) {
                console.log("视频播放结果 : " + res.isEnded);
            }
        });
```

用户点击 `关闭广告` 按钮的事件的回调函数



### dnsdk.isRewardedVideoLoaded\(\)

用于查询广告是否可播放。

> 由于部分平台会自动预先加载。所以我们提供此接口用于查询是否有加载好的广告。

#### 返回值

true-可播放 

false-不可播放



