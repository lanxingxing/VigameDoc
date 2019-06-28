# Vungle

## 模块引入

```text
    implementation 'com.libVigame.AD:Vungle:2.1.6'
```

## 注意事项

```text
    无
```

## 混淆过滤

```text
# Vungle 
-keep class com.vungle.warren.** { *; } 
# Evernote 
-dontwarn com.evernote.android.job.gcm.** 
-dontwarn com.evernote.android.job.GcmAvailableHelper 
-dontwarn com.google.android.gms.ads.identifier.** 
-keep public class com.evernote.android.job.v21.PlatformJobService 
-keep public class com.evernote.android.job.v14.PlatformAlarmService 
-keep public class com.evernote.android.job.v14.PlatformAlarmReceiver 
-keep public class com.evernote.android.job.JobBootReceiver 
-keep public class com.evernote.android.job.JobRescheduleService 
-dontwarn org.codehaus.mojo.animal_sniffer.IgnoreJRERequirement 
-keep class com.google.android.gms.internal.** { *; } 
# Moat SDK 
-keep class com.moat.** { *; } 
-dontwarn com.moat.**
```

## 集成测试

如何判断sdk是否初始化成功？

通过VungleAgent或者ADLog过滤日志查看广告状态，或者直接通过弹出的广告进行判断

