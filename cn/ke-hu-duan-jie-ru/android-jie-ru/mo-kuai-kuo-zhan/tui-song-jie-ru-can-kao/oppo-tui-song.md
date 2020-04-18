# OPPO推送

## 模块引入

```text
xxx_Implementation WB.fixVersions('Push:Oppo')
```

## 添加混淆

```text
# OPPO 推送
-dontwarn com.coloros.mcssdk.**
-keep class com.coloros.mcssdk.** { *; }
```

## 注意事项

```text
确保包名、参数正确，AppKey，AppSecret是配置在 feedata_oppo.xml 中的
```

