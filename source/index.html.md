---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
toc_footers:
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Kitchen API!This guide describes how to compose and send commands and queries to the IOT platform using the Kitchen REST API. The guide provides examples for a set of common tasks, but it does not describe how to configure the full feature set of the Kitchen Application and it does not list the classes, methods of the API
.We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


# Subscription and Unsubscription

## Subscription

```shell
curl "http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/subscribe_device?appeui=0220731000000127&deveui=d02544fffef42720&access_token=19f5ad9e-bf82-493e-aef0-d09daac5522"
```
> The above command returns JSON structured like this:

```json
{
"appeui": "0220731000000127",
"deviceeui": "d02544fffef42720",
"thingplug_resp": 201,
"status": "Success"
}
{
"appeui": "0220731000000127",
"deviceeui": "d02544fffef42720",
"thingplug_resp": 409,
"status": "Fail,Please check thingplug response code"
}

{
"appeui": "02207310000001271",
"deviceeui": " d02544fffef42720",
"thingplug_resp": 0,
"status": "Fail:appeui/deveui length/format is wrong"
}

{
"error": "unauthorized",
"error_description": "An Authentication object was not found in the SecurityContext"
}

```
This api UnSubscribe  kitchen device 

### HTTP Request

`POST  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/subscribe_device?appeui={appeui}&deveui={deveui}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
appeui | Application eui of the device.
deveui | Device eui of the device.
access_token | Access token to be used with api.


<aside class="success">
Remember — acess_token is an access token to be used only if authentication is enabled!
</aside>

## Unsubscription

```shell
curl "http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/unsubscribe_device?appeui=0220731000000127&deveui=d02544fffef42720&access_token=19f5ad9e-bf82-493e-aef0-d09daac5522"

```
> The above command returns JSON structured like this:

```json
{
"appeui": "0220731000000127",
"deviceeui": "d02544fffef42720",
"thingplug_resp": 200,
"status": "Success"
}

{
"appeui": "02207310000001271",
"deviceeui": " d02544fffef42720",
"thingplug_resp": 0,
"status": "Fail:appeui/deveui length/format is wrong"
}


```

This API UnSubscribe  kitchen device.
<aside class="warning">Unsubscribed devices have to be resubscribed to recieve data</aside>


### HTTP Request

`DELETE  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/unsubscribe_device?appeui={appeui}&deveui={deveui}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- |  -----------
appeui | Application eui of the device.
deveui | Device eui of the device.
access_token | Access token to be used with api.

# Device Information

## device Latest data

```shell
curl "http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/getkitchendata?appeui=0220731000000127&deveui=d02544fffef4bd1d &access_token=19f5ad9e-bf82-493e-aef0-d09daac55222"
```
> The above command returns JSON structured like this:

```json
{
"kitchenlatestdeviceinfo":{
"receive_time": "2017-09-28 13:57:10",
"app_eui": "0220731000000127",
"version": "0.3.2 ",
"device_id": "d02544fffef4bd20",
"seq": 4764,
"resistance": 527,
"tvoc": 19,
"temperature": 19115,
"humidity": 16568,
"status": 31,
"created_at": "2017-09-28 13:57:10.040528",
"ct": "2017-09-28 13:57:08",
"lt": "2017-09-28 13:57:08",
"cs": 50,
"temp_threshold": 50,
"fw_ver": "0.3.2 "
},
"status": "Success"
}

{
"kitchenlatestdeviceinfo": null,
"status": "Fail,appeui/deveui length/format is wrong"
}


```
Get Device latest information

### HTTP Request

`POST  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/getkitchendata/latest?appeui={appeui}&deveui={deveui}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
appeui | Application eui of the device.
deveui | Device eui of the device.
access_token | Access token to be used with api.
