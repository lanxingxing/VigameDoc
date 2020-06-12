# 互推

## 1.互推接口

#### 1.1 监听互推数据获取成功

方法接口:

```javascript
dnsdk.onDataReceived(func)
```

示例代码：

```javascript
 dnsdk.onDataReceived(function (data) {
     dnsdk.log(data);
 });
```

#### 1.2 使用互推数据

方法接口:

```javascript
dnsdk.data.pushData
```

示例代码：

```javascript
dnsdk.data.pushData.iconList
```

互推数据使用说明：

_**oppo**_

| 参数 | 类型 | 互推位置 |
| :--- | :--- | :--- |
| iconList | Array | icon样式（单个图标）互推 |
| gouppageList | Array | 首页侧边栏、6宫格矩阵（结算、失败页面） |

_**头条**_

| 参数 | 类型 | 互推位置 |
| :--- | :--- | :--- |
| gouppageList | Array | 6宫格矩阵（结算、失败页面） |

_**微信**_

| 参数 | 类型 | 互推位置 |
| :--- | :--- | :--- |
| moregameList | Array | 首页开屏弹框 |
| iconList | Array | 首页图标互推 |
| bannerList | Array | 横幅式互推 |
| plaqueList | Array | 插屏式互推 |
| buttomList | Array | 猜你爱玩互推 |
| grouppageList | Array | 6宫格矩阵（结算、失败页面） |
| moregroupList | Array | 插屏好友图像 |
| hotgameList | Array | 汇聚页热门推荐 |
| fungameList | Array | 汇聚页好友在玩互推 |

互推二级字段说明：

| 参数 | 类型 | 描述 |
| :--- | :--- | :--- |
| id | String | 推广产品的id |
| icon | String | 推广产品图标地址 |
| plist | String | 帧动画文件地址 |
| pushImage | String | 推广产品二维码图 |
| pushAppID | String | 推广产品的微信Appid（oppo小游戏为包名） |
| open | String | 打开类型（1.image 2.url 3.miniprogram） |
| openPath | String | 打开的小程序的路径 |
| gameName | String | 推广产品的名称 |
| extraData | String | 需要传递给目标小程序的数据，目标小程序可在 `App.onLaunch`，`App.onShow` 中获取到这份数据 |

> 注意：跳转小程序时，pushAppID和openPath字段需要同时用到，否则无法监控推送效果。

#### 1.3 互推展示统计

方法接口：

```text
dnsdk.tjSendShowEvent(eventid,object)
```

参数说明：

| 参数 | 类型 | 描述 |
| :--- | :--- | :--- |
| eventid | String | 事件名称，通常为互推数据列表标识 |
| object | Object | 上报的信息 |

#### Object object:

| 参数/key | 描述 | 参数类型/value | 是否必传 |
| :--- | :--- | :--- | :--- |
| label | 当前互推的唯一标识符 | String | 是 |
| pushappid | 要跳转的appid | String | 是 |
| placement | 展示界面名称标识 | String | 是 |

示例代码：

```javascript
// 展示上报
var tjData = {
        label: this.data.id,
        pushappid: this.data.pushAppID,
        placement: "home"
};
dnsdk.tjSendShowEvent("grouppage", tjData);
```

#### 1.4 互推点击统计

方法接口：

```text
dnsdk.tjSendClickEvent(eventid, object)
```

参数说明：

| 参数 | 类型 | 描述 |
| :--- | :--- | :--- |
| eventid | String | 事件名称，通常为互推数据列表标识 |
| object | Object | 上报的信息 |

#### Object object:

| 参数/key | 描述 | 参数类型/value | 是否必传 |
| :--- | :--- | :--- | :--- |
| label | 当前互推的唯一标识符 | String | 是 |
| pushappid | 要跳转的appid | String | 是 |
| placement | 展示界面名称标识 | String | 是 |

示例代码：

```javascript
// 点击上报
var tjData = {
 label: this.data.id,
 pushappid: this.data.pushAppID,
 placement: "home"
};

dnsdk.tjSendClickEvent("grouppage", tjData);
```

### 2.小程序跳转

> 在微信、QQ、OPPO小游戏上生效

方法接口：

```text
dnsdk.navigateToMiniProgram(object)
```

参数说明：

#### Object object:

| 属性 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| appId | string | 是 | 要打开的小程序 appId，对于oppo小游戏该参数是包名 |
| path | string | 否 | 打开的页面路径，如果为空则打开首页 |
| extraData | object | 否 | 需要传递给目标小程序的数据，目标小程序可在 `App.onLaunch`，`App.onShow` 中获取到这份数据。 |
| envVersion | string | 否 | 要打开的小程序版本。仅在当前小程序为开发版或体验版时此参数有效。如果当前小程序是正式版，则打开的小程序必定是正式版。 |
| success | function | 否 | 接口调用成功的回调函数 |
| fail | function | 否 | 接口调用失败的回调函数 |
| complete | function | 否 | 接口调用结束的回调函数（调用成功、失败都会执行 |

示例代码：

```javascript
dnsdk.navigateToMiniProgram({
  appId: selfData.pushAppID,
  path: selfData.openPath,
  extraData: selfData.extraData,
  success:function(res) {
    // 打开成功
  },
  fail:function() {
    //打开失败
  }
})
```

### 3.头条小游戏弹窗

参考以下链接接入：

[https://developer.toutiao.com/dev/cn/mini-game/develop/open-capacity/more-mini-game/tt.showmoregamesmodal](https://developer.toutiao.com/dev/cn/mini-game/develop/open-capacity/more-mini-game/tt.showmoregamesmodal)

