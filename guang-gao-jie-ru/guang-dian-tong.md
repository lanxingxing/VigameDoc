# 广点通

## 模块引入

```text
	implementation 'com.libVigame.AD2:GDTUnion:2.4.3'
	和
    implementation 'com.libVigame.AD2:GDTUnion:2.4.3'
```

## 注意事项
```text
    无
```

## 混淆过滤

```text
 -keep class com.qq.e.** { 
        public protected *; 
    }
    -keep class android.support.v4.**{
        public *;
    }
    -keep class android.support.v7.**{
        public *;
    }
```

## 集成测试

如何判断sdk是否初始化成功？

通过GDT或者ADLog过滤日志查看广告状态，或者直接通过弹出的广告进行判断