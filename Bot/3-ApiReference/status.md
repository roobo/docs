
## Status定义
返回结果状态标识，_code_ 是返回码，_errorType_ 是错误类型，_errorDetails_ 时候错误详情。

```
{
    "code":400,
    "errorType":"bad_request",
    "errorDetails":"token校验不通过"
}
```

| Status Code | Error Type | Description |
| :--- | :--- | :--- |
| 0 | success | 成功 |
| 1 | no\_result | 无结果 |
| 400 | bad\_request | 不合法的输入 |
| 401 | unauthorized | 权限校验失败 |
| 500 | internal | 系统错误，重试可能有效 |
| 501 | not\_supported | 语义 |
| 503 | too\_many\_requests | 在一定时间内访问次数超限 |
| 601 | service\_unreachable | 第三方服务不可用 |
| 602 | service\_unknown\_format | [第三方服务返回的数据格式有误] |
