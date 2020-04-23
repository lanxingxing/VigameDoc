---
description: 目前只在Oppo、Vivo小游戏平台有效
---

# 原生广告

## dnsdk.getNativeAd\(\)

获取原生广告数据。

### 返回值

NativeAd广告组件

> 注意：当没有可用原生广告时，会返回null

## NativeAd

原生广告

### NativeAd.show\(\)

广告展示后调用。内部会自动触发平台的reportAdShow接口。

### NativeAd.click\(\)

用户点击广告后调用。内部会自动触发平台的reportAdClick接口。

### NativeAd.close\(\)

用户关闭广告后调用。用于后续广告的预加载。



