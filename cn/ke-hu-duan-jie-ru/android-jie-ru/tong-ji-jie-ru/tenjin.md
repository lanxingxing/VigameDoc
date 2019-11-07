# Tenjin

## 模块引入

```text
    implementation 'com.libVigame.TJ:Tenjin:1.0.0'
```

## 混淆过滤

```text
-keep class com.tenjin.** { *; }-keep public class com.google.android.gms.ads.identifier.** { *; }-keep public class com.google.android.gms.common.** { *; }-keep public class com.android.installreferrer.** { *; }-keep class * extends java.util.ListResourceBundle {    protected Object[][] getContents();}-keepattributes *Annotation*
```

## 测试 引荐安装

```text
运行应用程序，然后在logcat中过滤 RFF tag,在命令行中先启动adb，然后输入命令： adb shell am broadcast -a com.android.vending.INSTALL_REFERRER -n <com.your.apppackage>/com.tenjin.android.TenjinReferrerReceiver --es "referrer" "ai=test&gclid=click_test"会在logcat中看到 ai=test&gclid=click_test 的输出注意 <com.your.apppackage> 替换成成包名 例如：adb shell am broadcast -a com.android.vending.INSTALL_REFERRER -n com.puzzle.game.hw/com.tenjin.android.TenjinReferrerReceiver --es "referrer" "ai=test&gclid=click_test"能看到日志正常输出
```

