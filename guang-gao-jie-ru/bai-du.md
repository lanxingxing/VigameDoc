# 百度

## 模块引入

```text
	implementation 'com.libVigame.AD:BaiduMob:2.3.7_temp2'  (带MobVisita用）
	和
    implementation 'com.libVigame.AD2:BaiduMob:2.3.7_temp2'  （不带MobVisita用）
```

## 注意事项
```text
    普通插屏广告有卡死可能，因此发布临时版本
```

## 混淆过滤
```text
-keepclassmembers	class *	extends	android.app.Activity{ public void *(android.view.View);	}

-keepclassmembers	enum *{public static **[] values(); public static ** valueOf(java.lang.String);	}

-keep class com.baidu.mobads.*.** {	*; }
```

## 集成测试

如何判断sdk是否初始化成功？

通过Baidu或者ADLog过滤日志查看广告状态，或者直接通过弹出的广告进行判断