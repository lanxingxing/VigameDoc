# Google国内

## 模块引入
1.采用本地导入的方式，将libAD_GoogleCN当做一个module引入你的工程当中
2.在app的build.gardle的dependencies前加入如下代码：
```text
    repositories {
        flatDir {
            dirs 'libs'
            dirs project(':libAD_GoogleCN').file('libs')
        }
    }
```
3.在app的build.gardle的dependencies中加入以下代码
```text
    implementation project(':libAD_GoogleCN')
        fileTree(dir: 'libs', include: ['*.aar']).each { file ->
            api(name: file.name.lastIndexOf('.').with {
                it != -1 ? file.name[0..<it] : file.name
            }, ext: 'aar')
        }
```
## 注意事项

  当打包结束的时候，建议把build.gradle中加入的代码注释掉，以免接其他渠道的时候还带了google广告的代码

## 混淆过滤

```text
-keep class * extends java.util.ListResourceBundle {
    protected java.lang.Object[][] getContents();
}
-keep public class com.google.android.gms.common.internal.safeparcel.SafeParcelable {
    public static final *** NULL;
}
-keepclassmembers enum * {
  public static **[] values();
  public static ** valueOf(java.lang.String);
}
-keepnames @com.google.android.gms.common.annotation.KeepName class *
-keepclassmembernames class * {
    @com.google.android.gms.common.annotation.KeepName *;
}
-keepnames class * implements android.os.Parcelable {
    public static final ** CREATOR;
}
-keep class * extends java.util.ListResourceBundle {
    protected java.lang.Object[][] getContents();
}
-keep class com.google.android.gms.ads.** {*;}
-keep class com.google.android.gms.common.** {*;}
-dontwarn com.google.android.gms.**
-dontwarn com.google.protobuf.**
-keep class com.google.ads.mediation.** {*;}
-dontwarn com.google.ads.mediation.**
```

## 集成测试

如何判断sdk是否初始化成功？

通过GoogleADAgent或者ADLog过滤日志查看广告状态，或者直接通过弹出的广告进行判断

