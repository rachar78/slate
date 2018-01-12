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

Welcome to the Keyco Crowd API!This guide describes how to compose and send commands and queries to the IOT platform using the keyco REST API. The guide provides examples for a set of common tasks, but it does not describe how to configure the full feature set of the keyco Finder crowd Application and it does not list the classes, methods of the API.We have language bindings in CURL! You can view code examples in the dark area to the right. 

# Device Information

## Get total keyco device count

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycodevicecount/' --data 'appeui=0220731000000127&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"total": 1523,
"status": "success"
}

{
"total": 0,
"status": "Fail,appeui length/format is wrong"
}

```
Get total no of of keyco devices count 

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycodevicecount?appeui={appeui}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
appeui | Application eui of the device.
access_token | access_token Access token to be used with api

## Get the user lists of specific device

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycodeviceuserlist/' --data 'appeui=0220731000000127& devicekey=995f9a9cb2d0ae26562cfbeb4f5b2c69598bc749&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"status": "Success",
"total": 2,
"listkeycouserinfo":[
{
"user_key": "1567c7a74d13f2441876b1f7558afaee4b249627",
"pin_code": "",
"user_name": "567034643",
"user_phone_num": "",
"phone_type": "Android",
"register_date": "2018-01-04 21:50:57",
"device_alias": "bruce office 1f0e",
"active_login": "1"
},
{
"user_key": "bd991840970e8005468094bb160e42845197b565",
"pin_code": "",
"user_name": "100439623793991393326,vudamalapati@gmail.com",
"user_phone_num": null,
"phone_type": "Android",
"register_date": "2017-12-30 12:19:40",
"device_alias": "bala-office2",
"active_login": "0"
}
]
}

```
Get the keyco user lists of specific device

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycodeviceuserlist?{appeui}&devicekey={devicekey}&access_token={access_token`

### Query Parameters

Parameter | Description
--------- | ------------
appeui | Application eui of the device.
devicekey | Device key of the device
access_token | access_token Access token to be used with api

## Get keyco device lists of specific user

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycouserdevicelist/' --data 'userkey=8f9e211ed7eb7f5cdf9712b8a78539d8754a73f0&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"status": "Success",
"total": 1,
"listkeycodeviceinfo":[
{
"device_key": "b54b6b0a296e996b665f05313a2b87a918691945",
"device_eui": "d02544fffef71f0f",
"app_eui": "0190691000000340",
"device_name": "Bala",
"keyco_num": "3612431",
"register_date": "2017-12-05 13:38:14",
"valid_date": "2018-03-05 13:38:14",
"fw_ver": "0.5.2 ",
"client_group_id": 20001,
"password": null,
"linking": 1
}
]
}
```
Get the keyco device lists of specific user

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycouserdevicelist?userkey={userkey}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
userkey | User key of the user
access_token | access_token Access token to be used with api

## Get keyco device data attribute

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycodataattribute/' --data 'appeui=0220731000000127&pgindex=0&offset=2&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'


curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycodataattribute/' --data 'appeui=0220731000000127&&deveui=d02544fffef44b98&
pgindex=0&offset=0&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycodataattribute/' --data 'appeui=0220731000000127&register_date_begin=20170801&register_date_end=20171004&pgindex=0&offset=2&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycodataattribute/' --data 'appeui=0220731000000127&valid_date_begin=20170801&valid_date_end=20171004&pgindex=0&offset=2&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycodataattribute/' --data 'appeui=0220731000000127&register_date_begin=20170901&register_date_end=20170904&keyword=0.7.9&pgindex=0&offset=10&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycodataattribute/' --data 'appeui=0220731000000127&valid_date_begin=20170901&valid_date_end=20170904&keyword=0.7.9&pgindex=0&offset=10&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycodataattribute/' --data 'appeui=0220731000000127&keyword=0.7.9&pgindex=0&offset=10&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycodataattribute/' --data 'appeui=0220731000000127&timestamp_begin=20170801&timestamp_end=20171004&pgindex=0&offset=2&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycodataattribute/' --data 'appeui=0220731000000127&clientgroupid=1&pgindex=0&offset=2&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"keycodataAttribute":[
{
"appeui": "0220731000000127",
"device_key": null,
"device_eui": "d02544fffef4432b",
"keyco_num": "",
"register_date": "2017-09-03 22:30:38",
"valid_date": "2017-12-03 14:59:59",
"location_interval": null,
"location_intervaltype": null,
"safetyzone_name": null,
"safetyzone_limit": null,
"safetyzone_status": null,
"client_group_id": 0,
“safetyzone_latitude": 13,
"safetyzone_longitude": 17,
"version": "1 ",
"major": "d10c",
"minor": "ac00",
"device_id": "d02544fffef4432b",
"timestamp": "2017-09-28 09:02:54",
"latitude": 1108134101,
"longitude": 1124081567,
"altitude": 50,
"speed": 0,
"hdop": 1,
"gps_num": 5,
"error": 0,
"battery": 50,
"positioning_mode": 1,
"function_operation": 0,
"gps_operation": 1,
"sensor": 1,
"fw_ver": "0.7.9 ",
"sensor_x": 7,
"sensor_y": 0,
"sensor_z": 19,
"created_at": "2017-09-28 09:03:40",
"ct": "2017-09-28 09:03:39",
"lt": "2017-09-28 09:03:39",
"cs": 0
}
],
"status": "Success",
"total": 28
}

{
"keycodataAttribute": null,
"status": "Fail,appeui length/format is wrong"
Total: 0
}


```
Get keyco device data attribute information by specifying various condition

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycodataattribute?appeui={appeui}&deveui={deveui}& pgindex={pgindex}&offset={offset}&register_date_begin={register_date_begin}&register_date_end={register_date_end}&keyword=
{keyword}&valid_date_begin={valid_date_begin}&valid_date_end={valid_date_end}&clientgroupid
={ clientgroupid}& timestamp_begin={ timestamp_begin}& timestamp_end ={timestamp_end }
access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
appeui | Application eui of the device
deveui | Device eui of the device
register_date_begin | Register date begin in YYYYMMDD eg: 20170801
register_date_end | Register date end in YYYYMMDD eg: 20170802
valid_date_begin | valid date begin in YYYYMMDD eg: 20170801
valid_date_end | valid date end in YYYYMMDD eg: 20170802
keyword | keyword for device_key, firmware_version, device_eui, device_name and keyco_number. 
client_group_id | Client group id
timestamp_begin | Timestamp begin date in YYYYMMDD eg: 20170801
timestamp_end | Timestamp end date in YYYYMMDD eg: 20170801
pgindex | Page index for the pagination support
offset | Offset to get no of device information
access_token | Access token to be used with api

# Device Configuration
## Register keyco Device

```shell

curl --request POST 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/register_keycodevice/' --data 'appeui=0220731000000127&deveui=d02544fffef40cc4&devname=test&access_token=19f5ad9e-bf82-493e-aef0-d09daac5522'

```
> The above command returns JSON structured like this:

```json

{
"keycodeviceinfo":{
"device_key": "136da34fe3cefe6b11f4b08013c866f190c226c2",
"device_eui": " d02544fffef40cc4",
"app_eui": "0220731000000127",
"device_name": "Device-2",
"keyco_num": "3773508",
"register_date": "2017-09-27 20:56:52.0",
"valid_date": "2017-12-27 20:56:52.0"
},
"status": "Success"
}

{
"keycodeviceinfo": null,
"status": "Fail,userkey/deveui length/format is wrong"
}

```

This api Register keyco device

### HTTP Request

`POST  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/register_keycodevice?userkey={userkey}&deveui={deveui}&devname={devname}&  
access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
userkey | User key of the user who wants to register device.
deveui | Device eui of the device.
devname | Device name
access_token | Access token to be used with api.

## Unlink keyco device

```shell

curl --request DELETE 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/unlink_keycodevice/' --data 'userkey==076f7293f63e3eb7bb84c35473a0e457f541e179&devicekey=4390be338981c3971bf9fa82fb4efc90ea9c5c83&access_token=19f5ad9e-bf82-493e-aef0-d09daac5522'

```
> The above command returns JSON structured like this:

```json

{
 "Status": "Device 4390be338981c3971bf9fa82fb4efc90ea9c5c83 unlinked from 
 076f7293f63e3eb7bb84c35473a0e457f541e179 Successfully"
}

{
"Status": "Fail,userkey/devicekey format is wrong"
}

```

Unlink registered keyco device mapping information from user

### HTTP Request

`DELETE  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/unlink_keycodevice?userkey={userkey}&devicekey={devicekey}&access_token=
{access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
userkey | User key of the user who wants to register device.
devicekey  | Device key of the device.
access_token | Access token to be used with api.

## Delete keyco device

```shell

curl --request DELETE 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/delete_keycodevice/' --data 'deveui =d02544fffef42fc0&access_token=19f5ad9e-bf82-493e-aef0-d09daac5522'

```
> The above command returns JSON structured like this:

```json
{
 "Status": "Success,Device d02544fffef42fc0 Deleted Successfully"
}

{
 "Status": "Fail, linking exists,Please unlink device before deleting"
}

{
"Status": "Fail,subscription information for the device d02544fffef42fc0 not found"
}

{
"Status": "Fail,deviceeui format is wrong"
}

```

Delete registered keyco device information from device table

### HTTP Request

`DELETE  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/delete_keycodevice?deveui={deveui}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
deveui  | Device eui.
access_token | Access token to be used with api.


## Change valid date of device

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/changekeycodevicevaliddate/' --data 'deveui =d02544fffef42fc0&access_token=19f5ad9e-bf82-493e-aef0-d09daac5522'

```
> The above command returns JSON structured like this:

```json
{
 "Status": "Success,valid date is 2017-12-14"
}

{
 "Status": "Fail,appeui/deveui length/format is wrong"
}

```
change keyco valid date of device

### HTTP Request

`PUT http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/changekeycodevicevaliddate?deveui={deveui}&appeui={appeui}&numofdays={numofdays}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
appeui | Application eui of the device.
deveui  | Device eui.
numofdays | No of days to be incremented/decremeneted eg:2, -2
access_token | Access token to be used with api.

## Update keyco device name

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/update_keycodevicename/' --data 'appeui=0220731000000127&userkey=011c945f30ce2cbafc452f39840f025693339c42&devicekey=995f9a9cb2d0ae26562cfbeb4f5b2c69598bc749&devicename=device1&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
 "Status": "Device 995f9a9cb2d0ae26562cfbeb4f5b2c69598bc749 updated with device1
Successfully"
}

{
 "Status": "Fail,appeui/deveui length/format is wrong"
}

```
Update keyco device name

### HTTP Request

`PUT http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/update_keycodevicename?appeui={appeui}&userkey={userkey}&devicekey={devicekey}&devicename={ devicename}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
appeui | Application eui of the device.
Devicekey  | Device key of the device.
devicename | Device name of the device
access_token | Access token to be used with api.

## Update client group id

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/updatekeycodeviceclientgroupid/' --data 'appeui=0220731000000127&deveui=d02544fffef47f85&clientgroupid=1&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"status": "Success,clientgroupid of d02544fffef47f85 is changed to 1"
}


{
 "Status": "Fail,appeui/deveui length/format is wrong"
}

```
Change the value of client group id of keyco device

### HTTP Request

`PUT http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/updatekeycodeviceclientgroupid?deveui={deveui}&appeui={appeui}&clientgroupid={clientgroupid }`

### Query Parameters

Parameter | Description
--------- | ------------
appeui | Application eui of the device.
deveui  | Device eui of the device.
clientgroupid | Client group id  eg:1,2,3
access_token | Access token to be used with api.

## Set Reporting/Location Interval

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/setinterval/' --data 'deveui=d02544fffef42720&appeui=0220731000000127&interval=2&intervaltype=1&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"appeui": "0220731000000127",
"deviceeui": "d02544fffef42720",
"thingplug_resp": 200,
"status": "Success",
"ri": "EI00000000000005470485"
}

{
"appeui": "0220731000000127",
"deviceeui": "d02544fffef42720",
"thingplug_resp": 0,
"status": "Fail:Invalid interval.Valid values are 1,2,5,10,30,60,120",
"ri": null
}


```
Set reporting/location interval for the device

### HTTP Request

`PUT http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/setinterval?appeui={appeui}&deveui={deveui}&interval={interval}&intervaltype=
{intervaltype}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
appeui | Application eui of the device.
deveui  | Device eui of the device.
interval | To set interval cycle. Valid values are 1,2,5,10,30,60,120
intervaltype  | To set location/reporting cycle. Valid values are 1,2
access_token | Access token to be used with api.

## Reset the device

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/resetdevice/' --data 'appeui={appeui}&deveui={deveui}&access_token={access_token}'

```
> The above command returns JSON structured like this:

```json
{
"appeui": "0220731000000127",
"deviceeui": "d02544fffef42720",
"thingplug_resp": 200,
"status": "Success",
"ri": "EI00000000000005470739"
}

{
"appeui": "0220731000000127",
"deviceeui": "d02544fffef427201",
"thingplug_resp": 0,
"status": "Fail:appeui/deveui length/format is wrong",
"ri": null}

```
Reset the device.

### HTTP Request

`PUT http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/resetdevice?deveui=d02544fffef42720&appeui=0220731000000127&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222`

### Query Parameters

Parameter | Description
--------- | ------------
appeui | Application eui of the device.
deveui  | Device eui of the device.
access_token | Access token to be used with api.

## Set keyco device safety zone information

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/setkeycodevicesafezone/' --data 'deveui={deveui}&appeui={appeui}&safetyzone_name={ safetyzone_name}&safetyzone_limit={safetyzone_limit}&safetyzone_status={ safetyzone_status}&safetyzone_latitude={safetyzone_latitude}&safetyzone_longitude={ safetyzone_longitude}&access_token={access_token}'

```
> The above command returns JSON structured like this:

```json
{
"status": "Success,updated device d02544fffef4bd21 with safetyzone_name=test safetyzone_limit=1500 safetyzone_status=1 safetyzone_latitude=13safetyzone_longitude=17"
}

{
Status: Fail,appeui/deveui length/format is wrong
}


```
Set keyco device safety zone information 

### HTTP Request

`PUT http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/setkeycodevicesafezone?appeui=0220731000000127&deveui=d02544fffef4bd21&safetyzone_name=test&safetyzone_limit=1500&safetyzone_status=1&safetyzone_latitude=13&safetyzone_longitude=17 &access_token=19f5ad9e-bf82-493e-aef0-d09daac55222`

### Query Parameters

Parameter | Description
--------- | ------------
appeui | Application eui of the device.
deveui  | Device eui of the device.
safetyzone_name | Safety zone name
safetyzone_limit | Safetyzone distance eg:200m
safetyzone_status | Safetyzone type for entry/exit eg:1,2
safetyzone_latitude | Safety zone current latitude location 
safetyzone_longitude | Safety zone current longitude location
access_token | Access token to be used with api.


# User Management
## Register keyco user

```shell

curl --request POST 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/register_keycouser/' --data '{"pin_code":"560018","user_name":"guru","user_phone_num":"9900217610","phone_type":"Android", "email":"r.achar@solu-m.com"}&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The JSON body and response of JSON structured like this:

```json
{"pin_code":"560018","user_name":"guru","user_phone_num":"9900217610","phone_type":"Android", "email":"r.achar@solu-m.com"}

{
"keycouserinfo":{
"user_key": "73a102d5663ca9fffd2a6738ea3da353f8edc3b1",
"pin_code": "560018",
"user_name": "guru",
"user_phone_num": "9900217610",
"phone_type": "Android",
"email": "r.achar@solu-m.com",
"register_date": "2017-08-24 21:07:02.0"
},
"status": "Success"
}

```
This api Register keyco user

### HTTP Request

`POST  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/register_keycouser?&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
pin_code  | Pin code of the user.
user_name  | Username of user.
user_phone_num | Phone no of user
email | Email id of the user
access_token | Access token to be used with api.

## Delete keyco user

```shell

curl --request DELETE 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/delete_keycouser/' --data 'userkey=a1872e333d0e52644f6125da2276530f7ebe5e77&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json

{
  "status": "Success, User a1872e333d0e52644f6125da2276530f7ebe5e77 Deleted Successfully"
}

```
Delete registered keyco user

### HTTP Request

`DELETE  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/delete_keycouser?userkey={userkey}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
userkey   | Userkey of the user.
access_token | Access token to be used with api.

## Get keyco user count

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycousercount/' --data 'access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json

{
"total": 3073,
"status": "success"
}

```
Get total no of keyco user count

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycousercount?access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
access_token | Access token to be used with api.

## Get keyco user list

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycouserlistbycondition/' --data 'pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycouserlistbycondition/' --data 'register_date_begin=20170901&register_date_end=20170904&pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycouserlistbycondition/' --data 'register_date_begin=20170901&register_date_end=20170904&keyword=IOS&pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycouserlistbycondition/' --data 'keyword=IOS&pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"status": "Success",
"total": 87,
"listkeycouserinfo":[
{
"user_key": "b2cf342c9ef18d3aab0bca414a64e59639eca7fd",
"pin_code": "",
"user_name": "579588867",
"user_phone_num": "",
"phone_type": "Android",
"register_date": "2018-01-02 09:42:40",
"device_alias": "",
"active_login": ""
},
{
"user_key": "1eec752b78c21e6683237caec24c60836df14b38",
"pin_code": "",
"user_name": "109177169338710333041,zweiwelten75@gmail.com",
"user_phone_num": null,
"phone_type": "iOS",
"register_date": "2018-01-02 09:23:03",
"device_alias": "",
"active_login": ""
}
]
}

```
Get keyco user list by condition

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycouserlistbycondition?appeui={appeui}&pgindex={pgindex}&offset={offset}&
&register_date_begin={register_date_begin}&register_date_end={register_date_end}&keyword={keyword&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
register_date_begin | Register date begin in YYYYMMDD eg: 20170801
register_date_end | Register date end in YYYYMMDD eg: 20170802
keyword | keyword for user_key,user_name, phone_number or phone type
pgindex | Page index for the pagination support
offset | Offset to get no of device information
access_token | Access token to be used with api.

## Get Specific keyco user information

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycouserinfo/' --data 'user_key=bd991840970e8005468094bb160e42845197b565&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycouserinfo/' --data 'user_name=vudamalapati@gmail.com&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'
getkeycouserinfo?user_name=vudamalapati@gmail.com
```
> The above command returns JSON structured like this:

```json
{
"keycouserinfo":{
"user_key": "bd991840970e8005468094bb160e42845197b565",
"pin_code": "",
"user_name": "100439623793991393326,vudamalapati@gmail.com",
"user_phone_num": null,
"phone_type": "Android",
"register_date": "2017-12-30 12:19:40",
"device_alias": "",
"active_login": "",
"password": ""
},
"status": "Success",
"statuscode": 200
}

{
"keycouserinfo": null,
"status": "Fail,user_name vudamalapati@gmail.com124 not found",
"statuscode": 406
}
```
Get Specific keyco user information by user name/user key

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycouserinfo?user_key={user_key}&user_name={user_name}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
user_key | Optional user_key of the user
user_name | Optional user_name of the user
access_token | Access token to be used with api.

## Validate custom keyco user

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/validate_keycouserlogin/' --data 'user_name=vudamalapati@gmail.com[CUSTOM]&password=vcdbnnbhnnvvb&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"keycouserinfo":{
"user_key": "ca2f37efaff516b93e6aa87673667cbe30159963",
"pin_code": "",
"user_name": "vudamalapati@gmail.com[CUSTOM]",
"user_phone_num": "",
"phone_type": "Android",
"register_date": "2018-01-11 15:20:16",
"device_alias": "",
"active_login": "",
"password": "vcdbnnbhnnvvb"
},
"status": "Success,User validated Successfully",
"statuscode": 200
}

{
"keycouserinfo": null,
"status": "Provided Password is wrong",
"statuscode": 406
}

```
Validate custom keyco user

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/validate_keycouserlogin?user_name={user_name}&password={password}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
user_name | keyco custom user name 
password | user password 
access_token | Access token to be used with api.

## Generate custom user forgot password

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/update_keycopassword/' --data 'user_name=vudamalapati@gmail.com[CUSTOM]&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"user_name": "vudamalapati@gmail.com[CUSTOM]",
"password": "P21$Q87zf!",
"status": "Success,password reset Successfully",
"statuscode": 200
}

{
"user_name": "vudamalapati@gmail.com[CUSTOM]11",
"password": null,
"status": "Fail,email id vudamalapati@gmail.com[CUSTOM]11 does not exists",
"statuscode": 406
}

```
Generate and update keyco custom user forgot password

### HTTP Request

`PUT  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/update_keycopassword?user_name={user_name}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
user_name | keyco custom user name 
access_token | Access token to be used with api.


## Reset/update custom user password

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/reset_keycopassword/' --data 'access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command uses below JSON body and returns JSON structured like this:

```json
{
 "user_name":"vudamalapati@gmail.com[CUSTOM]",
 "old_password" :"1234",
 "new_password" :"5678"
}
{
"user_name": "vudamalapati@gmail.com[CUSTOM]",
"old_password": "P21$Q87zf!",
"new_password": "12345678",
"status": "Success,password reset Successfully",
"statuscode": 200
}

{
"user_name": "vudamalapati@gmail.com[CUSTOM]1",
"old_password": "P21$Q87zf!",
"new_password": "12345678",
"status": "Fail,Local user with user_name vudamalapati@gmail.com[CUSTOM]1 does not exists",
"statuscode": 406
}

```
Generate and update keyco custom user password

### HTTP Request

`PUT  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/update_keycopassword?user_name={user_name}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
user_name | keyco custom user name in JSON body
old_password | old password of the user in json body
new_password | New password of the user in json body
access_token | Access token to be used with api.


# Serious/Warning Notification
## Push Serious/Warning notification to mobile device

```shell

curl --request POST 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/push_keyconotification/' --data 'userkey=1b1b3e65ca74a45e3525ee7642f4623e6f9800a5&onesignalkey=dea0c442-090a-4835-83a9-c1a276117b32&message=Alert keyco&severity=12 
&deveui=d02544fffef4bd20&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222&onesignalkey=dea0c442-090a-4835-83a9-c1a276117b32'

```
> The above command includes JSON body and  returns JSON structured like this:

```json
{
"one_signal_key": "dea0c442-090a-4835-83a9-c1a276117b32",
"user_key": "1b1b3e65ca74a45e3525ee7642f4623e6f9800a5",
"message": "Alert keyco",
"severity": "12",
"status": "Success"
}

{
"status": "Fail,invalid userkey"
}

```
Push notification to the keyco user mobile device

### HTTP Request

`POST  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/push_keyconotification?userkey={userkey&onesignalkey={onesignalkey}&message
 ={ message }&severity={severity}access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
deveui  | Device eui
userkey | Userkey of the user
onesignalkey | One signal key of the keyco user
message | Alert Message to be sent to device
severity | Severity of the message eg:2,3,10,12
access_token | Access token to be used with api.

## Update one signal key

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/update_keycoonesignalkey/' --data 'userkey=1b1b3e65ca74a45e3525ee7642f4623e6f9800a5&devicekey=eff56f0745ba3ed892c56eb964a1c34b1ede52c8&onesignalkey=dea0c442-090a-4835-83a9-c1a276117b32&state=0&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json

{
"status":"Success,userkey 1b1b3e65ca74a45e3525ee7642f4623e6f9800a5 
 devicekey eff56f0745ba3ed892c56eb964a1c34b1ede52c8 updated  with onesignalkey
 3b00fb42-f8e7-4c0c-9808-c7613fe2a1fb state false Successfully"
}
{
"status": "Fail,invalid userkey/devicekey"
}

```
update one signal key of the keyco user

### HTTP Request

`PUT  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/update_keycoonesignalkey?userkey={userkey}&devicekey={devicekey}&onesignalkey ={onesignalkey }&state={state}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
userkey   | Userkey of the user.
one_signal_key | One signal key of the keyco user
state | Notification state to be  set to true or false. Values should be 0/1. 0:false, 1:true
access_token | Access token to be used with api.

## Update active login user

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/update_keycoactivelogin/' --data 'userkey=c714b1243a731013e18318d46bfc0bb54c39cf33&onesignalkey=79dc9c92-135d-433d-b213-577ee88b7345&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json

{
  "status": "Success,userkey user_key c714b1243a731013e18318d46bfc0bb54c39cf33  onesignalkey 79dc9c92-135d-433d-b213-577ee88b7345 active login enabled Successfully"
  "statuscode":200
}

{
"status": "Fail,invalid userkey",
"statuscode":500
}

```
update keyco active login user for push notification

### HTTP Request

`PUT  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/update_keycoactivelogin?userkey={userkey}&onesignalkey={onesignalkey }&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
userkey   | Userkey of the user.
one_signal_key | One signal key of the keyco user
access_token | Access token to be used with api.

## Get one signal key of the keyco user

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycoonesignalkey/' --data 'userkey=1b1b3e65ca74a45e3525ee7642f4623e6f9800a5&devicekey=eff56f0745ba3ed892c56eb964a1c34b1ede52c8&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json

{
"one_signal_key": "3b00fb42-f8e7-4c0c-9808-c7613fe2a1fb",
"user_key": "1b1b3e65ca74a45e3525ee7642f4623e6f9800a5",
"device_key": "eff56f0745ba3ed892c56eb964a1c34b1ede52c8",
"notification_state": false,
"status": "Success"
}

{
"status": "Fail,invalid userkey/devicekey"
}

```
Get one signal key of the keyco user

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycoonesignalkey?userkey={userkey}&devicekey={devicekey}&access_token=
{access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
userkey   | Userkey of the user.
devicekey| One signal key of the keyco user
access_token | Access token to be used with api.

## Get Keyco Notification message

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeyconotification/' --data 'appeui=0220731000000127&deveui=d02544fffef4bd20&pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeyconotification/' --data 'appeui=0220731000000127&deveui=d02544fffef4bd20&receive_time_begin=20170901&receive_time_end=20171204&pgindex=0&offset=10&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeyconotification/' --data 'appeui=0220731000000127&deveui=d02544fffef4bd20&send_time_begin=20170901&send_time_end=20171204&pgindex=0&offset=10&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeyconotification/' --data 'appeui=0220731000000127&deveui=d02544fffef4bd20&content=poor&pgindex=0&offset=10 &access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeyconotification/' --data 'appeui=0220731000000127&deveui=d02544fffef4bd20&severity=1&pgindex=0&offset=10 &access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json

{
"one_signal_key": "dea0c442-090a-4835-83a9-c1a276117b32",
"user_key": "1b1b3e65ca74a45e3525ee7642f4623e6f9800a5",
"message": "Alert keyco",
"severity": "12",
"status": "Success"
}

{
"status": "Fail,invalid appeui/deviceeui"
}

```
Search notification message of keyco user device

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeyconotification?appeui={appeui}&deveui={deveui}&pgindex
 ={pgindex}&offset={offset}& receive_time_begin={ receive_time_begin
}&receive_time_end ={receive_time_end}& send_time_begin={send_time_begin
}&send_time_end ={send_time_end} content ={content}& severity={severity}
&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
appeui | Application eui of the device
deveui | Device eui of the device
receive_date_begin | receive date begin in YYYYMMDD eg: 20170801
receive_date_end | receive date end in YYYYMMDD eg: 20170802
send_date_begin | send date begin in YYYYMMDD eg: 20170801
send_date_end | send date end in YYYYMMDD eg: 20170802
content | content to be searched in message 
severity | Severity of the message, 12,3,14 etc
pgindex | Page index for the pagination support
offset | Offset to get no of device information
access_token | Access token to be used with api


# Firmware Management
## Upload keyco firmware

```shell

curl --request POST 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/upload_keycofirmware/' --data 'name=KEYCO_Tracker0810_r4.zip&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"status":" successfully uploaded file= KEYCO_Tracker0810_r4.zip",
"statuscode":200
}

{
"status":"failed to upload KEYCO_keyco0810.zip"
"statuscode":500
}

```
Upload keyco firmware to server

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/upload_keycofirmware?name={name}?access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
name   | Firmware filename with file extension
file   | Select the file to be uploaded to Server in Body
access_token | Access token to be used with api.

## Get latest keyco firmware information

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofirmwareinfo/' --data 'userkey=025cc868760689c53dca2fd283d960e3af59cb78&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"filename": "KEYCO_Tracker0810_r4.zip",
"md5": "a74e93ba98898dbece58dc8d1ff380f2",
"creationtime": "2017-11-24T11:09:34.649244Z",
"device_type": "keyco",
"version": "0810",
"status": "Success",
"statuscode": 200
} 

{
"status":"Fail,User does not have previlege to download firmware"
"statuscode":500
}

```
Get the latest keyco firmware information from server

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofirmwareinfo?&userkey={userkey}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
userkey   | Userkey of the user
access_token | Access token to be used with api.

## Download latest keyco firmware file

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/download_keycofirmware/' --data 'name=KEYCO_Tracker0810_r4.zip&userkey=025cc868760689c53dca2fd283d960e3af59cb78&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"status": "successfully downloaded file= KEYCO_Tracker0810_r4.zip",
"statuscode":200
}

{
"status":"Fail,User does not have previlege to download firmware"
"statuscode":500
}


```
Download keyco firmware file from server

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/download_keycofirmware?name={KEYCO_keyco0810.zip}&userkey ={userkey}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
name    | Firmware filename with file extension
userkey    | Userkey of the user
access_token | Access token to be used with api.

# Share Device Management

## Generate keyco device share link

```shell

curl --request POST 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/generate_keycosharelink/' --data 'access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command includes JSON body and  returns JSON structured like this:

```json
{
 "user_key":"172bc36c250aa965446af93d3a17edd9fe325c4d",
 "device_eui":"d0255c86c10001b8",
 "app_eui":"0190691000000340"
}

{
"user_key": "172bc36c250aa965446af93d3a17edd9fe325c4d",
"device_eui": "d0255c86c10001b8",
"app_eui": "0190691000000340",
"link": "TWAbB4Kr",
"creation_date": "2017-12-13 10:11:59.0",
"expiry_date": "2017-12-16 10:11:59.0",
"count": 1,
"status": "Success",
"statuscode": 200
}

{
  "status": "Fail,User does not exists", 
  "statuscode": 404
}

{
  "status": " Fail,maximum shared users exceeded", 
  "statuscode": 429
}

{
  "status":"Fail,deveui/userkey length/format is wrong", 
  "statuscode": 500
}

```
Generate keyco device share link.

### HTTP Request

`POST  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/generate_keycosharelink?access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
deveui  | Device eui
userkey | Userkey of the user
app_eui | App eui of the device
access_token | Access token to be used with api.

## Register keyco share device

```shell

curl --request POST 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/register_keycosharedevice/' --data 'access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command includes JSON body and  returns JSON structured like this:

```json
{"user_key":"eab6105a6ed3df61483d99f6447f594038e0006a",
 "link" :"RPoD0yBu",
 "one_signal_key":"dea0c442-090a-4835-83a9-c1a276117b32"
}

{
"user_key": "eab6105a6ed3df61483d99f6447f594038e0006a",
"link": "RPoD0yBu",
"one_signal_key": "dea0c442-090a-4835-83a9-c1a276117b32",
"status": "Success",
"statuscode": 200
}

{
  "status": " Fail,Primary user cannot share himself ", 
  "statuscode": 409
}

{
  "status": " Fail,Link is expired ", 
  "statuscode": 408
}

{
  "status": " Fail,userkey length/format is wrong", 
  "statuscode": 500
}

```
Register keyco share device.

### HTTP Request

`POST  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/register_keycosharedevice?access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
deveui  | Device eui
userkey | Userkey of the user
app_eui | App eui of the device
access_token | Access token to be used with api.

## Update keyco branch key

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/update_keycobranchkey/' --data 'link=4NsmhzWc&branch_key=BHrRYR05rJ&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command includes JSON body and  returns JSON structured like this:

```json

{
"status": "Success,link 4NsmhzWc branch_key BHrRYR05rJ updated Successfully",
"statuscode": 200
}

{
  "status": " Fail,invalid branch/link key", 
  "statuscode": 500
}

```
Update keyco branch key for sharing device

### HTTP Request

`PUT  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/update_keycobranchkey?link={link}&branch_key={branch_key}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
link  | link key for share device
branch_key | branch key for share device
access_token | Access token to be used with api.








