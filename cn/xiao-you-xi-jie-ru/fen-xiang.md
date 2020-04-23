# 分享

## 1.分享接口

### 1.1 设置分享

> 在微信、QQ、头条小游戏生效
>
> 将微信的wx.onShareAppMessage替换成dnsdk.onShareAppMessage

方法接口：

```javascript
dnsdk.onShareAppMessage(callback);
```

参数说明：

### function callback <a id="function-callback"></a>

用户点击右上角菜单的「转发」按钮时触发的事件的回调函数

**参数**

**Object res**

| 属性 | 是否必须 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| title | 否 | string | 转发标题，不传则默认使用服务器数据 |
| imageUrl | 否 | string | 转发显示图片的链接，不传则使用服务器数据。可以是网络图片路径或本地图片文件路径或相对代码包根目录的图片文件路径。显示图片长宽比是 5:4 |
| query | 否 | string | 查询字符串，必须是 key1=val1&key2=val2 的格式。从这条转发消息进入后，可通过 wx.getLaunchOptionsSync\(\) 或 wx.onShow\(\) 获取启动参数中的 query。 |

示例代码1：

```javascript
dnsdk.onShareAppMessage();//使用服务器数据
```

示例代码2：

```javascript
//分享，监听用户点击右上角菜单的“转发”按钮时触发的事件
  dnsdk.onShareAppMessage(function(){
    return {
      imageUrl : 'https://favicon.yandex.net/favicon/aldwx.com', //转发显示图片的链接
      title    : '分享title', //转发标题
      query    : 'id=89&select=2'//查询字符串，必须是 key1=val1&key2=val2 的格式。从这条转发消息进入后，可通过 wx.getLaunchOptionSync() 或 wx.onShow() 获取启动参数中的 query。
    }
  })
```

### 

### 1.2 分享

> 在微信、QQ、头条小游戏生效

方法接口：

```javascript
dnsdk.shareAppMessage(object);
```

> 将微信的wx.shareAppMessage替换成dnsdk.shareAppMessage

示例代码1：

```javascript
dnsdk.shareAppMessage();//使用服务器数据
```

示例代码2：

```javascript
// 分享，主动拉起转发，进入选择通讯录界面
  dnsdk.shareAppMessage({
    imageUrl : 'https://favicon.yandex.net/favicon/aldwx.com',//转发标题
    title    : '分享title',//转发标题
    query    : 'id=89&select=2'//查询字符串，必须是 key1=val1&key2=val2 的格式。从这条转发消息进入后，可通过 wx.getLaunchOptionSync() 或 wx.onShow() 获取启动参数中的 query。
  })
```

