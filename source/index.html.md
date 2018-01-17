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

## Get total keyco finder device count

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycofinderdevicecount/' --data access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"total": 1523,
"status": "success"
}


```
Get total no of of keyco finder device count 

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycofinderdevicecount?access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
access_token | access_token Access token to be used with api

## Get keyco finder user lists by condition

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofinderuserlistbycondition/' --data 'pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofinderuserlistbycondition/' --data 'register_date_begin=20170901&register_date_end=20170904&pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofinderuserlistbycondition/' --data 'register_date_begin=20170901&register_date_end=20170904&keyword=IOS&pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofinderuserlistbycondition/' --data 'keyword=IOS&pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"active_user": null,
"status": "Success",
"total": 130,
"statuscode": 0,
"listKeycofinderuserinfo":[
{
"user_key": "2ef2bf005d797df7f278cf2af8c53093ba4a8ebe",
"pin_code": "12345",
"user_name": "UrR8OVQGEQgpmqDbP5KIEHBMltJ2_test keyco",
"user_phone_num": null,
"phone_type": "Android",
"register_date": "2018-01-12 09:31:06",
"gcmid": "e0e1bccb-b01a-4fb4-8157-52e4ccd8259c",
"email": "keycotest@gmail.com"
},
{
"user_key": "272a927e06e467adb13175f18829f4f69883e24e",
"pin_code": "12345",
"user_name": "7KKISaXErTgW9AuRZAu1iYZmHHu2_Anand Kalagi",
"user_phone_num": null,
"phone_type": "Android",
"register_date": "2018-01-12 09:26:54",
"gcmid": "1219fd5d-014f-4c75-a411-bd32f80eceef",
"email": "Anand Kalagi"
}
]
}

```
Get keyco finder user lists by condition

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofinderuserlistbycondition?register_date_begin={register_date_begin}&register_date_end={register_date_end}&keyword={keyword}&pgindex={pgindex}&offset={offset}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
register_date_begin | Register date begin in YYYYMMDD eg: 20170801
register_date_end | Register date end in YYYYMMDD eg: 20170802
keyword | keyword for user_key,user_name, phone_number or phone type. 
pgindex | Page index for the pagination support
offset | Offset to get no of device information
access_token | Access token to be used with api

## Get keyco finder user lists of specific device
```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofinderdeviceuserlist/' --data 'deveui=d025d77336adf3ce&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"active_user": "781792b3f9a3a329e44cdaeda0bd61c28b93b9e1",
"status": "Success",
"total": 2,
"statuscode": 200,
"listKeycofinderuserinfo":[
{
"user_key": "781792b3f9a3a329e44cdaeda0bd61c28b93b9e1",
"pin_code": null,
"user_name": "107704090541995454648syamkumar1910@gmail.com",
"user_phone_num": null,
"phone_type": "IOS",
"register_date": "2018-01-11 11:58:00",
"gcmid": "03af6588-bdfd-4450-a4a6-70cbb8b1e329",
"email": "syamkumar1910@gmail.com"
},
{
"user_key": "0671fc9a62e39d5098f654042546db0a6aa1edee",
"pin_code": "12345",
"user_name": "YAAWP1Ue29ThsiYjiC5Lb1iUNLp1_Syam Kumar",
"user_phone_num": null,
"phone_type": "Android",
"register_date": "2018-01-12 05:41:15",
"gcmid": "421aeea6-cf48-4acf-9605-ed41e0cb5b59",
"email": "Syam Kumar"
}
]
}
```
Get keyco finder user lists of specific device

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofinderdeviceuserlist?deveui={deveui}&access_token={access_token`

### Query Parameters

Parameter | Description
--------- | ------------
deveui | device eui
access_token | Access token to be used with api

## Get keyco device lists of specific user

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofinderuserdevicelist/' --data 'userkey=8f9e211ed7eb7f5cdf9712b8a78539d8754a73f0&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"status": "Success",
"total": 1,
"statuscode": 200,
"listKeycofinderdeviceinfo":[
{
"device_key": "8b471703969579b99ba67009f82bfb8fc7823ca3",
"device_eui": "d025cd0cd5a354a5",
"device_name": "a5",
"register_date": "2017-11-29 12:03:13",
"valid_date": "2018-02-28 12:03:13",
"device_type": "CARD",
"latitude": 13.0454197,
"longitude": 77.6210666,
"connection_state": 0,
"active_user": null,
"linkloss_time": "2017-11-29 05:56:46",
"version": null,
"out_into_range": 1110111,
"phone_alarm": 3,
"device_alarm": 3,
"melody_type": 1,
"notification_state": false,
"base64": "iVBORw0KGgoA=",
"device_owner": "PRIMARY"
}
]
}

```
Get the keyco device lists of specific user

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofinderuserdevicelist?userkey={userkey}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
userkey | User key of the user
access_token | access_token Access token to be used with api

## Get keyco finder device lists by specific condition

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofinderdevicelistbycondition/' --data 'pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofinderdevicelistbycondition/' --data 'register_date_begin=20170901&register_date_end=20170904&pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofinderdevicelistbycondition/' --data 'register_date_begin=20170901&register_date_end=20170904&keyword=IOS&pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofinderdevicelistbycondition/' --data 'keyword=IOS&pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"status": "Success",
"total": 81,
"statuscode": 0,
"listKeycofinderdeviceinfo":[
{
"device_key": "2a2dee583fccfc7ba0c01d2fc5e5a1b0d69087a1",
"device_eui": "d025ce8785bbd311",
"device_name": "d311",
"register_date": "2018-01-12 10:07:32",
"valid_date": "2018-04-12 10:07:32",
"device_type": "CARD",
"latitude": 37.292198,
"longitude": 127.14841,
"connection_state": 0,
"active_user": null,
"linkloss_time": null,
"version": null,
"out_into_range": 1110111,
"phone_alarm": 3,
"device_alarm": 3,
"melody_type": 1,
"notification_state": true,
"base64": "iVBORw0KGgoASUVORK5CYII=",
"device_owner": null,
"last_receive_time": null,
"battery": 0
},
{
"device_key": "446a7f1c733589ac3a40e5536268960521d7409c",
"device_eui": "d025c1fe6e9176ce",
"device_name": "ce",
"register_date": "2018-01-12 10:05:57",
"valid_date": "2018-04-12 10:05:57",
"device_type": "CARD",
"latitude": 13.0454512,
"longitude": 77.6211463,
"connection_state": 1,
"active_user": "272a927e06e467adb13175f18829f4f69883e24e",
"linkloss_time": "2018-01-12 15:37:23",
"version": null,
"out_into_range": 1110111,
"phone_alarm": 3,
"device_alarm": 3,
"melody_type": 1,
"notification_state": true,
"base64": "iVBORw0KGgoAAASUVORK5CYII=",
"device_owner": null,
"last_receive_time": null,
"battery": 0
}
]
}

```
Get keyco finder device lists by specific condition

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofinderdevicelistbycondition?register_date_begin={register_date_begin}&register_date_end={register_date_end}&keyword={keyword}&pgindex={pgindex}&offset={offset}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
register_date_begin | Register date begin in YYYYMMDD eg: 20170801
register_date_end | Register date end in YYYYMMDD eg: 20170802
keyword | keyword for user_key,user_name, phone_number or phone type. 
pgindex | Page index for the pagination support
offset | Offset to get no of device information
access_token | Access token to be used with api

# Device Configuration
## Register keyco finder Device

```shell

curl --request POST 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/register_keycofinderdevice/' --data 'userkey=fb4b7dd7a14a5d07b11d9857bdd29dc51959264d&appeui=0220731000000127&deveui=d02544fffef40cc4&devname=test&latitude=37.2921308&longitude=127.1481029&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json

{
"keycofinderdeviceinfo":{
"device_key": "747417f2206148a3118d02f3adf20b5e4139baac",
"device_eui": "d02544fffef40cc4",
"device_name": "test",
"register_date": "2017-10-30 18:57:19.0",
"valid_date": "2018-01-30 18:57:19.0"
},
"status": "Success"
}


{
" keycofinderdeviceinfo ": null,
"status": "Fail,deveui length/format is wrong"
}

```

This api Register keyco finder device

### HTTP Request

`POST  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/register_keycofinderdevice?userkey={userkey}&deveui={deveui}&devname={devname}&
latitude={latitude}&longitude={longitude}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
userkey | User key of the user who wants to register device.
deveui | Device eui of the device.
devname | Device name
latitude | Latitude information of device
longitude | Longitude information of device
access_token | Access token to be used with api.

## Delete keyco finder device

```shell

curl --request DELETE 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/delete_keycofinderdevice/' --data 'userkey=4cd16fd52031768fed5ccca4f64487c53ca8b6c8&deveui=d02544fffef42fc0&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
 "Status": "Success,Device d02544fffef42fc0 Deleted Successfully"
}

{
"Status": "Fail,deviceeui format is wrong"
}

```

Delete registered keyco finder device information

### HTTP Request

`DELETE  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/delete_keycofinderdevice?userkey={userkey}&deveui={deveui}&access_token={access_token`

### Query Parameters

Parameter | Description
--------- | ------------
deveui  | Device eui.
access_token | Access token to be used with api.

## Update keyco finder settings

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/update_keycofindersettings/' --data 'access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command takes JSON body as below and returns JSON structured like this:

```json
{
 "user_key":"8f2721dde4e67a8c931fbc67ba76f713bc8cb56b",
 "deveui":"d025e99c966530bd",
 "device_alias":"test2",
 "out_into_range":"1",
 "phone_alarm":"1",
 "device_alarm":"1", 
 "melody_type":"2",
 "notification_state":"1",
 "version":"0.1.10",
 "base64":"iVBOCC"
}

{  
  "status": " Success", 
  "statuscode": 200
 }

{
  "status": " Fail,Image update failed ", 
  "statuscode": 500
}


```
Update keyco finder user settings. Each fields are optional except userkey and device eui

### HTTP Request

`PUT http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/uupdate_keycofindersettings?access_token={access_token`

### Query Parameters

Parameter | Description
--------- | ------------
Userkey | User key of the user
deveui | Device eui
device_alias | Device name
out_into_range | Out_into_range enable/disable
phone_alarm | Enable/disable phone alarm 1/0
device_alarm | Enable/disable device alarm 1/0
melody_type | Set melody type
notification_state | Enable/disable push notification state alarm 1/0
version | Set version no of the device
base64 | Base64 image
access_token | Access token to be used with api

## Update keyco finder device connection status

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/update_keycofinderconnectionstate/' --data 'userkey=8f2721dde4e67a8c931fbc67ba76f713bc8cb56b&deveui=d025eae17d2f9183&connection_state=1&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command takes JSON body as below and returns JSON structured like this:

```json
{  
  "status": " Success", 
  "statuscode": 200

}

{
  "status": " Fail,invalid user ", 
  "statuscode": 500
}


```
Update keyco finder device connection status

### HTTP Request

`PUT http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/update_keycofinderconnectionstate?userkey={userkey}&deveui={deveui}&connection_state=1&
access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
Userkey | User key of the user
Deveui | Device eui
Connection_state  | Enable/disable connection_state 1/0
access_token | Access token to be used with api

## Register device location information

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/update_keycofinderlocationinfo/' --data 'deveui=d025eae17d2f9183&latitude=37.2921308&longitude=127.1481029&linkloss_time=2017-10-11 13:22:50
&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222
'

```
> The above command takes JSON body as below and returns JSON structured like this:

```json
{
"keycofinderlocationinfo":{
"device_id": "d025eae17d2f9183",
"latitude": 37.2921308,
"longitude": 127.1481029,
"receive_time": "2017-10-30 10:32:17.0",
"linkloss_time": "2017-10-11 13:22:50"
},
"status": "Success"
}

{
  "status": " Fail,deviceeui format is wrong ", 
  "statuscode": 500
}

```
Register device location information of device into database

### HTTP Request

`PUT http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/uupdate_keycofinderlocationinfo?deveui={deveui}&latitude={latitude}& longitude={ longitude}&linkloss_time={linkloss_time}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
deveui | Device eui of the lost found device
latitude  | latitude of the lost found device
longitude  | longitude of the lost found device
linkloss_time | link loss time in the format yyyy-MM-dd HH:mm:ss
access_token | access_token

# User Management
## Register keyco finder user

```shell

curl --request POST 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/register_keycouser/' --data '{"pin_code":"560018","user_name":"ashok","user_phone_num":"9900217610","phone_type":"Android","gcmid":"12345","email":"r.achar@solu-m.com"}
&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The JSON body and response of JSON structured like this:

```json
{
"keycofinderuserinfo":{
"user_key": "9e0b93e9c5810aeb0f2c6945dc4891f6e9aba875",
"pin_code": "560018",
"user_name": "ashok",
"user_phone_num": "9900217610",
"phone_type": "Android",
"register_date": "2017-10-26 09:13:46.0",
"gcmid": "12345",
"email":"r.achar@solu-m.com"
},
"status": "Success"


```
This api Register keyco finder user

### HTTP Request

`POST  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/register_keycofinderuser?&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
pin_code  | Pin code of the user.
user_name  | Username of user.
user_phone_num | Phone no of user
phone_type | Phone type of user IOS/Android
gcmid | One signal key of the user
email | Email id of the user
access_token | Access token to be used with api.

## Delete keyco Finder user

```shell

curl --request DELETE 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/delete_keycofinderuser/' --data 'userkey=a1872e333d0e52644f6125da2276530f7ebe5e77&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json

{
  "status": "Success, User a1872e333d0e52644f6125da2276530f7ebe5e77 Deleted Successfully"
}

```
Delete registered keyco finder user

### HTTP Request

`DELETE  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/delete_keycofinderuser?userkey={userkey}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
userkey   | Userkey of the user.
access_token | Access token to be used with api.

## Get keycofinder user count

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeyfindercousercount/' --data 'access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json

{
"total": 3073,
"status": "success"
}

```
Get total no of keyco finder user count

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycousercount?access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
access_token | Access token to be used with api.

## Get keyco finder user list

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofinderuserlistbycondition/' --data 'pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofinderuserlistbycondition/' --data 'register_date_begin=20170901&register_date_end=20170904&pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofinderuserlistbycondition/' --data 'register_date_begin=20170901&register_date_end=20170904&keyword=IOS&pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofinderuserlistbycondition/' --data 'keyword=IOS&pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"active_user": null,
"status": "Success",
"total": 202,
"statuscode": 0,
"listKeycofinderuserinfo":[
{
"user_key": "c058825cc3a07dba6aefa87045858d5b4c02d2fc",
"pin_code": "12345",
"user_name": "701498194",
"user_phone_num": "",
"phone_type": "Android",
"register_date": "2018-01-17 11:20:35",
"gcmid": "5e55bf49-d347-4a3d-a81a-ac340d815520",
"email": "ej_k72@daum.net"
},
{
"user_key": "58173465f67d7a85d931dc0948cfae234f68711d",
"pin_code": "12345",
"user_name": "701494942",
"user_phone_num": "",
"phone_type": "Android",
"register_date": "2018-01-17 11:16:58",
"gcmid": "c170580c-edc1-46c1-bee0-3a00e65055ec",
"email": "natty79d@naver.com"
}
]
}
```
Get keycofinder user list by condition

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


## Validate custom keyco finder user

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/validate__keycofinderuserlogin/' --data 'email=achar123@gmail.com&password=qii8E8sPC-L&gcmid=1234&phone_type=Android&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
  "status": " Success,User validated Successfully", 
  "statuscode": 200

 }

 {
  "status": " Provided Password is wrong", 
  "statuscode": 500
}

```
Validate custom keyco finder user

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/validate_keycofinderuserlogin?email={email}&password={password}&gcmid={gcmid}&
phone_type={phone_type}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
email | email
password  | password 
gcmid | gcmid
phone_type | phone_type
access_token | access_token

## Generate custom user forgot password

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/update_keycofinderpassword/' --data 'email=achar123@gmail.com&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
  "user_name": "achar123@gmail.com",
  "password": "asduiik",
  "status": " Success,password reset Successfully ", 
  "statuscode": 200

 }
{
  "status": "Fail,email id  does not exists ", 
  "statuscode": 500
}


```
Generate and update keyco custom user forgot password

### HTTP Request

`PUT  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/update_keycopassword?user_name={user_name}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
email | Valid Email id of the user
access_token | Access token to be used with api.


## Reset/update custom user password

```shell

curl --request PUT 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/reset_keycofinderpassword/' --data '{"email":"gurubg@gmail.com",
 "old_password" :"1234",
 "new_password" :"5678"
}&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json

{
"email": "gurubg@gmail.com",
"old_password": "5678",
"new_password": "1234",
"status": "Success,password reset Successfully",
"statuscode": 200
}

{
"email": "gurubg@gmail.com",
"old_password": null,
"new_password": "5678",
"status": "Fail,invalid input",
"statuscode": 500
} 

{
"email": "gurubg@gmail.com",
"old_password": null,
"new_password": "5678",
"status": "Fail,Local user with email id doesnot exists",
"statuscode": 500
}

{
"email": "gurubg@gmail.com",
"old_password": null,
"new_password": "5678",
"status": "Fail,provided old password is wrong",
"statuscode": 404
}

```
Reset keyco finder password with user provided password.

### HTTP Request

`PUT  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/update_keycopassword?user_name={user_name}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
user_name | keyco custom user name in JSON body
old_password | old password of the user in json body
new_password | New password of the user in json body
access_token | Access token to be used with api.


#  Lost Found device Notification
## Register and push lost found device info to user

```shell

curl --request POST 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/register_keycofinderlostlocationinfo/' --data 'register_keycofinderlostlocationinfo?deveui=d025eae17d2f9183&latitude=37.2921308&longitude=127.1481029&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command includes JSON body and  returns JSON structured like this:

```json
{
"status": "Success",
"statuscode": 200
}

{
"status": "Fail, duplicate request with same location info",
"statuscode": 408
}

{
"status": "Fail, duplicate request within 5 mins",
"statuscode": 406
}
{
"status": "Fail,deviceeui format is wrong",
"statuscode": 500
}

{
"status": "Fail,unable to send Push notification",
"statuscode": 500
}


```
Register lost found device information and Push notification to the user.

### HTTP Request

`POST  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/register_keycofinderlostlocationinfo?deveui={deveui}&latitude={latitude}& longitude={ longitude}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
deveui | Device eui of the lost found device
latitude  | latitude of the lost found device
longitude  | longitude of the lost found device
access_token | Access token to be used with api


## Get Keyco Notification message

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycofindernotification/' --data 'deveui=d02544fffef4bd20&pgindex=0&offset=5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeycofindernotification/' --data 'deveui=d02544fffef4bd20&receive_time_begin=20170901&receive_time_end=20171204&pgindex=0&offset=10&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json

{
"status": "Success",
"statuscode": 200,
"total": 23,
"keycofindernotification":[
{
"device_id": "d025cd0cd5a354a5",
"receive_time": "2017-10-30 06:45:11",
"send_time": "2017-10-30 06:45:11",
"latitude": 13.0453614,
"longitude": 77.620979
}
]
}

{
"status": "Fail,Fail,invalid userkey"
}

```
Search notification message of keyco finder user device

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/getkeyconotification?appeui={appeui}&deveui={deveui}&pgindex
 ={pgindex}&offset={offset}&receive_time_begin={receive_time_begin}&receive_time_end ={receive_time_end}& send_time_begin={send_time_begin}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
deveui | Device eui of the device
receive_date_begin | receive date begin in YYYYMMDD eg: 20170801
receive_date_end | receive date end in YYYYMMDD eg: 20170802
pgindex | Page index for the pagination support
offset | Offset to get no of device information
access_token | Access token to be used with api


# Firmware Management
## Upload keyco finder firmware

```shell

curl --request POST 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/upload_keycofinderfirmware/' --data 'name=DFU_SKC_V1.0.10_20171031.zip&devtype=CARD&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

curl --request POST 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/upload_keycofinderfirmware/' --data 'name=DFU_SKM_V1.0.07_20171031.zip&devtype=MINI&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"status":" successfully uploaded file= DFU_SKC_V1.0.10_20171031.zip",
"statuscode":200
}

{
"status":"failed to upload DFU_SKC_V1.0.10_20171031.zip"
"statuscode":500
}

```
Upload keyco finder firmware to server

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/upload_keycofinderfirmware?name={name}&devtype={devtype} &access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
name   | Firmware filename with file extension
file   | Select the file to be uploaded to Server in Body
devtype | Device type CARD/MINI
access_token | Access token to be used with api.

## Get latest keyco finder firmware information

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofinderfirmwareinfo/' --data 'userkey=025cc868760689c53dca2fd283d960e3af59cb78&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
"filename": "DFU_SKC_V1.0.8_20170915.zip",
"md5": "fe2818bf2a8c91a28ae92b1febb54501",
"creationtime": "2017-11-28T12:12:25.920088Z",
"device_type": "CARD",
"version": "1.0.8",
"status": "Success",
"statuscode": 200
}

{
"status":"Fail,User does not have previlege to download firmware"
"statuscode":500
}

```
Get the latest keyco finder firmware information from server

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofinderfirmwareinfo?&userkey={userkey}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
userkey   | Userkey of the user
access_token | Access token to be used with api.

## Download latest keyco firmware file

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/download_keycofinderfirmware/' --data 'userkey=4cd16fd52031768fed5ccca4f64487c53ca8b6c8&name=DFU_SKC_V1.0.8_20170915.zip&devtype=CARD&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command returns JSON structured like this:

```json
{
status:"successfully downloaded file= DFU_SKC_V1.0.8_20170915.zip",
statuscode:200
}


{
"status":"Fail,User does not have previlege to download firmware"
"statuscode":500
}


```
Download keyco finder firmware file from server

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/download_keycofinderfirmware?name={name}&userkey ={userkey}&devtype={devtype}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
name    | Firmware filename with file extension
userkey    | Userkey of the user
access_token | Access token to be used with api.

# Share Device Management

## Generate keyco finder device share link

```shell

curl --request POST 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/generate_keycofindersharelink/' --data 'access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

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
Generate keyco finder device share link.

### HTTP Request

`POST  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/generate_keycfinderosharelink?access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
deveui  | Device eui
userkey | Userkey of the user
app_eui | App eui of the device
access_token | Access token to be used with api.

## Register keyco finder share device

```shell

curl --request POST 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/register_keycofindersharedevice/' --data 'access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command includes JSON body and  returns JSON structured like this:

```json
{"user_key":"eab6105a6ed3df61483d99f6447f594038e0006a",
 "link" :"RPoD0yBu"
}

{
"user_key": "eab6105a6ed3df61483d99f6447f594038e0006a",
"link": "RPoD0yBu",
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
Register keyco finder share device.

### HTTP Request

`POST  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/register_keycosharedevice?access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
deveui  | Device eui
userkey | Userkey of the user
access_token | Access token to be used with api.

## Delete keyco finder share device

```shell

curl --request DELETE 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/delete_keycofindersharedevice/' --data 'userkey=4cd16fd52031768fed5ccca4f64487c53ca8b6c8&deveui=d02544fffef42fc0&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command includes JSON body and  returns JSON structured like this:

```json

{
"status": "Shared Device unlinked from user Successfully",
"statuscode": 200
}

{
  "status": "Fail,Device not registered by shared user", 
  "statuscode": 500
}

```
Delete shared keyco finder device information from device table. Only Primary user can delete his shared device.

### HTTP Request

`DELETE  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/delete_keycofindersharedevice?userkey={userkey}&deveui={deveui}
&access_token={access_token}
`

### Query Parameters

Parameter | Description
--------- | ------------
userkey  | Userkey of the secondary user
deveui  | Shared Device eui
access_token | Access token to be used with api.


## Get keyco finder secondary user lists

```shell

curl --request GET 'http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofindersecondaryuserlist/' --data 'deveui=d025cd0cd5a354a5&access_token=19f5ad9e-bf82-493e-aef0-d09daac55222'

```
> The above command includes JSON body and  returns JSON structured like this:

```json

{
"status": "Success",
"total": 1,
"statuscode": 200,
"listKeycofinderuserinfo":[
{
"user_key": "45c73686c5c0bc1b400a394ad356d164451fc905",
"pin_code": "12345",
"user_name": "QIvzeME9quQwbrGrgj07b6Uuib53_Ashok soni",
"user_phone_num": null,
"phone_type": "Android",
"register_date": "2017-11-29 08:51:24",
"gcmid": "18213a95-315c-41a9-a4bc-f339183d3c44",
"email": null
}
]
}

{
“Status”: “Fail,deveui format is wrong”,
"statuscode": 500
}

```
Get the keyco finder secondary user lists of specific shared device

### HTTP Request

`GET  http://keycoiot.solu-m.com/keyco-crowd/iotrestapi/api/get_keycofindersecondaryuserlist? deveui={deveui}&access_token={access_token}`

### Query Parameters

Parameter | Description
--------- | ------------
deveui  | Shared Device eui
access_token | Access token to be used with api.









