# iOS



## 1. CocoaPods add KTMSDK

cocoapods can  save you time in project configuration.iOS SDK be published through cocoapods. It is recommended that you use pod.

1.  Install CocoaPods 

Cocoapods is a dependency manager for swift and Objective-C projects. It has more than 49000 third-party libraries, and more than 300000 apps are using cocoapods for dependency management. Cocoapods can help you expand your projects gracefully. If you have not installed cocoapods, you can install it from the following command line. For more details, please visit [CocoaPods HomePage](https://cocoapods.org/)。 

    ```
    $ sudo gem install cocoapods

    ```

    Note: the installation process may take a long time, or it may fail due to network conditions. Please try again and again until the installation is successful.

2.  Configure Podfile file 

There is a file named Podfile in the folder where your project files are located. If you use cocoapods for the first time, you can initialize a podfile with the following command:

    ```
    $ pod init
    ```

   open the Podfile file, the following contents should be included (there may be some differences in the specific contents): it has the function of accessing the demand list pod

    ```
    source 'http://wy@dnsdk.vimedia.cn:8080/r/IOSMavenSpec.git' #远程私有库地址
    source 'https://cdn.cocoapods.org/' #公有库地址
    
    platform :ios, '9.0'
    target 'Unity-iPhone' do
    
    sdkVersion='1.0.0'
    
    ####--广告---###
    pod 'KTMSDK/Ads/ByteDance',sdkVersion
    pod 'Bytedance-UnionAD', '2.8.0.1'
    pod 'KTMSDK/Ads/IronSource',sdkVersion
    pod 'KTMSDK/Ads/Admob',sdkVersion
    pod 'KTMSDK/Ads/GDT',sdkVersion
    pod 'KTMSDK/Ads/Unity',sdkVersion
    pod 'KTMSDK/Ads/Mintegral',sdkVersion
    pod 'KTMSDK/Ads/Facebook',sdkVersion
    pod 'KTMSDK/Ads/Applovin',sdkVersion
    pod 'KTMSDK/Ads/KTMAd',sdkVersion
    pod 'KTMSDK/Ads/Vungle',sdkVersion
    
    ####--统计---###
    pod 'KTMSDK/Analysis/Umeng',sdkVersion
    pod 'KTMSDK/Analysis/TrackingIO',sdkVersion
    pod 'KTMSDK/Analysis/ByteDance',sdkVersion
    pod 'KTMSDK/Analysis/DataEye',sdkVersion
    pod 'KTMSDK/Analysis/Appsflyer',sdkVersion
    pod 'KTMSDK/Analysis/Facebook',sdkVersion
    pod 'KTMSDK/Analysis/Adjust',sdkVersion
    pod 'KTMSDK/Analysis/Tenjin',sdkVersion
    pod 'KTMSDK/Analysis/Google',sdkVersion
    
    ####--社交（登录）---###
    pod 'KTMSDK/Social/wechat',sdkVersion
    pod 'KTMSDK/Social/facebook',sdkVersion
    pod 'KTMSDK/Social/apple',sdkVersion
    
    ####--扩展---###
    pod 'KTMSDK/Extension/notice',sdkVersion
    pod 'KTMSDK/Extension/activity',sdkVersion
    pod 'KTMSDK/Extension/auth',sdkVersion
    
    ####--内购---###
    pod 'KTMSDK/IAP',sdkVersion 
    
    ####--Bugly---###
    pod 'KTMSDK/Bugly',sdkVersion
    
    end
    
    ```
    Note: ironsource aggregate ads need to be imported separately
    ```
    #IronSource 聚合广告按需添加
    pod 'IronSourceAdMobAdapter','4.3.10.1'
    pod 'IronSourceFacebookAdapter','4.3.14.0'
    pod 'IronSourceUnityAdsAdapter','4.3.0.1'
    pod 'IronSourceTikTokAdapter','4.1.2.7'
    pod 'IronSourceAppLovinAdapter','4.3.10.1'
    pod 'IronSourceMintegralAdapter','4.3.1.0'
    ```
    
## 2.Add Vigame Module
1、auto set
add auto.sh in your project，command auto.sh
2、download Vigame
url: https://pan.baidu.com/s/1dE6OxUYIrb5VHxPMgPYEcA    Extraction code: k3cd 

add  .a  link

 (Note: delete deps file。\)


`"$(SRCROOT)/Vigame/include"`

`"$(SRCROOT)/Vigame/deps/boost/include"`

`"$(SRCROOT)/Vigame/deps/curl/include"`

`"$(SRCROOT)/Vigame/deps/openssl/include"`

`"$(SRCROOT)/Vigame/deps/zlib/include"`




## 3. Add Necessary Configuration

1. Open Capabilities-&gt; Keychain Sharing 
2. info.plist Add Admob Configuration

   GADIsAdManagerApp：YES

4. VigameLibrary.plist  add company\_appid 、apple\_appid、company\_prijid、company\_appkey.

   configuration

5. if contain Facebook ad   please find info.plist，add Facebook ad configuration：

   ![fb&#x914D;&#x7F6E;](../../../.gitbook/assets/2183351-96f3333dbc663e72.png)

6. Apple's new rules require permission to use camera albums or not
7. Games need access to the network, and network permission is required
8.  info.plist add  NSLocationWhenInUseUsageDescription



## 4. Device compilation options

1. Enable Bitcode set  NO
2. ![&#x8BBE;&#x7F6E;Bitcode](../../../.gitbook/assets/1648908-a8b9998bf49b9737.png)


## 5. Wechat（No Access Ignore）

info.plist  add

![](../../../.gitbook/assets/1648908-3b9d2adf2506a9a7.jpg)

add wechat URL Type

![](../../../.gitbook/assets/1648908-7aa347ae8a163c04.png)

## 6. SDK initialization

**1. import **

`#import "IOSLoader.h"`

**2. Call initialization method**

```objectivec
- (BOOL)application:(UIApplication *)application willFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    [IOSLoader splashReport];//统计上报
    return YES;
}

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    [IOSLoader application:application DidFinishLaunchingWithOptions:launchOptions];//初始化

    [IOSLoader openSplash]; //闪屏广告
    return YES;
}

- (BOOL)application:(UIApplication *)application continueUserActivity:(NSUserActivity *)userActivity restorationHandler:(void (^)(NSArray<id<UIUserActivityRestoring>> * _Nullable))restorationHandler {

    return [IOSLoader application:application continueUserActivity:userActivity restorationHandler:restorationHandler];
}

- (void)applicationDidEnterBackground:(UIApplication *)application {
    [IOSLoader applicationDidEnterBackground:application];//更新状态
}

- (void)applicationWillEnterForeground:(UIApplication *)application {
   [IOSLoader applicationWillEnterForeground:application];
}

- (void)applicationDidBecomeActive:(UIApplication *)application {
   [IOSLoader applicationDidBecomeActive:application];; //更新状态、开屏广告
}

-(BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<UIApplicationOpenURLOptionsKey,id> *)options {
    return [IOSLoader application:app openURL:url options:options];
}
```

## Interaction Process

1. We provide a test package name and certificate (for the projects that have been launched, in order to be able to advertise)
2. Use the test package name and certificate to generate a test package -- then test
3. After the test, change the name and certificate of the official package and upload it to Apple store

