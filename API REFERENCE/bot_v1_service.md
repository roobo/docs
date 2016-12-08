### /bot/v1/service

* [Overview](#overview)
* [URLs](#URLs)
* [Parameters and JSON Fields](#parameters)
* [Sample](#sample)

### Overview {#overview}
---
服务开放接口，开发者在意图和参数已知的情况，无需再通过自然语言处理，可直接调用相应的服务接口。

### URLs {#URLs}
---
| Method | Definition |
| :--- | :--- |
| POST /bot/v1/service/${service_name} | 调用service_name指定服务的接口，具体接口名称和接口参数通过JSON在请求体中指定 |

### Parameters and JSON Fields {#parameters}
---
#### 请求参数
| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| agentId | String | 应用唯一凭证 \(&lt;=64 char\) | Required |
| token | String | 访问凭证 \(&lt;=64 char\) | Required |
| function | String | 要调用的服务接口名称 | Required|
| sessionId | String | 用于区分client并为其管理上下文信息 \(&lt;=128 char\) | Optional |
| location | [Location](location.html#location_1) | Location对象，可以包含经纬度以及详细地址 | Optional |
| params | JSON Object | 接口所需调用参数的对象，字段描述见具体服务的接口说明 | Optional |

#### 响应参数
| Name | Type | Description |
| :--- | :--- | :--- | :--- |
| status | [Status](Status and Error Codes.md.html#status_1) | 成功失败信息 |
| result | JSON Object | 接口调用返回结果，字段描述见具体服务的接口说明 |

### 接口调用示例 {#post}
#### 请求数据
#### 响应数据