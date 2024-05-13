---
title: "履约订单"
date: 2024-05-10T10:45:48+08:00
draft: false
---

## 分页查询商家履约订单
特殊说明:返回所有待履约/待拦截发货的订单，商家处理后状态发生改变则不再返回
> BASIC

**Path:** /seller/202405/fulfillment/orders/list

**Method:** GET

> REQUEST

**Query:**

| name       | required | desc                                                     | example     |
|------------|----------|----------------------------------------------------------|-------------|
| size       | NO       | 每页条数 默认 20，max 200                                       | 20          |
| page       | NO       | 第几页 默认 1                                                 | 1           |
| queryState | YES      | 查询状态<br>UNFULFILLED :待履约<br>INTERCEPT_SHIPPED :待拦截发货<br> | UNFULFILLED |




> RESPONSE

**Body:**

| name                            | type                     | desc  | example |
|---------------------------------|--------------------------|-------|---------|
| code                            | integer                  | 响应状态码 | 200     |
| message                         | string                   | 提示信息  | success |
| data                            | object                   | 数据包   |         |
| &ensp;&ensp;&#124;─ list        | List<`FulfillmentOrder`> | 数据项   |         |
| &ensp;&ensp;&#124;─ total       | integer                  | 总条数   | 8       |
| &ensp;&ensp;&#124;─ totalPage   | integer                  | 总页数   | 1       |
| &ensp;&ensp;&#124;─ size        | integer                  | 分页大小  | 20      |
| &ensp;&ensp;&#124;─ currentPage | integer                  | 当前页   | 1       |
| locale                          | integer                  |       | 8       |
| localeDisplay                   | string                   |       | GMT+8   |

#### ```FulfillmentOrder```
| name                   | type              | desc                   | example    |
|------------------------|-------------------|------------------------|------------|
| fulfillmentOrderNumber | String            | 履约单号                   | 1231154465 |
| state                  | Integer           | 0未发货 20已发货 90已取消	 | 0          |
| address                | Object<`Address`> | 收货地址                   | -          |
| items                  | Object<`Items`>   | 履约商品                   | -          |


#### ```Address```
| name          | required | desc   | example         |
|---------------|----------|--------|-----------------|
| consignee     | String   | 收件人    | Matt            |
| phone         | String   | 联系电话   | +11927361822    |
| address1      | String   | 地址1    | 1234 amazon way |
| address2      | String   | 地址2    | suite 123       |
| address3      | String   | 地址3    | -               |
| address4      | String   | 地址4    | -               |
| city          | String   | 城市     | Troy            |
| stateProvince | String   | 州/省    | MI              |
| postalCode    | Integer  | 邮政编码   | 48084           |
| countryCode   | String   | 国家code | US              |


#### ```Items```
| name      | required | desc               | example |
|-----------|----------|--------------------|---------|
| sku       | string  | wahool Sku            | WU66ECPM8B      |
| sellerSku | string  | 商家自己的Sku              | B0CQ4JNC58      |
| quantity  | integer | 商品数量                  | 3               |



**Response Demo:**

```json
{
  "code": 200,
  "message": "success",
  "data": {
    "list": [
      {
        "fulfillmentOrderNumber": "1231154465",
        "state": 0,
        "address": {
          "consignee": "hall",
          "phone": "21111111111",
          "address1": "1234 amazon way",
          "address2": "suite 123",
          "city": "Troy",
          "stateProvince": "MI",
          "postalCode": "48084",
          "countryCode": "US"
        },
        "items": [
          {
            "sku": "WU66ECPM8B",
            "sellerSku": "B0CQ4JNC58",
            "quantity": 3
          }
        ]
      }
    ],
    "total": 8,
    "totalPage": 1,
    "size": 20,
    "currentPage": 1,
    "page": 1
  },
  "locale": 0,
  "localeDisplay": ""
}
```




---
## 查询履约单明细

> BASIC

**Path:** /seller/202405/fulfillment/fulfillment-orders/get/{fulfillmentOrderNumber}

**Method:** GET

> REQUEST

**Path Params:**

| name                   | required | desc | example    |
|------------------------|----------|------|------------|
| fulfillmentOrderNumber | YES      | 履约单号 | 1231154465 |


> RESPONSE

**Body:**

| name          | type                       | desc  | example |
|---------------|----------------------------|-------|---------|
| code          | integer                    | 响应状态码 | 200     |
| message       | string                     | 提示信息  | success |
| data          | Object<`FulfillmentOrder`> | 数据包   |         |
| locale        | integer                    |       | 8       |
| localeDisplay | string                     |       | GMT+8   |

#### ```FulfillmentOrder```
| name                   | type              | desc                   | example |
|------------------------|-------------------|------------------------|---------|
| fulfillmentOrderNumber | String            | 履约单号                   | -       |
| state                  | Integer           | 0未发货 20已发货 90已取消	 | 0       |
| address                | Object<`Address`> | 收货地址                   | -       |
| items                  | Object<`Items`>   | 履约商品                   | -       |


#### ```Address```
| name          | required | desc | example         |
|---------------|----------|------|-----------------|
| consignee     | String   | 收件人  | Matt            |
| phone         | String   | 联系电话 | +11927361822    |
| address1      | String   | 地址1  | 1234 amazon way |
| address2      | String   | 地址2  | suite 123       |
| address3      | String   | 地址3  | -               |
| address4      | String   | 地址4  | -               |
| city          | String   | 城市   | Troy            |
| stateProvince | String   | 州/省  | MI              |
| postalCode    | Integer  | 邮政编码 | 48084           |
| countryCode   | String   | 国家   | US              |


#### ```Items```
| name      | required | desc       | example    |
|-----------|----------|------------|------------|
| sku       | string   | wahool Sku | WU66ECPM8B |
| sellerSku | string   | 商家自己的Sku   | B0CQ4JNC58 |
| quantity  | integer  | 商品数量       | 3          |


**Response Demo:**

```json
{
  "code": 200,
  "message": "success",
  "data": {
    "fulfillmentOrderNumber": "1231154465",
    "state": 0,
    "address": {
      "consignee": "hall",
      "phone": "21111111111",
      "address1": "1234 amazon way",
      "address2": "suite 123",
      "city": "Troy",
      "stateProvince": "MI",
      "postalCode": "48084",
      "countryCode": "US"
    },
    "fulfillmentOrderItems": [
      {
        "sku": "WU66ECPM8B",
        "sellerSku": "B0CQ4JNC58",
        "quantity": 3
      }
    ]
  },
  "locale": 0,
  "localeDisplay": ""
}
```




---
## 商家发货

特殊说明:不支持部分发货、所有商品必须全部发货
> BASIC

**Path:** /seller/202405/fulfillment/fulfillment-orders/shipment

**Method:** POST

> REQUEST

**Request Body:**

| name                                                | required | type    | desc       | example            |
|-----------------------------------------------------|----------|---------|------------|--------------------|
| fulfillmentOrderNumber                              | YES      | string  | 履约单号       | 123456             |
| fulfillmentShipmentPackages                         | YES      | array   | 发货包裹list   |                    |
| &ensp;&ensp;&#124;─                                 | YES      | object  |            |                    |
| &ensp;&ensp;&ensp;&ensp;&#124;─carrierCode          | YES      | string  | 物流公司       | UPS                |
| &ensp;&ensp;&ensp;&ensp;&#124;─trackingNumber       | YES      | string  | 物流单号       | 1Z9999W99999999999 |
| &ensp;&ensp;&ensp;&ensp;&#124;─shipmentItems        | YES      | array   | 包裹商品       |                    |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─         | YES      | object  |            |                    |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─sku      | YES      | string  | wahool sku | WU66ECPM8B         |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─quantity | YES      | integer | 数量         | 2                  |

**Request Demo:**

```json
{
  "fulfillmentOrderNumber": "123456",
  "fulfillmentShipmentPackages": [
    {
      "carrierCode": "UPS",
      "trackingNumber": "1Z9999W99999999999",
      "shipmentItems": [
        {
          "sku": "WU66ECPM8B",
          "quantity": 3
        }
      ]
    },
    {
      "carrierCode": "FedEx",
      "trackingNumber": "123456789012",
      "shipmentItems": [
        {
          "sku": "WU66ECPM8B",
          "quantity": 3
        }
      ]
    }
  ]
}
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
## 商家履约反馈

> BASIC

**Path:** /seller/202405/fulfillment/fulfillment-orders/seller-fulfillment-feedback

**Method:** POST

> REQUEST


**Request Body:**

| name                   | required | type   | desc                                                                                                     | example      |
|------------------------|----------|--------|----------------------------------------------------------------------------------------------------------|--------------|
| fulfillmentOrderNumber | YES      | string | 履约单号                                                                                                     | 123456       |
| sellerFeedback         | YES      | string | 商家反馈类型<br>OUT_OF_STOCK :商家无货无法发出<br>INTERCEPT_SHIPPED_SUCCESS :拦截发货成功<br>INTERCEPT_SHIPPED_FAIL :拦截失败已发出 | OUT_OF_STOCK |

**Request Demo:**

```json
{
  "fulfillmentOrderNumber": "123456",
  "sellerFeedbackState": "OUT_OF_STOCK"
}
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


