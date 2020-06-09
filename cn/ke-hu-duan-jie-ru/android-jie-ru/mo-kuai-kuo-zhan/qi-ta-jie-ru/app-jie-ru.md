## 1.0 引入模块

```java
	xxximplementation WB.fixVersions('Proxy:APP')
```

## 1.1 初始化(application中调用)

```java
	AppCore.init(application);
```

## 1.2 生命周期接口（activity中对应生命周期调用）

```java
AppCore.onPause();

AppCore.onResume();
```

## 1.3 设置服务器数据获取成功的回调

```java
AppCore.setCfgLoadCallBack(CfgLoadedCallBack);
```

### CfgLoadedCallBack

```csharp
void onResult(int type) 
```

参数：

- type：  //AppCore.CTYPE_MM 
  //AppCore.CTYPE_AD 
  //AppCore.CTYPE_XYX 
  //AppCore.CTYPE_GAME 
  //AppCore.CTYPE_SPLASH 

  **回调返回成功后调用获取接口才能渠道数据**

示例：

```
AppCore.getInstance().setCfgLoadCallBack(new AppCore.CfgLoadedCallBack() {
    @Override
    public void onResult(int type) {
        if(type == AppCore.CTYPE_AD)
        {
            ADConfig adcfg =  AppCore.getInstance().getAdConfig();
            if(adcfg !=null)
            {
                Log.d(TAG, "  adcfg  = "+ adcfg.getSourceList().toString());
            }
        }
        else if(type == AppCore.CTYPE_XYX)
        {
            XYXConfig xyxCfg =  AppCore.getInstance().getXyxConfig();
            if(xyxCfg !=null)
            {
                Log.d(TAG, "  xyxCfg  = "+ xyxCfg.getItemList().toString());
            }
        }
    }
});
```

## 1.4 获取配置的常用接口

```
/**
     * 获取广告配置   在获取到服务器配置之前会返回上次获取到的数据
     **/
AppCore.getInstance().getAdConfig();
    /**
     * 获取 开屏配置   在获取到服务器配置之前会返回上次获取到的数据
     **/
AppCore.getInstance().getSplashCfg();
/**
     * 获取 开屏配置 
     * 在获取到服务器配置之前会返回上次获取到的数据
     * 优先返回广告配置 其次返回开屏配置
     **/
AppCore.getInstance().getModifiedSplashCfg();
/**
     * 获取 互推配置   在获取到服务器配置之前会返回上次获取到的数据
     **/
AppCore.getInstance().getXyxConfig();
/**
     * 更新开屏广告配置   
     **/
AppCore.getInstance().updateSplashCfg();


```



## 1.5 native常用接口

```java
import com.temp.proxy.AppNative;

    //自定义事件，需初始化后调用
   AppNative.nativeOnEvent(String key);

 //自定义事件，需初始化后调用
    AppNative.nativeOnEventLabel(String key,String val);
   //自定义事件，需初始化后调用。map 中  key 和 value 都不能含有 '=' 和 ','
    AppNative.nativeOnEventMap(String key, HashMap<String,String> map)
    //账号登录  暂时不可用
     AppNative.nativeOnSignIn(String account,String acountType);
    // 账号登出  暂时不可用
    AppNative.nativeOnSignOut();
   //设置用户等级
     AppNative.nativeSetUserLevel(int lv);
    // 开始关卡
    AppNative.nativeStartLevel(String lv);
   //退出关卡 需和开始关卡成对出现
    AppNative.nativeExitLevel(String lv);
    //通过关卡 需和开始关卡成对出现
     AppNative.nativeFinishLevel(String level,String score);
   //关卡失败 需和开始关卡成对出现
     AppNative.nativeFailLevel(String level,String score);
    /**
     * 支付统计
     * money 人民币价格
     * coin  虚拟币
     * source  支付方式
     **/
    AppNative.nativePay(double money,int coin,int source);
 	/**
     * 支付统计
     *  money 人民币价格
     *  item 道具名
     *  道具数量
     *  道具价格
     *  支付方式
     **/
    AppNative.nativePay2(double money,int coin,int source);
	//log 开关，默认为true
	AppNative.nativeSetLogEnabled(boolean enableLog);
	//获取 MM 协议返回数据 字符串
	AppNative.nativeGetMMChl();
	//获取广告配置  字符串
	AppNative.nativeGetADCfg();
	//获取互推配置 字符串
	AppNative.nativeGetXYXCfg();
	//获取游戏配置 字符串
	AppNative.nativeGetGameCfg();
	//从服务器获取游戏配置
	AppNative.nativeGetNetGameCfg(String ver);
	//更新 MM协议配置
	AppNative.nativeUpdateMMChl();
	//更新 广告配置
	AppNative.nativeUpdateADCfg();
	//更新 互推配置
	AppNative.nativeUpdateXYXCfg();
```



## 1.6 获取应用参数

```java
import com.temp.proxy.AppUtils;

//获取应用名称
AppUtils.getAppName();
//获取包名
AppUtils.get_package_name();
//获取渠道名		配置 meta-data name 为 com.app.sdk.channel
AppUtils.getChannel();
//获取项目ID	配置 meta-data name 为 com.app.sdk.prjid
AppUtils.get_prjid();
//获取产品id	配置 meta-data name 为 com.app.sdk.appid
AppUtils.get_appid();
//获取产品appkey配置 meta-data name 为 com.app.sdk.appkey
AppUtils.get_appkey();
//获取app版本
AppUtils.get_app_ver();
//获取imei
AppUtils.get_imei();
//获取网络状态 (0-无网络 1-手机网络 2-wifi网络 3-以太网络 4-蓝牙网络)
AppUtils.get_net_state();
```

### 



