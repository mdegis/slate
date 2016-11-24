---
title: Shark API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Shark API! You can use our API to upload images to Ocean API endpoints or get generated reports, which can get information abou the project.

This example API documentation page was created with [Slate](https://github.com/mdegis/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

Shark uses API keys to allow access to the API. You cannot register a new Shark API key, but if you have an auditor account you may login with it.
Shark expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: "Bearer $TOKEN$"`

<aside class="notice">
You must replace <code>$TOKEN$</code> with your personal API key.
</aside>

## Request Token

```shell
curl -X POST -H "Content-Type: application/json" -H "Cache-Control: no-cache" -d '{
  "client_id": "meowmeowmeow,
  "client_secret": "weomweomweom",
  "grant_type": "password",
  "username": "test@vispera.co",
  "password": "youraccountpassword",
  "scope": "shark"
}' "http://ocean.vispera.co/oauth/token"
```

> Make sure to replace `meowmeowmeow` with your client id and `weomweomweom` with your client secret.

> The above command returns JSON structured like this:

```json
{
  "access_token": "5db7fd1b3561f448b8b488db4deebc710aa153ce136e3c251e91f3522b1208cb",
  "token_type": "bearer",
  "expires_in": 7200,
  "refresh_token": "4c221f165d2ac5eddb3ce171b1e6d4ae0877111e47932862a745d50875d426ba",
  "scope": "shark",
  "created_at": 1479907224
}
```


### HTTP Request

`POST http://ocean.vispera.co/oauth/token`

### Query Parameters

Parameter | Description
--------- | -----------
client_id | Client ID that provided to you.
client_secret | Client secret that provided to you.
grant_type | Use "password" to get token.
username | Username of your auditor account.
password | Password of your auditor account.
scope | Scope of your token, in this case it is "shark"

## Request Token with Refresh Token

```shell
curl -X POST -H "Content-Type: application/json" -H "Cache-Control: no-cache" -d '{
  "client_id": "meowmeowmeow,
  "client_secret": "weomweomweom",
  "grant_type": "refresh_token",
  "refresh_token": "yourrefreshtoken"
}' "http://ocean.vispera.co/oauth/token"
```

> Make sure to replace `meowmeowmeow` with your client id, `weomweomweom` with your client secret `yourrefreshtoken` with refresh token.

> The above command returns JSON structured like this:

```json
{
  "access_token": "5db7fd1b3561f448b8b488db4deebc710aa153ce136e3c251e91f3522b1208cb",
  "token_type": "bearer",
  "expires_in": 7200,
  "refresh_token": "4c221f165d2ac5eddb3ce171b1e6d4ae0877111e47932862a745d50875d426ba",
  "scope": "shark",
  "created_at": 1479907224
}
```

### HTTP Request

`POST http://ocean.vispera.co/oauth/token`

### Query Parameters

Parameter | Description
--------- | -----------
client_id | Client ID that provided to you.
client_secret | Client secret that provided to you.
grant_type | Use "password" to get token.
refresh_token | Your refresh token.

## Revoke Token 

```shell
curl -X POST -H "Content-Type: application/json" -H "Cache-Control: no-cache" '{
	"token": "5db7fd1b3561f448b8b488db4deebc710aa153ce136e3c251e91f3522b1208cb"
}' "http://localhost:3000/oauth/revoke"
```

> The above command does not return anything expect HTTP Status code 204. 

### HTTP Request

`POST http://ocean.vispera.co/oauth/revoke`

### Query Parameters

Parameter | Description
--------- | -----------
token | Token that you want to revoke.

# Auditor

Get logged auditor.

```shell
curl -X GET -H "Authorization: Bearer $TOKEN$" 
-H "Cache-Control: no-cache" -H "http://localhost:3000/api/shark/v1/auditors/me"
```

> The above command returns JSON structured like this:

```json
{
  "id": 479,
  "username": "test",
  "name": "John",
  "surname": "Snow",
  "email": "test@vispera.co"
}
```

### HTTP Request

`GET http://ocean.vispera.co/api/shark/v1/auditors/me`

# Assignment
## Get All Assignments

```shell
curl -X GET -H "Authorization: Bearer $TOKEN$" "http://localhost:3000/api/shark/v1/assignments"
```

Get all assignments for logged in auditor.

> The above command returns JSON structured like this:

```json
[
  {
    "id": 630,
    "name": "carrefourSA_2016_altayçeşme",
    "description": "CarrefourSA Altayçeşme 2016",
    "stores_todo_codes": [
      "Carrefour001"
    ],
    "updated_at": "2016-11-08T12:35:13.483Z",
    "internal_project_uuid": "5dd8134e-20e3-4899-ac4c-2b28b13203ae",
    "device_reports": false,
    "reference_image_sets": [
      {
        "id": 899,
        "survey_id": 20,
        "activity_category_id": 59,
        "product_group_id": "69763366-27d5-4aab-b903-b30fb2ca8cc5",
        "image_set_id": "3de2916e-2833-4744-b08a-7275a90f05db",
        "store_code": "Carrefour001",
        "display_type": "shelf",
        "mosaic": {
          "xxxsmall": "/uploads/image_set_report/mosaic/6392/xxxsmall_a1835f7310.jpg",
          "xxsmall": "/uploads/image_set_report/mosaic/6392/xxsmall_a1835f7310.jpg",
          "xsmall": "/uploads/image_set_report/mosaic/6392/xsmall_a1835f7310.jpg",
          "small": "/uploads/image_set_report/mosaic/6392/small_a1835f7310.jpg",
          "medium": "/uploads/image_set_report/mosaic/6392/medium_a1835f7310.jpg",
          "large": "/uploads/image_set_report/mosaic/6392/large_a1835f7310.jpg",
          "xlarge": "/uploads/image_set_report/mosaic/6392/xlarge_a1835f7310.jpg",
          "xxlarge": "/uploads/image_set_report/mosaic/6392/xxlarge_a1835f7310.jpg",
          "xxxlarge": "/uploads/image_set_report/mosaic/6392/xxxlarge_a1835f7310.jpg",
          "original": "/uploads/image_set_report/mosaic/6392/a1835f7310.jpg"
        },
        "title": null,
        "description": null
      },
      {
        "id": 898,
        "survey_id": 20,
        "activity_category_id": 59,
        "product_group_id": "69763366-27d5-4aab-b903-b30fb2ca8cc5",
        "image_set_id": "3de2916e-2833-4744-b08a-7275a90f05db",
        "store_code": "Carrefour001",
        "display_type": "shelf",
        "mosaic": {
          "xxxsmall": "/uploads/image_set_report/mosaic/6392/xxxsmall_a1835f7310.jpg",
          "xxsmall": "/uploads/image_set_report/mosaic/6392/xxsmall_a1835f7310.jpg",
          "xsmall": "/uploads/image_set_report/mosaic/6392/xsmall_a1835f7310.jpg",
          "small": "/uploads/image_set_report/mosaic/6392/small_a1835f7310.jpg",
          "medium": "/uploads/image_set_report/mosaic/6392/medium_a1835f7310.jpg",
          "large": "/uploads/image_set_report/mosaic/6392/large_a1835f7310.jpg",
          "xlarge": "/uploads/image_set_report/mosaic/6392/xlarge_a1835f7310.jpg",
          "xxlarge": "/uploads/image_set_report/mosaic/6392/xxlarge_a1835f7310.jpg",
          "xxxlarge": "/uploads/image_set_report/mosaic/6392/xxxlarge_a1835f7310.jpg",
          "original": "/uploads/image_set_report/mosaic/6392/a1835f7310.jpg"
        },
        "title": null,
        "description": null
      }
    ],
    "active": true,
    "period": "always",
    "route": {
      "id": 595,
      "key": "route_BNQT8Bxz",
      "name": "carrefourSA_2016_route",
      "title": "CarrefourSA 2016 route",
      "updated_at": "2016-11-07T14:53:12.437Z",
      "stores": [
        {
          "code": "Carrefour001",
          "name": "CarrefourSA Altayçeşme",
          "hint": "Carrefour001 CarrefourSA Altayçeşme İstanbul",
          "store_type": "Market",
          "latitude": null,
          "longitude": null,
          "address": " ",
          "district": "",
          "city": "İstanbul",
          "state": "",
          "country": ""
        }
      ]
    },
    "project": {
      "id": 19,
      "key": "project_RF+0AdMP",
      "name": "Carrefour Altaycesme 2016",
      "description": "CarrefourSA Altaycesme 2016",
      "active": true
    },
    "survey": {
      "id": 20,
      "key": "survey_uFJZEbNW",
      "name": "carrefourSA_altaycesme_2016_survey",
      "description": "CarrefourSA Altaycesme 2016 Survey",
      "hybrid": false,
      "can_send_actions": false,
      "can_send_activities": false,
      "visit_seal_strategy": "manuel",
      "visit_seal_interval": 0,
      "start_time": "2016-10-12T09:00:00.000Z",
      "end_time": "2018-10-17T09:00:00.000Z",
      "activity_categories": [
        {
          "id": 59,
          "key": "shpyalco",
          "name": "CarrefourSA_Altaycesme_2016_shelf",
          "title": "Raf",
          "place": "list",
          "action_type": "image",
          "image_set_type": "shelf",
          "questionnaire": null,
          "position": 1,
          "visible": true,
          "min_action_count": 0,
          "max_action_count": 99,
          "min_activity_count": 0,
          "max_activity_count": 99,
          "max_image_set_count": 99,
          "product_groups": [
            {
              "id": "69763366-27d5-4aab-b903-b30fb2ca8cc5",
              "name": "carrefoursa_2016_food",
              "title": "Yiyecek"
            }
          ]
        },
        {
          "id": 61,
          "key": "fthixlbw",
          "name": "CarrefourSA_Altaycesme_2016_cooler",
          "title": "Soğutucu",
          "place": "list",
          "action_type": "image",
          "image_set_type": "cooler",
          "questionnaire": null,
          "position": 3,
          "visible": true,
          "min_action_count": 0,
          "max_action_count": 99,
          "min_activity_count": 0,
          "max_activity_count": 99,
          "max_image_set_count": 99,
          "product_groups": [
            {
              "id": "69763366-27d5-4aab-b903-b30fb2ca8cc5",
              "name": "carrefoursa_2016_food",
              "title": "Yiyecek"
            }
          ]
        },
        {
          "id": 60,
          "key": "kloqgjtz",
          "name": "CarrefourSA_Altaycesme_2016_display",
          "title": "Teşhir",
          "place": "list",
          "action_type": "image",
          "image_set_type": "display",
          "questionnaire": null,
          "position": 2,
          "visible": true,
          "min_action_count": 0,
          "max_action_count": 99,
          "min_activity_count": 0,
          "max_activity_count": 99,
          "max_image_set_count": 99,
          "product_groups": [
            {
              "id": "69763366-27d5-4aab-b903-b30fb2ca8cc5",
              "name": "carrefoursa_2016_food",
              "title": "Yiyecek"
            }
          ]
        }
      ],
      "can_device_receive_reports": false,
      "project_id": 19,
      "internal_project_uuid": "5dd8134e-20e3-4899-ac4c-2b28b13203ae",
      "can_select_reference_image_set": true,
      "active": true,
      "action_categories": [
        {
          "id": 59,
          "key": "shpyalco",
          "name": "CarrefourSA_Altaycesme_2016_shelf",
          "title": "Raf",
          "place": "list",
          "action_type": "image",
          "image_set_type": "shelf",
          "questionnaire": null,
          "position": 1,
          "visible": true,
          "min_action_count": 0,
          "max_action_count": 99,
          "min_activity_count": 0,
          "max_activity_count": 99,
          "max_image_set_count": 99,
          "product_groups": [
            {
              "id": "69763366-27d5-4aab-b903-b30fb2ca8cc5",
              "name": "carrefoursa_2016_food",
              "title": "Yiyecek"
            }
          ]
        },
        {
          "id": 61,
          "key": "fthixlbw",
          "name": "CarrefourSA_Altaycesme_2016_cooler",
          "title": "Soğutucu",
          "place": "list",
          "action_type": "image",
          "image_set_type": "cooler",
          "questionnaire": null,
          "position": 3,
          "visible": true,
          "min_action_count": 0,
          "max_action_count": 99,
          "min_activity_count": 0,
          "max_activity_count": 99,
          "max_image_set_count": 99,
          "product_groups": [
            {
              "id": "69763366-27d5-4aab-b903-b30fb2ca8cc5",
              "name": "carrefoursa_2016_food",
              "title": "Yiyecek"
            }
          ]
        },
        {
          "id": 60,
          "key": "kloqgjtz",
          "name": "CarrefourSA_Altaycesme_2016_display",
          "title": "Teşhir",
          "place": "list",
          "action_type": "image",
          "image_set_type": "display",
          "questionnaire": null,
          "position": 2,
          "visible": true,
          "min_action_count": 0,
          "max_action_count": 99,
          "min_activity_count": 0,
          "max_activity_count": 99,
          "max_image_set_count": 99,
          "product_groups": [
            {
              "id": "69763366-27d5-4aab-b903-b30fb2ca8cc5",
              "name": "carrefoursa_2016_food",
              "title": "Yiyecek"
            }
          ]
        }
      ],
      "rules": []
    }
  }
]
```

### HTTP Request

`GET http://ocean.vispera.co/api/shark/v1/assignments`

## Get Specific Assignment

Get a specific assignment with ID.

```shell
curl -X GET -H "Authorization: Bearer $TOKEN$" 
"http://localhost:3000/api/shark/v1/assignments/$ID$/stores/todo"
```

> The above command returns JSON structured like this:

```json
[
  {
    "code": "Carrefour001",
    "name": "CarrefourSA Altayçeşme",
    "hint": "Carrefour001 CarrefourSA Altayçeşme İstanbul",
    "store_type": "Market",
    "latitude": null,
    "longitude": null,
    "address": " ",
    "district": "",
    "city": "İstanbul",
    "state": "",
    "country": ""
  }
]
```

### HTTP Request

`GET http://ocean.vispera.co/api/shark/v1/assignments/$ID$/stores/todo`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the assignment to retrieve

# Data
## Get Data

```shell
curl -X GET -H "Authorization: Bearer $TOKEN$" "http://localhost:3000/api/shark/v1/data/version"
```

> The above command returns JSON structured like this:

```json
{
  "latest_update_at": "2016-11-08T12:35:13.483Z",
  "resource_key": "assignments/630-20161108123513483653000",
  "min_version_code": null
}
```

### HTTP Request

`GET http://localhost:3000/api/shark/v1/data/version`

## Post Data

```shell
curl --KEMAL
```

> The above command returns JSON structured like this:

```json
"KEMAL": {
    "Buralara": {"neler", "gelicek", undefined}
}
```

### HTTP Request

`POST http://localhost:3000/api/shark/v1/data/version`

### Query Parameters
Parameter | Description
--------- | -----------
KEMAL | KEMAL.
KEMAL | KEMAL.
KEMAL | KEMAL.


# Report

## Get All Reports 

```shell
curl -X GET -H "Authorization: Bearer $TOKEN$" "http://localhost:3000/api/shark/v1/reports"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id":6596,
    "type":"ImageSetReport",
    "visit_id":"bf0ad8d1-c0d2-456f-bcaf-5cad2e01e62a",
    "image_set_id":"26ccd17f-974a-489a-b6e6-f1880e108112",
    "store_name":"CarrefourSA Altayçeşme",
    "image_set_type":"Shelf",
    "url":"http://ocean.vispera.co/embedded/reports/6596",
    "updated_at":"2016-11-23T13:07:21.494Z"
  },
  {
    "id":6597,
    "type":"VisitReport",
    "visit_id":"bf0ad8d1-c0d2-456f-bcaf-5cad2e01e62a",
    "image_set_id":null,
    "store_name":"CarrefourSA Altayçeşme",
    "image_set_type":null,
    "url":"http://ocean.vispera.co/embedded/reports/6597",
    "updated_at":"2016-11-23T13:07:39.046Z"
  }
]
```

This endpoint retrieves all reports.

### HTTP Request

`GET http://localhost:3000/api/shark/v1/reports`

# Message

## Get All Messages

```shell
curl -X GET -H "Authorization: Bearer $TOKEN$" "http://localhost:3000/api/shark/v1/messages"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id":1,
    "title":"ImageSetReport",
    "content":"ImageSetReport",
    "created_at":"2016-11-23T13:07:21.494Z"
  }
]
```

This endpoint retrieves all messages.

### HTTP Request

`GET http://localhost:3000/api/shark/v1/messages`

# Image Service

```shell
curl -X PATCH -H "Authorization: Bearer $TOKEN$" -H "Content-Type: multipart/form-data" 
-F "file=@file.jpg" "http://localhost:3000/api/shark/v1/images/$IMAGE_ID$"
```

> The above command does not return anything expect HTTP Status code 204. 

Update an image.

### HTTP Request

`PATCH http://localhost:3000/api/shark/v1/images/$IMAGE_ID$`

### Query Parameters
Multipart form-data

Parameter | Description
--------- | -----------
file| New image file.

### URL Parameters

Parameter | Description
--------- | -----------
IMAGE_ID | The ID of the image to change. 

# Answer Service

```shell
curl -X PATCH -H "Authorization: Bearer $TOKEN$" -H "Content-Type: multipart/form-data" 
-F "file=@file.jpg|.mp4" "http://localhost:3000/api/shark/v1/answers/$ANSWER_ID$"
```

> The above command does not return anything expect HTTP Status code 204. 

### HTTP Request

`PATCH http://localhost:3000/api/shark/v1/answers/$ANSWER_ID$`

### Query Parameters
Multipart form-data

Parameter | Description
--------- | -----------
file| New image or video file.

<aside class="success">
Please note that file can be image or video.
</aside>

### URL Parameters

Parameter | Description
--------- | -----------
ANSWER_ID | The ID of the image or video to change. 

# GPS Log Service

```shell
curl -X POST -H "Authorization: Bearer $TOKEN$" -F "latitude=123.1" -F "longitude=123.1" 
-F "provider=satellite" -F "satellite_count=1" -F "recorded_at=2016-11-23T13:07:21.494Z" 
"http://localhost:3000/api/shark/v1/gps_logs"
```

> The above command does not return anything expect HTTP Status code 201. 

### HTTP Request

`POST http://localhost:3000/api/shark/v1/gps_logs`

### Query Parameters
Multipart form-data

Parameter | Description
--------- | -----------
latitude | Latitude of GPS coordinate.
longitude | Longitude of GPS coordinate.
provider | One of [satellite, cellular, wifi].
satellite_count | number of satellite.
recorded_at | Recored date and time of this log.

# Test

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

