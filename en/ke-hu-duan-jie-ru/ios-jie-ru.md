# iOS

## Clone URL of Demo：

[http://gitblit.vigame.cn:6300/summary/VigameDemo-iOS.git](http://gitblit.vigame.cn:6300/summary/VigameDemo-iOS.git)

## 1. Add related files to the project

![](https://github.com/jieban0604/VigameDoc/tree/3e6ec92fbfeb594c2d6cc7a14fdca2834eb651ee/en/.gitbook/assets/1.png)

### \(Remark: Delete deps file)

## 2. Add  xx .a  dependency path

\(target-&gt;build setting -&gt; search path -&gt;Header Search Paths add the following set\) 

`"$(SRCROOT)/Vigame/include"`

`"$(SRCROOT)/Vigame/tools"`

`"$(SRCROOT)/Vigame/deps/boost/include"`

`"$(SRCROOT)/Vigame/deps/curl/include"`

`"$(SRCROOT)/Vigame/deps/openssl/include"`

`"$(SRCROOT)/Vigame/deps/zlib/include"`

![](https://github.com/jieban0604/VigameDoc/tree/3e6ec92fbfeb594c2d6cc7a14fdca2834eb651ee/en/.gitbook/assets/1648908-f0a533025fd7e71f.png)

## 3. Add necessary configuration

1. open Capabilities-&gt; Keychain Sharing 

2. Add Google ad configuration in info.plist

   GADIsAdManagerApp：YES

3. Add AppLovin ad configuration in info.plist

   AppLovinSdkKey：Occxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

4. Detect company_appid 、apple_appid、company_prijid in VigameLibrary.plist.

   And relevant statistical parameters

5. If there are Facebook ads in offshore outsourcing, you need to add the following configuration in the info.plist file:

   ![fb&#x914D;&#x7F6E;](https://github.com/jieban0604/VigameDoc/tree/3e6ec92fbfeb594c2d6cc7a14fdca2834eb651ee/en/.gitbook/assets/2183351-96f3333dbc663e72.png)

6. Apple's new rules require permission to use camera albums or not

7. Games need access to the network, and network permission is required.

8. The third party of the game may use location. All games info.plist add nslocationwheninuseusagedescription

## 4.Add system support library file

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

`//Access to tapjoy requires the following libraries and add test equipment`

`PassKit.framework`

`MapKit.framework`

`ImageIO.framework`

`CoreData.framework`

## 5. Device compilation options

1. `Other Linker Flags add -ObjC`

![](https://github.com/jieban0604/VigameDoc/tree/3e6ec92fbfeb594c2d6cc7a14fdca2834eb651ee/en/.gitbook/assets/2183351-f13ed84628186502.png.jpeg)

1. Enable Bitcode set to  NO
2. ![&#x8BBE;&#x7F6E;Bitcode](https://github.com/jieban0604/VigameDoc/tree/3e6ec92fbfeb594c2d6cc7a14fdca2834eb651ee/en/.gitbook/assets/1648908-a8b9998bf49b9737.png)

## 6. Common configuration errors and Solutions

1. Add Google ad configuration gadisadmanagerapp in info.plist: If yes is not configured, it will crash.

   ![&#x672A;&#x914D;&#x7F6E;Google&#x5E7F;&#x544A;ID](https://github.com/jieban0604/VigameDoc/tree/3e6ec92fbfeb594c2d6cc7a14fdca2834eb651ee/en/.gitbook/assets/1648908-10b02a368fa1b206.png)

Add as follows：

![&#x6DFB;&#x52A0;Google&#x5E7F;&#x544A;&#x914D;&#x7F6E;&#x65B9;&#x5F0F;](https://github.com/jieban0604/VigameDoc/tree/3e6ec92fbfeb594c2d6cc7a14fdca2834eb651ee/en/.gitbook/assets/1648908-89539912206f3690.png)

1. Due to the use of Xib for automatic layout of Google ads, the minimum version of IOS 9 will report the following errors ![&#x7CFB;&#x7EDF;&#x7248;&#x672C;&#x592A;&#x4F4E;&#x62A5;&#x9519;](https://github.com/jieban0604/VigameDoc/tree/3e6ec92fbfeb594c2d6cc7a14fdca2834eb651ee/en/.gitbook/assets/1648908-60441f51b86e81a6.png)

2. Modify the game to support IOS version to at least IOS 9 ![&#x8BBE;&#x7F6E;iOS&#x6700;&#x4F4E;&#x652F;&#x6301;9](https://github.com/jieban0604/VigameDoc/tree/3e6ec92fbfeb594c2d6cc7a14fdca2834eb651ee/en/.gitbook/assets/1648908-e94d66e37fb2142e.png)

3. Missing include file configuration error

   ![&#x7F3A;&#x5C11;&#x914D;&#x7F6E;&#x9519;&#x8BEF;](https://github.com/jieban0604/VigameDoc/tree/3e6ec92fbfeb594c2d6cc7a14fdca2834eb651ee/en/.gitbook/assets/1648908-cf447bd6d14c7a26.png)

Solution：

![&#x6DFB;&#x52A0;include&#x5F15;&#x7528;](https://github.com/jieban0604/VigameDoc/tree/3e6ec92fbfeb594c2d6cc7a14fdca2834eb651ee/en/.gitbook/assets/1648908-933ec652fe73bbd7.png)

1. The introduction error of boost file in include is missing

   ![&#x7F3A;&#x5C11;boost&#x5F15;&#x5165;&#x9519;&#x8BEF;](https://github.com/jieban0604/VigameDoc/tree/3e6ec92fbfeb594c2d6cc7a14fdca2834eb651ee/en/.gitbook/assets/1648908-5f38236e86b5d8e8.png)

Solution：

![&#x6DFB;&#x52A0;boost&#x5F15;&#x7528;](https://github.com/jieban0604/VigameDoc/tree/3e6ec92fbfeb594c2d6cc7a14fdca2834eb651ee/en/.gitbook/assets/1648908-a4fce67fdbbba4ef.png)

1. **weak typeof\(self\)wSelf = self error：- A parameter list without types is only allowed in a function definition. A corresponding warning tells me that** weak only applies to Objective-C object or block pointer types;type here is 'int'

Solution: Xcode－&gt; Build Settings-&gt; C Language Dialect  Modify configuration，C99--GNU99，C99  does not contain typeof

## 7. Confirm C + + compiler

![](https://github.com/jieban0604/VigameDoc/tree/3e6ec92fbfeb594c2d6cc7a14fdca2834eb651ee/en/.gitbook/assets/2183351-cb8d2dc8d55a615c.png)

If it is not set, the following error will be reported

![D970B31A66A9D0CC47F120ECE3C4F362.jpg](https://github.com/jieban0604/VigameDoc/tree/3e6ec92fbfeb594c2d6cc7a14fdca2834eb651ee/en/.gitbook/assets/1648908-dc7dca47a865b797.jpg)

## 8. Set project to ARC

![&#x8BBE;&#x7F6E;ARC](https://github.com/jieban0604/VigameDoc/tree/3e6ec92fbfeb594c2d6cc7a14fdca2834eb651ee/en/.gitbook/assets/2183351-ff19eccac2bf6326.png.jpeg) ![&#x8BBE;&#x7F6E;.png](https://github.com/jieban0604/VigameDoc/tree/3e6ec92fbfeb594c2d6cc7a14fdca2834eb651ee/en/.gitbook/assets/1648908-2b663a3c58c6a41b.png)

## 9. Access wechat configuration（No access ignore）

Add in info.plist file

![](https://github.com/jieban0604/VigameDoc/tree/3e6ec92fbfeb594c2d6cc7a14fdca2834eb651ee/en/.gitbook/assets/1648908-3b9d2adf2506a9a7.jpg)

Add wechat  URL Type

![](https://github.com/jieban0604/VigameDoc/tree/3e6ec92fbfeb594c2d6cc7a14fdca2834eb651ee/en/.gitbook/assets/1648908-7aa347ae8a163c04.png)

## 10. SDK initialization

**1. Import header file**

Introduce header file in appdelegate file `#import "IOSLoader.h"`

**2. Call initialization entry file**

```objective-c
- (BOOL)application:(UIApplication *)application willFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    [IOSLoader splashReport];
    return YES;
}

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    [IOSLoader startLoaderLibrary];
    return YES;
}

- (BOOL)application:(UIApplication *)application continueUserActivity:(NSUserActivity *)userActivity restorationHandler:(void (^)(NSArray<id<UIUserActivityRestoring>> * _Nullable))restorationHandler {

    if (userActivity.activityType == NSUserActivityTypeBrowsingWeb) {
    [IOSLoader application:application continueUserActivity:userActivity];
    return YES;
    }
    return NO;
}

- (void)applicationDidEnterBackground:(UIApplication *)application {
    [IOSLoader is_Active:false];
}

- (void)applicationWillEnterForeground:(UIApplication *)application {
   [IOSLoader isAwaken];
}

- (void)applicationDidBecomeActive:(UIApplication *)application {
    [IOSLoader is_Active:true]; 
     [IOSLoader openAwakenAd];
}

-(BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<UIApplicationOpenURLOptionsKey,id> *)options {
    [IOSLoader isOpenURL];
    return YES;
}
```

## Interaction process

1. We provide a test package name and certificate (for the projects that have been launched, in order to be able to advertise)
2. Use the test package name and certificate to create a test package -- then test
3. After the test, change the official package name and certificate, and upload the official package to Apple store.

