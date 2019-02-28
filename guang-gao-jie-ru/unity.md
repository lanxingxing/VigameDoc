# unity

## 模块引入

```text
    implementation 'com.libVigame.AD:Unity:2.1.3'
```

## 注意事项

```text
    无
```

## 混淆过滤

```text
# Keep filenames and line numbers for stack traces
-keepattributes SourceFile,LineNumberTable

# Keep JavascriptInterface for WebView bridge
-keepattributes JavascriptInterface

# Sometimes keepattributes is not enough to keep annotations
-keep class android.webkit.JavascriptInterface {
   *;
}

# Keep all classes in Unity Ads package
-keep class com.unity3d.ads.** {
   *;
}

# Keep all classes in Unity Services package
-keep class com.unity3d.services.** {
   *;
}

-dontwarn com.google.ar.core.**
```

## 集成测试

如何判断sdk是否初始化成功？

通过UnityAgent或者ADLog查看广告的状态，或者直接通过弹出的广告进行判断

