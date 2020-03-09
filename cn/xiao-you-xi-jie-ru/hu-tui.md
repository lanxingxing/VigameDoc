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

互推数据说明：

| 参数 | 类型 | 描述 |
| :--- | :--- | :--- |
| iconList | Array | icon广告互推列表 |
| bannerList | Array | 横幅式互推列表 |
| plaqueList | Array | 插屏式互推列表 |
| buttomList | Array | 首页的滚动互推列表 |
| gouppageList | Array | 首页侧边栏热门推荐互推列表 |
| moregroupList | Array | 分发页的更多游戏互推列表 |
| hotgameList | Array | 分发页的大图滚动互推列表 |
| fungameList | Array | 分发页的滚动互推列表 |

互推二级字段说明：

| 参数 | 类型 | 描述 |
| :--- | :--- | :--- |
| id | String | 推广产品的id |
| icon | String | 推广产品图标地址 |
| plist | String | 帧动画文件地址 |
| pushImage | String | 推广产品二维码图 |
| pushAppID | String | 推广产品的微信Appid |
| open | String | 打开类型（1.image 2.url 3.miniprogram） |
| openPath | String | 打开的小程序的路径 |
| gameName | String | 推广产品的名称 |
| extra | String | 额外参数 |

> 注意：跳转小程序时，pushAppID和openPath字段需要同时用到，否则无法监控推送效果。

#### 1.3 互推展示统计

方法接口：

```text
dnsdk.tjSendShowEvent(object)
```

参数说明：

| 参数/key | 描述 | 参数类型/value | 是否必传 |
| :--- | :--- | :--- | :--- |
| label | 当前互推的唯一标识符 | String | 是 |
| pushappid | 要跳转的appid | String | 是 |
| placement | 展示界面名称标识 | String | 是 |
| eventid | 互推数据列表标识 | String | 是 |

示例代码：

```javascript
// 展示上报
var tjData = {
        label: this.data.id,
        pushappid: this.data.pushAppID,
        placement: "home",
          eventid: "grouppage"
};
dnsdk.tjSendShowEvent("bottom", tjData);
```

#### 1.4 互推点击统计

方法接口：

```text
dnsdk.tjSendClickEvent(object)
```

参数说明：

| 参数/key | 描述 | 参数类型/value | 是否必传 |
| :--- | :--- | :--- | :--- |
| label | 当前互推的唯一标识符 | String | 是 |
| pushappid | 要跳转的appid | String | 是 |
| placement | 展示界面名称标识 | String | 是 |
| eventid | 互推数据列表标识 | String | 是 |

示例代码：

```javascript
// 点击上报
var tjData = {
 label: this.data.id,
 pushappid: this.data.pushAppID,
 placement: "home",
 eventid: "grouppage"
 };

dnsdk.tjSendClickEvent(tjData);
```

