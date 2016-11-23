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

> The above command does not return anything expect HTTP Status code 200. 

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

