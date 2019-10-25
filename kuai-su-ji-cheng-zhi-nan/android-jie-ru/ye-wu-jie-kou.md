---
description: 常用业务接口说明
---

# 业务接口

## 1. 基础功能模块

### 1.1 初始化\(必接\)

```text
CoreNative.init();
```

### 1.2 设置退出响应代码

```text
PayNative.setGameExitCallback(new Runnable() {

    @Override
    public void run() {
        // TODO Auto-generated method stub
        CoreNative.gameExit();//该方法必须调用
        currentActivity.finish();
        System.exit(0);
    }
});
```

### 1.3 获取应用参数

```text
//获取应用名称
Utils.getAppName();
//获取包名
Utils.get_package_name();
//获取渠道名
Utils.getChannel();
//获取项目ID
Utils.get_prjid();
//获取app版本
Utils.get_app_ver();
//获取imei
Utils.get_imei();
```

### 1.4 获取审核开关

```text
ChnlManager.getValueForKey("audit");
```

返回值:0-未审核 1-审核中

### 1.5 获取自定义开关

```text
String customKey = "你的自定义key值";
ChnlManager.getValueForKey(customKey);
```

### 1.3 使用兑换码

```text
String dhm = "111111";
CDKey.use(dhm,new CDKey.DhmCallback() {

    @Override
    public void onFinish(CDKey.DhmData data) {
        // TODO Auto-generated method stub
        showToast(data.message);
    }
});
```

### 1.4 打开活动页面

```text
com.vigame.Activity.open();
```

### 1.5 打开公告

```text
Notice.open();
```

### 1.6 打开排行榜

```text
Rank.open();
```

### 1.7 打开用户协议

```text
UserAgreement.open();
```

注：用户协议的内容可通过assets/agrement.html修改

### 1.8 打开问题反馈

```text
Feedback.open();
```

## 2. 广告能力

### 2.1 初始化（必接）

```text
ADNative.init();
```

### 2.2 设置广告打开回调

```text
//设置广告回调
ADNative.setAdResultCallback(new ADManager.AdParamCallback() {

    @Override
    public void onStatusChanged(ADParam arg0, int status) {
        // TODO Auto-generated method stub
        Log.d(TAG,"onStatusChanged:"+status);
    }

    @Override
    public void onRequestAddGameCoin(ADParam arg0, int arg1, int arg2,
            String arg3) {
        // TODO Auto-generated method stub
        Log.d(TAG,"onRequestAddGameCoin");

    }

    @Override
    public void onOpenResult(ADParam adParam, int result) {
        // TODO Auto-generated method stub
        Log.d(TAG,"onOpenResult:"+result);
        //判断广告类型是否是视频
        if(adParam.getType().equals(ADDef.AD_TypeName_Video)){

        }

        if(result== ADParam.ADOpenResult_Success){//广告打开成功

        }
        else {//广告打开失败

        }
    }
});
```

回调方法说明：  
**AdParamCallback .onOpenResult\(onOpenResult\(ADParam adParam , int result\)\)** //广告打开结果通知  
adParam:广告相关参数（可获取广告ID，广告状态，广告代理商） result:广告打开结果：0成功 1失败 2取消

**AdParamCallback.onRequestAddGameCoin\(ADParam adParam, int result, int num, String reason\)**//积分墙类广告的钻石奖励通知  
adParam:广告相关参数  
result：奖励结果类型：0成功 1失败 2取消  
num：奖励数量  
reason：通知字符串

### 2.3 打开广告

```text
ADNative.openAd(String adPositionName);
```

adPositionName： 广告位名称

### 2.4 查看广告是否就绪

```text
ADNative.isAdReady(String adPositionName);
```

```text
ADNative.isAdReady2(String adPositionName, String type);
```

adPositionName:广告位名称  
type: 广告类型 \(plaque-插屏 video-视频 banner-广告条 wall-积分墙 splash 启动画\)

### 2.5 关闭广告

```text
ADNative.closeAd(String adPositioname);
```

adPositionName： 广告位名称

### 2.6 获取视频限制次数

```text
ADNative.getVideoLimitOpenNum();
```

返回值：可播放次数，为-1表示无限次。

### 2.7 广告位是否已打开

可用于防止用户连续多次点击广告按钮

```text
ADNative.isAdOpen(String adPositionName);
```

返回值：true-广告已被打开 false-广告未被打开

### 2.8 某关卡是否出现广告

```text
ADNative.isAdBeOpenInLevel(String adPositionname,int lv);
```

参数： adPositionname-广告位名称 lv-关卡编号\(1-无限\)  
返回值：true-可出现 false-不可出现

### 2.9 查询某种广告类型是否存在

```text
ADNative.isAdTypeExist(String adType);
```

参数： adType-广告类型 （1.横幅：banner, 2.插屏：plaque， 3.视频：video, 4.信息流广告：msg）  
返回值：true-存在 false-不存在

### 2.10 获取广告位控制参数

```text
ADNative.getAdPositionParam(String positionName,String key);
```

参数： positionName-广告位名称  key-控制字段名称  
返回值：value值

## 3. 计费相关

### 3.1 初始化

```text
PayNative.init();
```

### 3.2 设置支付回调

```text
PayNative.setPayResultCallback(new PayManager.PayCallback() {

    @Override
    public void onPayFinish(PayParams params) {
        // TODO Auto-generated method stub
        switch (params.getPayResult()){
            //支付成功
            case PayDef.PAY_RESULT_SUCCESS:
                break;
            //支付失败
            case PayDef.PAY_RESULT_FAIL:
                break;
            //取消支付
            case PayDef.PAY_RESULT_CANCEL:
                break;
        }
    }

    @Override
    public void onInitPayAgentFinish(BasePayAgent arg0) {
        // TODO Auto-generated method stub

    }
});
```

### 3.3 获取支付按钮类型

```text
PayNative.getButtonType(payID);
```

### 3.4 该市场是否支持退出

```text
PayNative.isExitGame();
```

### 3.5 调用退出框

```text
PayNative.openExitGame();
```

**因游戏有自己的退出界面，建议按照如下方法判断：**


```text
if(PayNative.isExitGame()){
    //通过调用下面的方法弹出渠道的退出
    PayNative.openExitGame();
}
else{
    //这里弹出引擎的退出界面
    ...
}
```

### 3.6 获取所在的市场类型

```text
PayNative.getMarketType();
```

### 3.7 获取礼包控制信息

```text
PayNative.getGiftCtrlFlagUse(int ctrl);
```

{% hint style="info" %}
ctrl：控制参数

返回值：控制参数

控制参数说明：  
1-新手礼包 - 进入游戏首页时如果没购买过新手礼包则弹出  
2-快冲 - 用户虚拟货币不足时弹出  
3-限时礼包 - 进入游戏首页时如果已经买过新手礼包则弹出  
4-过关奖励 - 过关时弹出  
5-vip礼包 - 进入关卡选择页时弹出 6-今日特价  
7-实惠大礼包  
8-商城
{% endhint %}

### 3.8 调用支付

```text
PayNative.orderPay(id);
```

id:计费点ID

```text
orderPay(int id,String userdata);
```

id:游戏中定义的计费点id  
userdata:用户数据

```text
orderPay(int id,int price，String userdata);
```

id:游戏中定义的计费点id  
price:计费点的价格，单位为分。  
userdata:用户数据

```text
orderPay(int id, int price, int payType，String userdata);
```

id:游戏中定义的计费点id  
price:计费点的价格，单位为分。  
payType:指定的支付类型。eg:PayDef.PAY\_TYPE\_MM  
userdata:用户数据

### 3.9 是否需要有更多游戏按钮

```text
PayNative.isMoreGame();
```

### 3.10 打开更多游戏

```text
PayNative.openMoreGame();
```

### 3.11 跳转应用商店的某个应用详情页

```text
PayNative.openMarket(String package);
```

package:跳转应用的包名

### 3.12 跳转当前应用的商店详情页

```text
PayNative.openAppraise();
```

## 4. 统计相关

### 4.1 初始化

```text
TJNative.init();
```

### 4.2 自定义统计

```text
TJNative.event(String eventId);
TJNative.event(String eventId, String label);
TJNative.event(String eventId, HashMap<String, String> attributes);
```

eventId: 为当前统计的事件ID  
label：事件的标签属性  
attributes:事件的多标签属性

### 4.3 关卡统计

```text
TJNative.startLevel(String level);
TJNative.finishLevel(String level, String score);
TJNative.failLevel(String level, String score)
```

level:关卡名称
score:关卡得分，可传空

### 4.4 计费统计

统计充值：

```text
TJNative.pay(double money, double coin, int source);
```

money:金额，单位元
coin：买到的钻石数
source：充值渠道标识（使用PayNative.getDefaultPayType获取）



统计充值并购买道具：

```text
TJNative.pay(double money, String item, int number, double price, int source);
```

money:金额，单位元
item:买到的道具名称
number：买到的道具数量
price：买到的道具价值
source：充值渠道标识（使用PayNative.getDefaultPayType获取）

## 5. 互推相关

### 5.1 初始化

```text
XYXNative.init();
```

### 5.2 获取互推数据

```text
XYXNative.getConfig();
```

### 5.3 上报互推展示

```text
XYXConfig config = XYXNative.getConfig();
ArrayList<XYXItem> list = config.getItemList();
if (list != null && list.size() > 0) {
    XYXItem item = list.get(0);
    config.exposureShow(item);
}
```

### 5.4 响应互推点击

```text
XYXConfig config = XYXNative.getConfig();
ArrayList<XYXItem> list = config.getItemList();
if (list != null && list.size() > 0) {
    XYXItem item = list.get(0);
    config.handleClick(item);
}
```

## 6. 社交相关

### 6.1 初始化

```text
SocialProxy.init()
```

### 6.2 登录及获取用户信息

```text
SocialProxy.loginAndUpdateInfo(SocialDef.TYPE_WX,new SocialProxy.SocialCallBack() {
    @Override
    public void onResult(HashMap<String, String> map) {
        if(map.get("retCode").equalsIgnoreCase("1"))//获取用户信息成功
        {
            Log.i("skay","loginAndUpdateInfo  success  ");
            Log.i("skay","openId  is  "+map.get("openid"));
            Log.i("skay","nickname  is  "+map.get("nickname"));
            Log.i("skay","headimgUrl  is  "+map.get("headimgUrl"));
            Log.i("skay","sex  is  "+map.get("sex"));
        }else//登录失败/获取用户信息失败
        {
            Log.i("skay","loginAndUpdateInfo  fail   "+map.toString());
        }
    }
});
```

### 6.3 微信需引用微信模块

```text
implementation 'com.libVigame.Social:WeChat:2.1.9'//改为最新版本
```

### 6.4 微信登录需添加 WXEntryActivity类\(包名为 applicationID + ".wxapi"\)

```text
package com.hw2.jgzsj2.wxapi;//包名为 applicationID + ".wxapi"

import android.app.Activity;
import android.content.Intent;
import android.os.Bundle;

import com.libSocial.WeChat.WeChatActivityHandler;

public class WXEntryActivity extends Activity {
    private WeChatActivityHandler weChatActivityHandler = null;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        weChatActivityHandler = new WeChatActivityHandler();
        weChatActivityHandler.onCreate(this);
        this.finish();
    }
    @Override
    protected void onNewIntent(Intent intent) {
        super.onNewIntent(intent);
        if (weChatActivityHandler != null) {
            weChatActivityHandler.onNewIntent(intent);
        }
    }
}
```

