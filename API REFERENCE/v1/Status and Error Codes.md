### Status and Error Codes

---

here

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| query | String | 文本自然语言 \(&lt;=255 char\) | Required |
| sessionId | String | 用于区分client并为其管理上下文信息 \(&lt;=128 char\) | Required |
| agentId | String | 应用唯一凭证 \(&lt;=64 char\) | Required |
| token | String | 访问凭证 \(&lt;=64 char\) | Required |
| contexts | String | Context对象数组，若client输入上文，替换server上文 | Optional |
| location | String | Location对象，可以包含经纬度以及详细地址 | Optional |

---

_Sample Response_

```
{
    "code":400,
    "errorType":"bad_request",
    "errorDetails":"token校验不通过"
}
```




