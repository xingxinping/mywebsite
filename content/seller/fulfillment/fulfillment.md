---
title: "履约订单"
date: 2024-05-10T10:45:48+08:00
draft: false
---

### 说明
>商家履约订单相关接口


---
## 分页查询商家未履约订单
特殊说明:返回所有未履约订单，商家调用发货api后则不再返回
> BASIC

**Path:** /seller/202405/fulfillment/fulfillment-orders/unfulfilled-list

**Method:** GET

> REQUEST

**Query:**

| name | required | desc               | example |
|------|----------|--------------------|---------|
| size | NO       | 每页条数 默认 20，max 200 | 20      |
| page | NO       | 第几页 默认 1           | 1       |



> RESPONSE

**Body:**

| name                                                                         | type    | desc                  | example         |
|------------------------------------------------------------------------------|---------|-----------------------|-----------------|
| code                                                                         | integer | 响应状态码                 | 200             |
| message                                                                      | string  | 提示信息                  | success         |
| data                                                                         | object  | 数据包                   |                 |
| &ensp;&ensp;&#124;─data                                                      | array   | 数据项                   |                 |
| &ensp;&ensp;&ensp;&ensp;&#124;─                                              | object  |                       |                 |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─fulfillmentOrderNumber            | string  | 履约单号                  | 1231154465      |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─state                             | integer | 状态 0未发货 10已发货 9履约单已取消 | 0               |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─address                           | object  | 地址                    |                 |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─consignee             | string  | 收件人姓名                 | hall            |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─phone                 | string  | 联系电话                  | 21111111111     |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─address1              | string  | 地址1                   | 1234 amazon way |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─address2              | string  | 地址2                   | suite 123       |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─city                  | string  | 城市                    | Troy            |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─stateProvince         | string  | 州编码或者省份               | MI              |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─postalCode            | string  | 邮编                    | 48084           |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─countryCode           | string  | 国家code                | US              |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─fulfillmentOrderItems             | array   | 履约单商品List             |                 |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─                      | object  |                       |                 |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─sku       | string  | wahool Sku            | WU66ECPM8B      |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─sellerSku | string  | 商家自己的Sku              | B0CQ4JNC58      |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─quantity  | integer | 商品数量                  | 3               |
| &ensp;&ensp;&#124;─total                                                     | integer | 总条数                   | 8               |
| &ensp;&ensp;&#124;─totalPage                                                 | integer | 总页数                   | 1               |
| &ensp;&ensp;&#124;─size                                                      | integer | 分页大小                  | 20              |
| &ensp;&ensp;&#124;─currentPage                                               | integer | 当前页                   | 1               |
| locale                                                                       | integer |                       |
| localeDisplay                                                                | string  |                       |
**Response Demo:**

```json
{
  "code": 200,
  "message": "success",
  "data": {
    "data": [
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
        "fulfillmentOrderItems": [
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

| name                                                 | type    | desc                  | example         |
|------------------------------------------------------|---------|-----------------------|-----------------|
| code                                                 | integer | 响应状态码                 | 200             |
| message                                              | string  | 提示信息                  | success         |
| data                                                 | object  | 数据包                   |                 |
| &ensp;&ensp;&#124;─fulfillmentOrderNumber            | string  | 履约单号                  | 1231154465      |
| &ensp;&ensp;&#124;─state                             | integer | 状态 0未发货 10已发货 9履约单已取消 | 0               |
| &ensp;&ensp;&#124;─address                           | object  | 地址                    |                 |
| &ensp;&ensp;&ensp;&ensp;&#124;─consignee             | string  | 收件人姓名                 | hall            |
| &ensp;&ensp;&ensp;&ensp;&#124;─phone                 | string  | 联系电话                  | 21111111111     |
| &ensp;&ensp;&ensp;&ensp;&#124;─address1              | string  | 地址1                   | 1234 amazon way |
| &ensp;&ensp;&ensp;&ensp;&#124;─address2              | string  | 地址2                   | suite 123       |
| &ensp;&ensp;&ensp;&ensp;&#124;─city                  | string  | 城市                    | Troy            |
| &ensp;&ensp;&ensp;&ensp;&#124;─stateProvince         | string  | 州编码或者省份               | MI              |
| &ensp;&ensp;&ensp;&ensp;&#124;─postalCode            | string  | 邮编                    | 48084           |
| &ensp;&ensp;&ensp;&ensp;&#124;─countryCode           | string  | 国家code                | US              |
| &ensp;&ensp;&#124;─fulfillmentOrderItems             | array   | 履约单商品List             |                 |
| &ensp;&ensp;&ensp;&ensp;&#124;─                      | object  |                       |                 |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─sku       | string  | wahool Sku            | WU66ECPM8B      |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─sellerSku | string  | 商家自己的Sku              | B0CQ4JNC58      |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─quantity  | integer | 商品数量                  | 3               |
| locale                                               | integer |                       | 0               |
| localeDisplay                                        | string  |                       |                 |


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

| name                                                | required | type       | desc       | example            |
|-----------------------------------------------------|----------|------------|------------|--------------------|
| fulfillmentOrderNumber                                  | YES      |  string    | 履约单号      | 123456             |
| fulfillmentShipmentPackages                       | YES      |array    | 发货包裹list   |                    |
| &ensp;&ensp;&#124;─                                 | YES      |object   |            |                    |
| &ensp;&ensp;&ensp;&ensp;&#124;─carrierCode          | YES      |string   | 物流公司       | UPS                |
| &ensp;&ensp;&ensp;&ensp;&#124;─trackingNumber       | YES      |string   | 物流单号       | 1Z9999W99999999999 |
| &ensp;&ensp;&ensp;&ensp;&#124;─shipmentItems      | YES      |array    | 包裹商品       |                    |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─         | YES      |object   |            |                    |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─sku      | YES      |string   | wahool sku | WU66ECPM8B         |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─quantity | YES      |integer  | 数量         | 2                  |

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
| locale        | integer |       | 0       |
| localeDisplay | string  |       |         |

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
## 分页查询需要拦截发货的履约订单

> BASIC

**Path:** /seller/202405/fulfillment/fulfillment-orders/intercept-shipped-list

**Method:** GET

> REQUEST

**Query:**

| name | required | desc               | example |
|------|----------|--------------------|---------|
| size | NO       | 每页条数 默认 20，max 200 | 20      |
| page | NO       | 第几页 默认 1           | 1       |



> RESPONSE

**Body:**

| name                                                 | type    | desc                  | example         |
|------------------------------------------------------|---------|-----------------------|-----------------|
| code                                                 | integer | 响应状态码                 | 200             |
| message                                              | string  | 提示信息                  | success         |
| data                                                 | object  | 数据包                   |                 |
| &ensp;&ensp;&#124;─fulfillmentOrderNumber            | string  | 履约单号                  | 1231154465      |
| &ensp;&ensp;&#124;─state                             | integer | 状态 0未发货 10已发货 9履约单已取消 | 9               |
| &ensp;&ensp;&#124;─address                           | object  | 地址                    |                 |
| &ensp;&ensp;&ensp;&ensp;&#124;─consignee             | string  | 收件人姓名                 | hall            |
| &ensp;&ensp;&ensp;&ensp;&#124;─phone                 | string  | 联系电话                  | 21111111111     |
| &ensp;&ensp;&ensp;&ensp;&#124;─address1              | string  | 地址1                   | 1234 amazon way |
| &ensp;&ensp;&ensp;&ensp;&#124;─address2              | string  | 地址2                   | suite 123       |
| &ensp;&ensp;&ensp;&ensp;&#124;─city                  | string  | 城市                    | Troy            |
| &ensp;&ensp;&ensp;&ensp;&#124;─stateProvince         | string  | 州编码或者省份               | MI              |
| &ensp;&ensp;&ensp;&ensp;&#124;─postalCode            | string  | 邮编                    | 48084           |
| &ensp;&ensp;&ensp;&ensp;&#124;─countryCode           | string  | 国家code                | US              |
| &ensp;&ensp;&#124;─fulfillmentOrderItems             | array   | 履约单商品List             |                 |
| &ensp;&ensp;&ensp;&ensp;&#124;─                      | object  |                       |                 |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─sku       | string  | wahool Sku            | WU66ECPM8B      |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─sellerSku | string  | 商家自己的Sku              | B0CQ4JNC58      |
| &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&#124;─quantity  | integer | 商品数量                  | 3               |
| locale                                               | integer |                       | 0               |
| localeDisplay                                        | string  |                       |                 |


**Response Demo:**

```json
{
  "code": 200,
  "message": "success",
  "data": {
    "fulfillmentOrderNumber": "1231154465",
    "state": 9,
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
| locale        | integer |       | 0       |
| localeDisplay | string  |       |         |

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


