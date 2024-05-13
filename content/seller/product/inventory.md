---
title: "库存"
date: 2024-05-10T10:45:48+08:00
draft: false
---

## 批量修改库存数量

> BASIC

**Path:** /seller/202405/product/inventory/batch-update

**Method:** POST

> REQUEST



**Request Body:**

| name                        | required | type    | desc       | example    |
|-----------------------------|----------|---------|------------|------------|
|                             | YES      | array   |            |            |
|                             | YES      | object  |            |            |
| &ensp;&ensp;&#124;─sku      | YES      | string  | wahool Sku | WU66ECPM8B |
| &ensp;&ensp;&#124;─quantity | YES      | integer | 库存数量       | 2          |

**Request Demo:**

```json
[
  {
    "sku": "WU66ECPM8B",
    "quantity": 2
  }
]
```



> RESPONSE


**Body:**

| name          | type    | desc  | example |
|---------------|---------|-------|---------|
| code          | integer | 响应状态码 | 200     |
| message       | string  | 提示信息  | success |
| data          | object  | 数据包   |         |
| locale        | integer |       | 8       |
| localeDisplay | string  |       | GMT+8   |

**Response Demo:**

```json
{
  "code": 200,
  "message": "success",
  "data": {},
  "locale": 0,
  "localeDisplay": ""
}
```




---
## 分页查询库存列表

> BASIC

**Path:** /seller/202405/product/inventory/list

**Method:** POST

> REQUEST

**Request Body:**

| name                | required | type    | desc               | example    |
|---------------------|----------|---------|--------------------|------------|
| size                | NO       | integer | 每页条数 默认 20，max 200 | 20         |
| page                | NO       | string  | 第几页 默认 1           | 1          |
| skuList             | NO       | array   | wahool sku列表       |
| &ensp;&ensp;&#124;─ | NO       | string  | wahool sku         | WU66ECPM8B |
| sellerSkuList       | NO       | array   | 商家自己的SKU列表         |
| &ensp;&ensp;&#124;─ | NO       | string  | 商家自己的SKU           | B0CQ4JNC58 |

**Request Demo:**

```json
{
  "skuList": [
    "WU66ECPM8B"
  ],
  "sellerSkuList": [
    "B0CQ4JNC58"
  ],
  "size": 1,
  "page": 20
}
```



> RESPONSE


**Body:**

| name                                                 | type    | desc       |
|------------------------------------------------------|---------|------------|
| code                                                 | integer | 响应状态码      |
| message                                              | string  | 提示信息       |
| data                                                 | object  | 数据包        |
| &ensp;&ensp;&#124;─data                              | array   | 数据项        |
| &ensp;&ensp;&ensp;&ensp;&#124;─                      | object  |            |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─sku       | string  | wahool Sku |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─sellerSku | string  | 商家自己的Sku   |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─quantity  | integer | 库存数量       |
| &ensp;&ensp;&#124;─total                             | integer | 总条数        |
| &ensp;&ensp;&#124;─totalPage                         | integer | 总页数        |
| &ensp;&ensp;&#124;─size                              | integer | 分页大小       |
| &ensp;&ensp;&#124;─currentPage                       | integer | 当前页        |
| locale                                               | integer |            |
| localeDisplay                                        | string  |            |

**Response Demo:**

```json
{
  "code": 200,
  "message": "success",
  "data": {
    "data": [
      {
        "sku": "WU66ECPM8B",
        "sellerSku": "B0CQ4JNC58",
        "quantity": 0
      }
    ],
    "total": 8,
    "totalPage": 1,
    "size": 20,
    "currentPage": 1
  },
  "locale": 0,
  "localeDisplay": ""
}
```



