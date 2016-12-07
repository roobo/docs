### Context {#context_1}

---


| Status Code | Error Type | Description |
| :--- | :--- | :--- |
| 0 | success | 成功 |
| 1 | no\_result | 无结果 |
| 400 | bad\_request | 不合法的输入 |
| 401 | unauthorized | 权限校验失败 |
| 500 | internal | 系统错误，重试可能有效 |
| 501 | not_supported | 语义 |
| 503 | too_many_requests | 在一定时间内访问次数超限 |
| 601 | service_unreachable | 第三方服务不可用 |
| 602 | service_unknown_format | 第三方服务返回的数据格式有误 |

---

_Sample Response_

```
{
    "code":400,
    "errorType":"bad_request",
    "errorDetails":"token校验不通过"
}
```



