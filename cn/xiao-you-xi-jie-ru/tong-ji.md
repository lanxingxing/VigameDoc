# 统计

### 1.自定义事件统计

方法接口：

```text
dnsdk.tjSendEvent(eventId, object);
```

参数说明：

| 参数 | 描述 | 参数类型 | 长度 | 是否必传 |
| :--- | :--- | :--- | :--- | :--- |
| eventId | 事件名称 | String | 不超过255个字符 | 是 |
| object | 事件参数 | Object |  | 是 |

示例代码：

```javascript
dnsdk.tjSendEvent('事件名称',{'参数key' : '参数value'})
```

### 2.关卡统计

> 此接口用于追踪玩家对关卡的完成情况等

方法接口：

```javascript
//关卡开始
dnsdk.tjOnStart(object)
//关卡进行中
dnsdk.tjOnRunning(object)
//关卡结束
dnsdk.tjOnEnd(object)
```

#### dnsdk.tjOnStart关卡开始

| 参数 | 描述 | 参数类型 | 规则 | 是否必传 |
| :--- | :--- | :--- | :--- | :--- |
| stageId | 关卡ID | String | 1 , 2 , 3 , 1.1 , 1.2 , 1.3 格式 最多支持 32 个字符 | 是 |
| stageName | 关卡名称 | String | 最多支持 32 个字符 | 是 |
| userId | 用户名称 | String | 最多支持 32 个字符 | 否 |

示例代码：

```javascript
dnsdk.tjOnStart({
  stageId : "1.1", //关卡ID， 必须是1 || 2 || 1.1 || 12.2 格式  该字段必传
  stageName : "第一大关-第一小关",//关卡名称，该字段必传
  userId  : "123456" //用户ID
})
```

#### dnsdk.tjOnRunning捕捉用户在关卡中的一些行为和操作

| 参数 | 描述 | 参数类型 | 规则 | 是否必传 |
| :--- | :--- | :--- | :--- | :--- |
| stageId | 关卡ID | String | 1 , 2 , 3 , 1.1 , 1.2 , 1.3 格式 最多支持 32 个字符 | 是 |
| stageName | 关卡名称 | String | 最多支持 32 个字符 | 是 |
| userId | 用户名称 | String | 最多支持 32 个字符 | 否 |
| event | 时间类型 | String | payStart:发起支付 paySuccess:支付成功 payFail:支付失败 tools:使用道具 revive:复活 award:奖励 | 否 |
| params | 事件参数 | Object | 否 |  |
| params.itemName | 商品/道具名称 | String | “屠龙刀” | 是 |
| params.itemId | 商品/道具ID    String | "123" | 否 |  |
| params.itemCount | 商品/道具数量 | Number | 1 | 否 默认:1 |
| params.desc | 描述 | String | “+9屠龙刀” | 否 |
| params.itemMoney | 商品/道具价格 | Number | 12 | 否 默认:0 |

示例代码：

```javascript
// 在关卡中使用道具
dnsdk.tjOnRunning({
  stageId : "1.1",
  stageName : "第一大关-第一小关",
  userId : "123456",
  event : "tools",
  params : {
    itemName : "火力加强",

  }
})
```

#### dnsdk.tjOnEnd 关卡结束

| 参数 | 描述 | 参数类型 | 规则 | 是否必传 |  |
| :--- | :--- | :--- | :--- | :--- | :--- |
| stageId | 关卡ID | String | 1 , 2 , 3 , 1.1 , 1.2 , 1.3 格式 | 最多支持 32 个字符 | 是 |
| stageName | 关卡名称 | String | 最多支持 32 个字符 | 是 |  |
| userId | 用户ID | String | 最多支持 32 个字符 | 否 |  |
| event | 事件类型 | String | complete:关卡完成 fail:关卡失败 | 是 |  |
| params | 事件参数 | Object |  |  |  |
| params.desc | 描述 | String | 对关卡失败/成功的描述 | 否 |  |

示例代码：

```javascript
//关卡完成
dnsdk.tjOnEnd({
  stageId : "1",    //关卡ID 该字段必传
  stageName : "第一关", //关卡名称  该字段必传
  userId : "06_bmjrPtlm6_2sgVt7hMZOPfL2M",  //用户ID 可选
  event : "complete",   //关卡完成  关卡进行中，用户触发的操作    该字段必传
  params : {
    desc : "关卡完成"   //描述
  }
})
```

