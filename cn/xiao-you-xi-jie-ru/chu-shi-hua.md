# 初始化



### 1.初始化SDK（必接）

方法接口：

```text
dnsdk.init(appid,adData);
```

参数说明：

| 参数 | 参数类型 | 是否必传 | 描述 |
| :--- | :--- | :--- | :--- |
| appid | String | 是 | 产品ID |
| adData | Object | 否 | 广告参数 |

adData 属性：

| 标识 | 参数类型 | 描述 |
| :--- | :--- | :--- |
| wechat | Object | 微信小游戏 |
| qq | Object | QQ小游戏 |
| tt | Object | 头条小游戏 |
| oppo | Object | Oppo小游戏 |
| vivo | Object | Vivo小游戏 |

二级Object属性说明：

| 参数 | 类型 | 描述 |
| :--- | :--- | :--- |
| bannerAdId | String | Banner广告ID |
| interstitialAdId | String | 插屏广告ID |
| rewardedVideoAdId | String | 激励视频广告ID |

示例代码：

```javascript
var adData = {
    wechat: {
        bannerAdId: "adunit-de95d0a3dfda7d13",
        interstitialAdId: "adunit-7a19f10e95343d01",
        rewardedVideoAdId: "adunit-858bfb991ab0f3e2"
    },
    oppo: {
        bannerAdId: "158197",
        interstitialAdId: "158198",
        rewardedVideoAdId: "158203"
    },
    vivo: {
        bannerAdId: "a43ae2d881d24b37b37d2f8fc464470b",
        interstitialAdId: "5c70d8170f0245b8ba8893544b41169a",
        rewardedVideoAdId: "9dd39bd805514e1f85b02a4316ecbe32"
    },
    qq: {
        bannerAdId: "ba4c4f87b2a6bdc4ec0d59bbaffc5723",
        interstitialAdId: "d4a1ecbcdc53cd0ba61769982c0fb603",
        rewardedVideoAdId: "d710a7647e9e5de62294827aaee11665"
    },
    tt: {
        bannerAdId: "1v2pi8lvk8w68965eg",
        interstitialAdId: "11286cj144c4d5g841",
        rewardedVideoAdId: "18g7egd3mm9222217j"
    }
};

//初始化
dnsdk.init("20065", adData);
```

### 2.初始化监听

方法接口：

```
dnsdk.onInit(Object object);
```

参数说明：

##### Object object:

| 参数     | 参数类型 | 是否必传 | 描述                                         |
| :------- | :------- | :------- | :------------------------------------------- |
| success  | function | 否       | 接口调用成功的回调                           |
| fail     | function | 否       | 接口调用失败的回调                           |
| complete | function | 否       | 接口调用结束的回调（调用成功、失败都会执行） |

##### Object res:

| 参数     | 参数类型 | 描述                                           |
| :------- | :------- | :--------------------------------------------- |
| error    | int      | 错误码。0表示成功，其他表示网络错误。          |
| provider | String   | 当前所在的平台(wechat/qq/oppo/vivo/tt)         |
| openid   | String   | 能取到平台openid时为平台的openid，否则为uuid。 |
| ptOpenid | String   | 平台的openid                                   |



示例代码：

```
dnsdk.onInit({
	success:function(res){
		
	},
	fail:function(res){
	
	},
	complete:function(res){
	
	}
});
```
