# iOS

\### Demo工程克隆地址：

[http://gitblit.vigame.cn:6300/summary/VigameDemo-iOS.git](http://gitblit.vigame.cn:6300/summary/VigameDemo-iOS.git)

### 1. 将相关的文件添加到工程中

![](../../.gitbook/assets/1.png)

#### \(备注: 将deps文件删除引用。\)

### 2. 添加所有的 .framework .a 文件 路径和头文件链接

\(target-&gt;build setting -&gt; search path -&gt;Header Search Paths 中添加\) 特殊添加一项目录 路径

`"$(SRCROOT)/Vigame/include"`

`"$(SRCROOT)/Vigame/tools"`

`"$(SRCROOT)/Vigame/deps/boost/include"`

`"$(SRCROOT)/Vigame/deps/curl/include"`

`"$(SRCROOT)/Vigame/deps/openssl/include"`

`"$(SRCROOT)/Vigame/deps/zlib/include"`

![](../../.gitbook/assets/1648908-f0a533025fd7e71f.png)

### 3. 添加必要配置

1. 打开 Capabilities-&gt; Keychain Sharing 获取设备唯一标识
2. 在info.plist添加Google广告配置

    GADIsAdManagerApp：YES

3. 如果项目中使用到Applovin广告在info.plist添加

    AppLovinSdkKey：Occxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

4. 在VigameLibrary.plist 中检测 company\_appid 、apple\_appid、company\_prijid.

    以及相关的统计参数

5. 如果出海外包带有Facebook广告 需要在info.plist文件中添加Facebook 中相关的配置如下：

   ![fb&#x914D;&#x7F6E;](../../.gitbook/assets/2183351-96f3333dbc663e72.png)

6. 苹果新出的规定无论有没有使用到相机相册都得申请 权限
7. 游戏需要访问网络 需要有网络权限
8. 游戏第三方可能会用到定位，所有游戏info.plist添加NSLocationWhenInUseUsageDescription

### 4.添加系统支持库文件

target-&gt;build phases -&gt; Link Binary With Libraries

`OpenGLES.framework`

`OpenAL.framework`

`iAd.framework`

`WebKit.framework`

`AVFoundation.framework`

`Accelerate.framework`

`MobileCoreServices.framework`

`CoreMotion.framework`

`CoreLocation.framework`

`CoreTelephony.framework`

`QuartzCore.framework`

`StoreKit.framework`

`AdSupport.framework`

`UIKit.framework`

`CoreFoundation.framework`

`CoreGraphics.framework`

`CoreMedia.framework`

`CoreBluetooth.framework`

`CoreText.framework`

`Security.framework`

`MediaPlayer.framework`

`CFNetwork.framework`

`libresolv.9.tbd`

`SystemConfiguration.framework`

`MessageUI.framework`

`JavaScriptCore.framework`

`AudioToolBox.framework`

`GLKit.framework`

`libz.tbd`

`libsqlite3.tbd`

`libiconv.tbd`

`libxml2.tbd`

`libc++.tbd`

`libz.1.1.3.tbd`

`libresolv.tbd`

`libsqlite3.0.tbd`

`//接入tapjoy需要下面库并且需要添加测试设备`

`PassKit.framework`

`MapKit.framework`

`ImageIO.framework`

`CoreData.framework`

### 5. 设备编译选项

1. `Other Linker Flags添加-ObjC`

![](../../.gitbook/assets/2183351-f13ed84628186502.png.jpeg)

1. Enable Bitcode 设置为NO
2.   ![&#x8BBE;&#x7F6E;Bitcode](../../.gitbook/assets/1648908-a8b9998bf49b9737.png)

### 6 常见配置错误及解决方法

1. 在info.plist添加Google广告配置 GADIsAdManagerApp：YES不配置会出现崩溃

   ![&#x672A;&#x914D;&#x7F6E;Google&#x5E7F;&#x544A;ID](../../.gitbook/assets/1648908-10b02a368fa1b206.png)

添加方式如下：

 ![&#x6DFB;&#x52A0;Google&#x5E7F;&#x544A;&#x914D;&#x7F6E;&#x65B9;&#x5F0F;](../../.gitbook/assets/1648908-89539912206f3690.png)

1. Google广告由于用xib自动布局，需要最低iOS9版本会报如下错误 ![&#x7CFB;&#x7EDF;&#x7248;&#x672C;&#x592A;&#x4F4E;&#x62A5;&#x9519;](../../.gitbook/assets/1648908-60441f51b86e81a6.png)
2. 如果报这个错误，修改游戏支持iOS版本最低为iOS9，参考下图 ![&#x8BBE;&#x7F6E;iOS&#x6700;&#x4F4E;&#x652F;&#x6301;9](../../.gitbook/assets/1648908-e94d66e37fb2142e.png)
3. 缺少include文件配置报错

 ![&#x7F3A;&#x5C11;&#x914D;&#x7F6E;&#x9519;&#x8BEF;](../../.gitbook/assets/1648908-cf447bd6d14c7a26.png)

解决如下：

 ![&#x6DFB;&#x52A0;include&#x5F15;&#x7528;](../../.gitbook/assets/1648908-933ec652fe73bbd7.png)

1. 缺少include中boost文件引入错误

   ![&#x7F3A;&#x5C11;boost&#x5F15;&#x5165;&#x9519;&#x8BEF;](../../.gitbook/assets/1648908-5f38236e86b5d8e8.png)

解决如下：

 ![&#x6DFB;&#x52A0;boost&#x5F15;&#x7528;](../../.gitbook/assets/1648908-a4fce67fdbbba4ef.png)

1. **weak typeof\(self\)wSelf = self报错：- A parameter list without types is only allowed in a function definition. A corresponding warning tells me that** weak only applies to Objective-C object or block pointer types;type here is 'int'

解决方案: Xcode－&gt; Build Settings-&gt; C Language Dialect修改配置，C99改为GNU99，C99不包含typeof

### 7. 确认c++ 编译项

![](../../.gitbook/assets/2183351-cb8d2dc8d55a615c.png)

如未设置会报如下错

 ![D970B31A66A9D0CC47F120ECE3C4F362.jpg](../../.gitbook/assets/1648908-dc7dca47a865b797.jpg)

### 8设置项目为自动内存管理

![&#x8BBE;&#x7F6E;ARC](../../.gitbook/assets/2183351-ff19eccac2bf6326.png.jpeg) ![&#x8BBE;&#x7F6E;.png](../../.gitbook/assets/1648908-2b663a3c58c6a41b.png)

## 9接入微信配置（不接入忽略）

在info.plist文件添加

![](../../.gitbook/assets/1648908-3b9d2adf2506a9a7.jpg)

添加微信登陆URL Type

![](../../.gitbook/assets/1648908-7aa347ae8a163c04.png)

### 10 SDK初始化工作

**1 导入头文件**

在appDelegate文件中引入头文件`#import "IOSLoader.h"`

**2 调用初始化入口文件**

```text
- (BOOL)application:(UIApplication *)application willFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    [IOSLoader splashReport];//统计上报
    return YES;
}

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    [IOSLoader startLoaderLibrary];//初始化
    return YES;
}

- (BOOL)application:(UIApplication *)application continueUserActivity:(NSUserActivity *)userActivity restorationHandler:(void (^)(NSArray<id<UIUserActivityRestoring>> * _Nullable))restorationHandler {

    if (userActivity.activityType == NSUserActivityTypeBrowsingWeb) {
    [IOSLoader application:application continueUserActivity:userActivity];//appflyer统计相关设置
    return YES;
    }
    return NO;
}

- (void)applicationDidEnterBackground:(UIApplication *)application {
    [IOSLoader is_Active:false];//更新状态
}

- (void)applicationWillEnterForeground:(UIApplication *)application {
   [IOSLoader isAwaken];
}

- (void)applicationDidBecomeActive:(UIApplication *)application {
    [IOSLoader is_Active:true]; //更新状态、开屏广告
     [IOSLoader openAwakenAd];
}

-(BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<UIApplicationOpenURLOptionsKey,id> *)options {
    [IOSLoader isOpenURL];//解决唤醒广告在微信登录、充值频繁问题
    return YES;
}
```

### 交互流程

1. 我们提供一个测试包名和证书（已上线的项目\#为了能出广告\#）
2. 使用测试包名和证书出一个测试包--然后测试
3. 测试完成后 换正式包名和证书出正式包上传苹果商店



