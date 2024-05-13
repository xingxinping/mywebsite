---
title: "sku"
date: 2024-05-10T10:45:48+08:00
draft: false
---
## 分页查询商家商品sku基础信息列表

> BASIC

**Path:** /seller/202405/product/sku/base-list

**Method:** POST

> REQUEST


**Request Body:**

| name                | required | type    | desc                    | example    |
|---------------------|----------|---------|-------------------------|------------|
| size                | NO       | integer | 每页条数 默认 20，max 200      | 20         |
| page                | NO       | string  | 第几页 默认 1                | 1          |
| state               | NO       | object  | 状态 0 下架 1 上架 9待上架 99已归档 | 1          |
| skuList             | NO       | array   | wahool sku列表            |
| &ensp;&ensp;&#124;─ | NO       | string  | wahool sku              | WU66ECPM8B |
| sellerSkuList       | NO       | array   | 商家自己的SKU列表              |
| &ensp;&ensp;&#124;─ | NO       | string  | 商家自己的SKU                | B0CQ4JNC58 |

**Request Demo:**

```json
{
  "state": 1,
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

| name                                                 | type    | desc                    | example        |
|------------------------------------------------------|---------|-------------------------|----------------|
| code                                                 | integer | 响应状态码                   | 200            |
| message                                              | string  | 提示信息                    | success        |
| data                                                 | object  | 数据包                     |                |
| &ensp;&ensp;&#124;─data                              | array   | 数据项                     |                |
| &ensp;&ensp;&ensp;&ensp;&#124;─                      | object  |                         |                |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─sku       | string  | wahool Sku              | WU66ECPM8B     |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─sellerSku | string  | 商家自己的Sku                | B0CQ4JNC58     |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─name      | string  | 商品名称                    | XX-Large Black |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─state     | integer | 状态 0 下架 1 上架 9待上架 99已归档 | 1              |
| &ensp;&ensp;&#124;─total                             | integer | 总条数                     | 8              |
| &ensp;&ensp;&#124;─totalPage                         | integer | 总页数                     | 1              |
| &ensp;&ensp;&#124;─size                              | integer | 分页大小                    | 20             |
| &ensp;&ensp;&#124;─currentPage                       | integer | 当前页                     | 1              |
| locale                                               | integer |                         | 8              |
| localeDisplay                                        | string  |                         | GMT+8          |
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
        "name": "XX-Large Black",
        "state": 1
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



