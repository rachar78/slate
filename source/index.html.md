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

Welcome to the Kitchen API!This guide describes how to compose and send commands and queries to the IOT platform using the Kitchen REST API. The guide provides examples for a set of common tasks, but it does not describe how to configure the full feature set of the Kitchen Application and it does not list the classes, methods of the API.We have language bindings in CURL! You can view code examples in the dark area to the right. 

# Device Subscription/Unsubscription

## Subscription

```shell

curl --request POST 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/subscribe_device/' --data 'appeui=0220731000000127&deveui=d02544fffef42720&access_token=19f5ad9e-bf82-493e-aef0-d09daac5522'

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

This api Subscribe  kitchen device 

### HTTP Request

`POST  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/subscribe_device?appeui={appeui}&deveui={deveui}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
appeui | Application eui of the device.
deveui | Device eui of the device.
access_token | Access token to be used with api.
<aside class="success">
Remember — access_token is an access token to be used only if authentication is enabled!
</aside>

## Unsubscription
```shell

curl --request DELETE 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/unsubscribe_device/' --data 'appeui=0220731000000127&deveui=d02544fffef42720&access_token=19f5ad9e-bf82-493e-aef0-d09daac5522'

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

'DELETE  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/unsubscribe_device?appeui={appeui}&deveui={deveui}&access_token={access_token}`

### Query Parameters
Parameter | Description
--------- |  -----------
appeui | Application eui of the device.
deveui | Device eui of the device.
access_token | Access token to be used with api.
# Device Information
## Get Latest Device data

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/getkitchendata/latest/ --data 'appeui=0220731000000127&deveui=d02544fffef4bd1d &access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

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

`GET  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/getkitchendata/latest?appeui={appeui}&deveui={deveui}&access_token={access_token}`

### Query Parameters
Parameter | Description
--------- | ------------
appeui | Application eui of the device.
deveui | Device eui of the device.
access_token | Access token to be used with api.

## Get Device History data

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/getkitchendata/' --data 'appeui=0220731000000127&deveui=d02544fffef4bd1f&appeui=0220731000000127&begindate=201707260100&enddate=201707262059&pgindex=0&offset=2&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"status": "Success",
"total": 137,
"listKitchendevices":[
{
"receive_time": "2017-09-27 23:57:10",
"app_eui": "0220731000000127",
"version": "1 ",
"device_id": "d02544fffef4bd20",
"seq": 4680,
"resistance": 1773,
"tvoc": 209,
"temperature": 19137,
"humidity": 27560,
"status": 31,
"created_at": "2017-09-27 23:57:10.011255",
"ct": "2017-09-27 23:57:06",
"lt": "2017-09-27 23:57:06",
"cs": 50,
"temp_threshold": 50,
"fw_ver": "0.3.2 "
}
]
}

{
"status": "Fail,appeui/deveui length/format is wrong",
"total": 0,
"listKitchendevices": null
}

{
"status": "Fail,begindate/enddate format is wrong.Valid format(YYYYMMDDHHMM)",
"total": 0,
"listKitchendevices": null
}

{
"kitchenlatestdeviceinfo": null,
"status": "Fail,appeui/deveui length/format is wrong"
}
```
Get Device history information for a specific date 

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/getkitchendata?appeui={appeui}&deveui={deveui}&beginedate={begindatae}&enddate={enddate}
&pgindex={pgindex}&offset={offset}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
appeui | Application eui of the device.
deveui | Device eui of the device.
access_token | Begin date in the format YYYYMMDDHHMM.
begindate  | Access token to be used with api.
enddate  | end date in the format YYYYMMDDHHMM
pgindex  | Page index for the pagination support
offset  | Offset to get no of device information

## Get appeui of the kitchen device

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/getkitchenappeui/' --data 'deveui=d02544fffef44b98&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"app_eui": "0220731000000127",
"device_eui": "d02544fffef44b98",
"status": "success"
}

{
"app_eui": null,
"device_eui": "d02544fffef44b981",
"status": "Fail,appeui length/format is wrong"
}

{
"app_eui": null,
"device_eui": "d12544fffef44b98",
"status": "Fail,d12544fffef44b98 not ready for registration"
}

```
Get appeui of the specific kitchen device 

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/getkitchenappeui?deveui={deveui}access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
deveui | Device eui of the device.
access_token | access_token Access token to be used with api

# Device Configuration
## Register Kitchen Device

```shell

curl --request POST 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/register_kitchendevice/' --data 'appeui=0220731000000127&deveui=d02544fffef40cc4&devname=test&access_token=19f5ad9e-bf82-493e-aef0-d09daac5522'

```
> The above command returns JSON structured like this:

```json

{
"kitchendeviceinfo":{
"device_key": "136da34fe3cefe6b11f4b08013c866f190c226c2",
"device_eui": " d02544fffef40cc4",
"app_eui": "0220731000000127",
"device_name": "Device-2",
"keyco_kitchen_num": "3773508",
"register_date": "2017-09-27 20:56:52.0",
"valid_date": "2017-12-27 20:56:52.0"
},
"status": "Success"
}

{
"kitchendeviceinfo": null,
"status": "Fail,userkey/deveui length/format is wrong"
}

```

This api Register kitchen device

### HTTP Request

`POST  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/register_kitchendevice?userkey={userkey}&deveui={deveui}&devname={devname}&  
access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
userkey | User key of the user who wants to register device.
deveui | Device eui of the device.
devname | Device name
access_token | Access token to be used with api.

## Unlink kitchen device

```shell

curl --request DELETE 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/unlink_kitchendevice/' --data 'userkey==076f7293f63e3eb7bb84c35473a0e457f541e179&devicekey=4390be338981c3971bf9fa82fb4efc90ea9c5c83&access_token=19f5ad9e-bf82-493e-aef0-d09daac5522'

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

Unlink registered kitchen device mapping information from user

### HTTP Request

`DELETE  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/unlink_kitchendevice?userkey={userkey}&devicekey={devicekey}&access_token=
{access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
userkey | User key of the user who wants to register device.
devicekey  | Device key of the device.
access_token | Access token to be used with api.

## Delete kitchen device

```shell

curl --request DELETE 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/delete_kitchendevice/' --data 'deveui =d02544fffef42fc0&access_token=19f5ad9e-bf82-493e-aef0-d09daac5522'

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

Delete registered kitchen device information from device table

### HTTP Request

`DELETE  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/delete_kitchendevice?deveui={deveui}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
deveui  | Device eui.
access_token | Access token to be used with api.


## Change valid date of device

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/changekitchendevicevaliddate/' --data 'deveui =d02544fffef42fc0&access_token=19f5ad9e-bf82-493e-aef0-d09daac5522'

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
change kitchen valid date of device

### HTTP Request

`PUT http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/changekitchendevicevaliddate?deveui={deveui}&appeui={appeui}&numofdays={numofdays}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
appeui | Application eui of the device.
deveui  | Device eui.
numofdays | No of days to be incremented/decremeneted eg:2, -2
access_token | Access token to be used with api.

## Update kitchen device name

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/update_kitchendevicename/' --data 'appeui=0220731000000127&userkey=011c945f30ce2cbafc452f39840f025693339c42&devicekey=995f9a9cb2d0ae26562cfbeb4f5b2c69598bc749&devicename=device1&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

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
Update kitchen device name

### HTTP Request

`PUT http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/update_kitchendevicename?appeui={appeui}&userkey={userkey}&devicekey={devicekey}&devicename={ devicename}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
appeui | Application eui of the device.
Devicekey  | Device key of the device.
devicename | Device name of the device
access_token | Access token to be used with api.

## Update client group id

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/updatekitchendeviceclientgroupid/' --data 'appeui=0220731000000127&deveui=d02544fffef47f85&clientgroupid=1&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

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
Change the value of client group id of kitchen device

### HTTP Request

`PUT http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/updatekitchendeviceclientgroupid?deveui={deveui}&appeui={appeui}&clientgroupid={clientgroupid }`

### Query Parameters

Parameter | Description
--------- | ------------
appeui | Application eui of the device.
deveui  | Device eui of the device.
clientgroupid | Client group id  eg:1,2,3
access_token | Access token to be used with api.

## Update the kitchen device settings.

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/update_kitchendevicesettings/' --data 'deveui=d02544fffef4bd20&appeui=0220731000000127&latitude=13.456&longitude=17.567&temperature_threshold=50&password=123456&client_group_id=1101&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request PUT 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/update_kitchendevicesettings/' --data 'deveui=d02544fffef4bd20&appeui=0220731000000127&password=123456&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"statuscode": 200,
"status": " Success,Setting information updated"
}

{
 "statuscode": 500,
 "Status": "Fail,invalid userkey"
}

```
Update the kitchen device settings.

### HTTP Request

`PUT http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/update_kitchendevicesettings?deveui={deveui}&appeui={appeui}&latitude={latitude}&longitude ={longitude}&temperature_threshold = {temperature_threshold}&client_group_id ={client_group_id}&password={paswsword}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
appeui | Application eui of the device.
deveui  | Device eui of the device.
latitude | optional latitude of the device
longitude  | optional longitude  of the device
temperature_threshold | Set optional temperature_threshold for the device
client_group_id  | Set optional client_group_id of the device
password  | Optional Password for the device
access_token | Access token to be used with api.

# Device Statistics
## Get Device Day Statistics

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/getkitchendaystats/' --data 'appeui=0220731000000127&deveui=d02544fffef4bd1d &begindate=20170711&enddate=20170713&pgindex=1&offset=1&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"kitchenstatsdaydeviceinfo":[
{
"st_date": "2017-09-24",
"dev_eui": "d02544fffef47f89",
"min_resistance": 26,
"min_tvoc": 0,
"min_temperature": 18998,
"min_humidity": 29630,
"max_resistance": 71,
"max_tvoc": 554,
"max_temperature": 19176,
"max_humidity": 36415,
"avg_resistance": 58,
"avg_tvoc": 31,
"avg_humidity": 33424
}
],
"status": "Success",
"total": 1
}

{
"kitchenstatsdaydeviceinfo": null,
"status": "Fail,appeui/deveui length/format is wrong",
"total": 0
}

{
"kitchenstatsdaydeviceinfo": null,
"status": "Fail,begindate/enddate format is wrong.Valid format(YYYYMMDD)",
"total": 0
}

```
Get Device Statistics Information for date range 

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/getkitchendaystats?appeui={appeui}&deveui={deveui}&beginedate={begindatae}&enddate={enddate}
&pgindex={pgindex}&offset={offset}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
appeui  | Application eui of the device
begindate  | Begin date in the format YYYYMMDD.
enddate  | end date in the format YYYYMMDD.
pgindex  | Page index for the pagination support.
offset  | Offset to get no of device information.
access_token | Access token to be used with api.

## Get Device hourly Statistics

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/getkitchenhourstats/' --data 'appeui=0220731000000127&deveui=d02544fffef4bd1d &begindate=2017071116&enddate=2017071320&pgindex=1&offset=2&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"kitchenstatsdaydeviceinfo":[
{
"st_date": "2017-09-24",
"dev_eui": "d02544fffef47f89",
"min_resistance": 26,
"min_tvoc": 0,
"min_temperature": 18998,
"min_humidity": 29630,
"max_resistance": 71,
"max_tvoc": 554,
"max_temperature": 19176,
"max_humidity": 36415,
"avg_resistance": 58,
"avg_tvoc": 31,
"avg_humidity": 33424
}
],
"status": "Success",
"total": 1
}

{
"kitchenstatsdaydeviceinfo": null,
"status": "Fail,appeui/deveui length/format is wrong",
"total": 0
}

{
"kitchenstatsdaydeviceinfo": null,
"status": "Fail,begindate/enddate format is wrong.Valid format(YYYYMMDD)",
"total": 0
}

```
Get Device statistics information based on specific hour range in a day

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/getkitchenhourstats?appeui={appeui}&deveui={deveui}&beginedate={begindatae}&enddate={enddate}
&pgindex={pgindex}&offset={offset}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
appeui  | Application eui of the device
begindate | Begin date in the format YYYYMMDDHH.
enddate  | end date in the format YYYYMMDDHH.
pgindex  | Page index for the pagination support.
offset  | Offset to get no of device information.
access_token | Access token to be used with api.

# User Management
## Register Kitchen user

```shell

curl --request POST 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/register_kitchenuser/' --data '{"pin_code":"560018","user_name":"guru","user_phone_num":"9900217610","phone_type":"Android", "email":"r.achar@solu-m.com"}&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The JSON body and response of JSON structured like this:

```json
{"pin_code":"560018","user_name":"guru","user_phone_num":"9900217610","phone_type":"Android", "email":"r.achar@solu-m.com"}

{
"kitchenuserinfo":{
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
This api Register kitchen user

### HTTP Request

`POST  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/register_kitchenuser?&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
pin_code  | Pin code of the user.
user_name  | Username of user.
user_phone_num | Phone no of user
email | Email id of the user
access_token | Access token to be used with api.

## Delete Kitchen user

```shell

curl --request DELETE 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/delete_kitchenuser/' --data 'userkey=a1872e333d0e52644f6125da2276530f7ebe5e77&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json

{
  "status": "Success, User a1872e333d0e52644f6125da2276530f7ebe5e77 Deleted Successfully"
}

```
Delete registered kitchen user

### HTTP Request

`DELETE  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/delete_kitchenuser?userkey={userkey}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
userkey   | Userkey of the user.
access_token | Access token to be used with api.

## Update the kitchen user settings

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/update_kitchenusersettings/' --data 'userkey=172bc36c250aa965446af93d3a17edd9fe325c4d&devicekey=6cc9afa018259ae5f2ce25c5211913ed0ccaebdc&push_notification_state=1&periodic_notification_state=1&weather_notification_state=1&notification_time_start=21&notification_time_end=22&notification_period=1&notification_interval=1&refresh_interval=1& one_signal_key=dea0c442-090a-4835-83a9-c1a276117b32&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json

{
"statuscode": 200,
"status": "Success,User Settings updated"
}
{
"status": "Fail,invalid userkey",
"statuscode": 500

}

```
Update the kitchen user settings

### HTTP Request

`PUT  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/update_kitchenusersettings?userkey={userkey}&devicekey={devicekey}& push_notification_state={push_notification_state}&weather_notification_state ={ weather_notification_state }& notification_time_start ={ notification_time_start
}&notification_time_end={notification_time_end}&notification_period=={ notification_period}&notification_interval ={notification_interval}&refresh_interval ={refresh_interval }& one_signal_key={one_signal_key}access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
userkey   | Userkey of the user.
devicekey | Device key of the device
push_notification_state | Enable/Disable optional push notification state 1/0.
weather_notification_state | Enable/Disable optional weather notification state 1/0
notification_time_start | Set optional notification time start in hour
notification_time_end | Set optional notification time end in hour
notification_period | set values for optional notification period 
notification_interval | set values for optional notification interval 
refresh_interval | set values for optional refresh interval
one_signal_key | set one_signal_key
access_token | Access token to be used with api.

## Update active login user

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/update_kitchenactivelogin/' --data 'userkey=c714b1243a731013e18318d46bfc0bb54c39cf33&onesignalkey=79dc9c92-135d-433d-b213-577ee88b7345&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

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
update kitchen active login user for push notification

### HTTP Request

`PUT  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/update_kitchenactivelogin?userkey={userkey}&onesignalkey={onesignalkey }&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
userkey   | Userkey of the user.
one_signal_key | One signal key of the kitchen user
access_token | Access token to be used with api.

## Get kitchen user count

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/getkitchenusercount/' --data 'access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json

{
"total": 3073,
"status": "success"
}

```
Get total no of kitchen user count

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/getkitchenusercount?access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
access_token | Access token to be used with api.

## Get kitchen user list

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/get_kitchenuserlistbycondition/' --data 'pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/get_kitchenuserlistbycondition/' --data 'register_date_begin=20170901&register_date_end=20170904&pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/get_kitchenuserlistbycondition/' --data 'register_date_begin=20170901&register_date_end=20170904&keyword=IOS&pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/get_kitchenuserlistbycondition/' --data 'keyword=IOS&pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"status": "Success",
"total": 87,
"listKitchenuserinfo":[
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
Get kitchen user list by condition

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/get_kitchenuserlistbycondition?appeui={appeui}&pgindex={pgindex}&offset={offset}&
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
# Serious/Warning Notification
# Weather Notification
## Get Weather Information

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/getkitchenweather/' --data 'userkey=172bc36c250aa965446af93d3a17edd9fe325c4d&devicekey=6cc9afa018259ae5f2ce25c5211913ed0ccaebdc&language=kor
&access_token=caf1366e-eb95-4d48-80a7-f8b83e0cf53b'

curl --request GET 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/getkitchenweather/' --data 'userkey=172bc36c250aa965446af93d3a17edd9fe325c4d&devicekey=6cc9afa018259ae5f2ce25c5211913ed0ccaebdc&language=eng&
access_token=caf1366e-eb95-4d48-80a7-f8b83e0cf53b'

```
> The above command returns JSON structured like this:

```json
{
"status": "Success",
"latitude": "37.4831368714460851",
"longitude": "127.132857792502961",
"user_key": "1567c7a74d13f2441876b1f7558afaee4b249627",
"device_key": "d14f0a82310144f410019cbe92eb17ea87871435",
"grid": "{\"city\":\"서울\",\"latitude\":\"37.48645\",\"county\":\"송파구\",\"village\":\"문정2동\",\"longitude\":\"127.10414\"}",
"currentTemp": "{\"tmax\":\"0.00\",\"tmin\":\"-6.00\",\"tc\":\"-0.40\"}",
"currentSky": "{\"code\":\"SKY_O01\",\"name\":\"Sunny\"}",
"currentHumidity": "30.00",
"currentWind": "{\"wdir\":\"297.00\",\"wspd\":\"1.60\"}",
"rainForecast": "10.00",
"currentPm25": "{\"grade\":\"Moderate\",\"value\":\"17\"}",
"currentPm10": "{\"grade\":\"Moderate\",\"value\":\"33\"}",
"currentO3": "{\"grade\":\"Good\",\"value\":\"0.023\"}",
"forecast2dayTempMax": "0.00",
"forecast2dayTempMin": "-7.00",
"forecast2daySky": "{\"code\":\"SKY_M04\",\"name\":\"흐림\"}",
"forecast3dayTempMax": "2.00",
"forecast3dayTempMin": "-4.00",
"forecast3daySky": "{\"code\":\"SKY_M04\",\"name\":\"흐림\"}",
"forecast4dayTempMax": "2",
"forecast4dayTempMin": "-6",
"forecast4daySky": "{\"code\":\"SKY_W02\", \"name\":\"Partly Cloudy\"}",
"forecast5dayTempMax": "2",
"forecast5dayTempMin": "-5",
"forecast5daySky": "{\"code\":\"SKY_W03\", \"name\":\"Mostly Cloudy\"}",
"forecast6dayTempMax": "2",
"forecast6dayTempMin": "-2",
"forecast6daySky": "{\"code\":\"SKY_W12\", \"name\":\"Snow\"}",
"timeRelease": "2018-01-03 15:00:00"
}

```
Get the weather of kitchen device location by language

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/getkitchenweather?userkey={user_key}&devicekey={device_key}&language={language}
&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
userkey  | Userkey of the user
devicekey | Device key of the device
language | Language – kor, eng
access_token | Access token to be used with api.

## Push weather notification to user

```shell

curl --request POST 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/pushkitchenWeatherNotification/' --data 'notificationtime=13&access_token=caf1366e-eb95-4d48-80a7-f8b83e0cf53b'

```
> The above command returns JSON structured like this:

```json
{
"kitchennotification":[
{
"one_signal_key": "30541824-866b-4394-a550-b095abe9128c",
"user_key": "1c1479753d82a541a14e75e303c3f08385a19745",
"message": "오늘은 어제보다 0.6°C 높아요.(-1.0°C~5.0°C)",
"severity": "0",
"status": "Success"
}
],
"status": "Success",
"total": 1
}

{
"kitchennotification":[],
"status": "Fail, SK Plannet API has an error.",
"total": 0
}

```
Push weather notification to the kitchen user mobile device at the specified time

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/pushkitchenWeatherNotification?notificationtime={notification_time}
&access_token={access_token}
`

### Query Parameters

Parameter | Description
--------- | ------------
notificationtime  | User specified time
access_token | Access token to be used with api.

# Firmware Management
## Upload kitchen firmware

```shell

curl --request POST 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/upload_kitchenfirmware/' --data 'name=KEYCO_Kitchen0810.zip&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"status":" successfully uploaded file= KEYCO_Kitchen0810.zip",
"statuscode":200
}

{
"status":"failed to upload KEYCO_Kitchen0810.zip"
statuscode:500
}

```
Upload kitchen firmware to server

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/upload_kitchenfirmware?name={name}?access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
name   | Firmware filename with file extension
file   | Select the file to be uploaded to Server in Body
access_token | Access token to be used with api.

## Get latest kitchen firmware information

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/get_kitchenfirmwareinfo/' --data 'userkey=025cc868760689c53dca2fd283d960e3af59cb78&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"filename": "KEYCO_Kitchen0810.zip",
"md5": "a74e93ba98898dbece58dc8d1ff380f2",
"creationtime": "2017-11-24T11:09:34.649244Z",
"device_type": "kitchen",
"version": "0810",
"status": "Success",
"statuscode": 200
} 

{
"status":"Fail,User does not have previlege to download firmware"
"statuscode":500
}

```
Get the latest kitchen firmware information from server

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/get_kitchenfirmwareinfo?&userkey={userkey}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
userkey   | Userkey of the user
access_token | Access token to be used with api.

## Download latest kitchen firmware file

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/download_kitchenfirmware/' --data 'name=KEYCO_Kitchen0810.zip&userkey=025cc868760689c53dca2fd283d960e3af59cb78&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"status": "successfully downloaded file= KEYCO_Kitchen0810.zip",
"statuscode":200
}

{
"status":"Fail,User does not have previlege to download firmware"
"statuscode":500
}


```
Download kitchen firmware file from server

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/download_kitchenfirmware?name={KEYCO_Kitchen0810.zip}&userkey ={userkey}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
name    | Firmware filename with file extension
userkey    | Userkey of the user
access_token | Access token to be used with api.

# Share Device Management

## Generate kitchen device share link

```shell

curl --request POST 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/generate_kitchensharelink/' --data 'access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

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
Generate kitchen device share link.

### HTTP Request

`POST  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/generate_kitchensharelink?access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
deveui  | Device eui
userkey | Userkey of the user
app_eui | App eui of the device
access_token | Access token to be used with api.

## Register kitchen share device

```shell

curl --request POST 'http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/register_kitchensharedevice/' --data 'access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

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
Register kitchen share device.

### HTTP Request

`POST  http://keycoiot.solu-m.com/keyco-kitchen/iotrestapi/api/register_kitchensharedevice?access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
deveui  | Device eui
userkey | Userkey of the user
app_eui | App eui of the device
access_token | Access token to be used with api.




