# 分享

### 1.分享接口

#### 1.1 设置分享

> 将微信的wx.onShareAppMessage替换成dnsdk.onShareAppMessage

方法接口：

```javascript
dnsdk.onShareAppMessage(func);
```

示例代码：

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

#### 1.2 分享

方法接口：

```javascript
dnsdk.shareAppMessage(object);
```

> 将微信的wx.shareAppMessage替换成dnsdk.shareAppMessage

示例代码：

```javascript
// 分享，主动拉起转发，进入选择通讯录界面
  dnsdk.shareAppMessage({
    imageUrl : 'https://favicon.yandex.net/favicon/aldwx.com',//转发标题
    title    : '分享title',//转发标题
    query    : 'id=89&select=2'//查询字符串，必须是 key1=val1&key2=val2 的格式。从这条转发消息进入后，可通过 wx.getLaunchOptionSync() 或 wx.onShow() 获取启动参数中的 query。
  })
```

### 

