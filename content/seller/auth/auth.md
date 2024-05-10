---
title: "认证"
date: 2024-05-10T10:45:48+08:00
draft: false
---

## 接口调用说明

> 用户方每次发起 http 请求时，需要在 http header 填入一个属性：
Authorization， Authorization 对应 用户获取认证token接口返回的accessToken。
Http request header 信息如下表格所示：


**Headers:**

| name          | value                                                                                                    | required | desc               |
|---------------|----------------------------------------------------------------------------------------------------------|----------|--------------------|
| Authorization | Bearer eyJ0dGxNaWxsaXMiOjcyMDAwMDAsIm9wZW5BY2NvdW50SWQiOjEsImlhdCI6MTcxNDk4MTI2MywiZXhwIjoxNzE0OTgNDYzfQ | Yes      | 认证接口返回的accessToken |


---
## 获取认证token接口

> BASIC

**Path:** /seller/202405/auth/get-access-token

**Method:** POST

> REQUEST

**Request Body:**

| name      | required | type   | desc | example                                  |
|-----------|----------|--------|------|------------------------------------------|
| accessKey | YES      | string |      | RjtQObU4DB3egXyAjiYO                     |
| secretKey | YES      | string |      | ddjY22igIqjeY0GtE8GUcRBtsQwOYYEGWFsoQb5u |

**Request Demo:**

```json

{
  "accessKey":"RjtQObU4DB3egXyAjiYO",
  "secretKey":"ddjY22igIqjeY0GtE8GUcRBtsQwOYYEGWFsoQb5u"
}
```



> RESPONSE

**Body:**

| name                           | type    | desc   | example                                                                                                  |
|--------------------------------|---------|--------|----------------------------------------------------------------------------------------------------------|
| code                           | integer | 响应状态码  | 200                                                                                                      |
| message                        | string  | 提示信息   | success                                                                                                  |
| data                           | object  | 数据包    |                                                                                                          |
| &ensp;&ensp;&#124;─accessToken | string  | 访问令牌   | Bearer eyJ0dGxNaWxsaXMiOjcyMDAwMDAsIm9wZW5BY2NvdW50SWQiOjEsImlhdCI6MTcxNDk4MTI2MywiZXhwIjoxNzE0OTgNDYzfQ |
| &ensp;&ensp;&#124;─expiresIn   | integer | 有效期（秒） | 7200000                                                                                                  |
| locale                         | integer |        | 8                                                                                                        |
| localeDisplay                  | string  |        | GMT+8                                                                                                    |

**Response Demo:**

```json
{
  "code": 200,
  "message": "success",
  "data": {
    "accessToken": "Bearer eyJhbGciOiJIUzUxMiJ9.eyJ0dGxNaWxsaXMiOjcyMDAwMDAsIm9wZW5BY2NvdW50SWQiOjEsImlhdCI6MTcxNDk5MTI5OSwiZXhwIjoxNzE0OTk4NDk5fQ.Nxad0qm7pvpxi9yW9ksqgC0HFTflnhYnggbHpRLY8CH1eOEF85-wWfVyngCmFmMOjoPQdD2oA3MSsC-nxxI_tA",
    "expiresIn": "7200000"
  },
  "locale": 8,
  "localeDisplay": "GMT+8"
}
```



