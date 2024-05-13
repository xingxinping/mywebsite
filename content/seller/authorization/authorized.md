---
title: "授权"
date: 2024-05-10T10:45:48+08:00
draft: false
---


## 获取认证token接口

> BASIC

**Path:** /seller/202405/authorization

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
  "accessKey": "RjtQObU4DB3egXyAjiYO",
  "secretKey": "ddjY22igIqjeY0GtE8GUcRBtsQwOYYEGWFsoQb5u"
}
```

> RESPONSE

**Body:**

| name          | type           | desc  | example |
|---------------|----------------|-------|---------|
| code          | integer        | 响应状态码 | 200     |
| message       | string         | 提示信息  | success |
| data          | Object<`Data`> | 数据包   |         |
| locale        | integer        |       | 8       |
| localeDisplay | string         |       | GMT+8   |

**Data:**

| name        | type   | desc   | example                                             |
|-------------|--------|--------|-----------------------------------------------------|
| expiresIn   | integer | 有效期（秒） | 7200000                                             |
| accessToken | string | 访问令牌   | Bearer eyJ0dGxNaWx**************************gNDYzfQ |

**Response Demo:**

```json
{
  "code": 200,
  "message": "success",
  "data": {
    "accessToken": "Bearer eyJ0dGxNaWx**************************gNDYzfQ",
    "expiresIn": "7200000"
  },
  "locale": 8,
  "localeDisplay": "GMT+8"
}
```



