---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - http

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Kittn API
---

# Introduction

Welcome to the Gotovo API!

# Authentication

> URL

```http
https://gotovo-api-staging.fly.dev/api/auth
```
> Success response body

```json
{
    "user": {
        "email": "user@user.com",
        "first_name": "Вася",
        "last_name": "Готовий",
        "phone": "380933456789",
        "theme": "light",
        "role": "default",
        "delivery_point": {
            "lat": null,
            "lng": null
        },
        "location": {
            "lat": null,
            "lng": null
        },
        "delivery_address": null,
        "working": false,
        "guest": false,
        "telegram_id": null,
        "picture": false
    }
}
```

> Success response header

```json
{
      "access-token": "Uq9TmrhxylU90bLQcfrMAw",
      "client": "7qlM_XwZIQihDuFvGIyTNA",
      "last_name": "Готовий",
      "expiry": 1675455256,
      "uid": "user@user.com"
}
```

### Register user

`POST https://gotovo-api-staging.fly.dev/api/auth`

#### Query Parameters

Parameter | Required | Type
--------- | ------- | -----------
email | true | string
first_name | true | string
last_name | true | string
phone | true | string
password | true | string
password_confirmation | false | string

## Login user

> URL

```http
https://gotovo-api-staging.fly.dev/api/auth/sign_in
```

> Success response body

```json
{
    "user": {
        "email": "user@user.com",
        "first_name": "Вася",
        "last_name": "Готовий",
        "phone": "380933456789",
        "theme": "light",
        "role": "default",
        "delivery_point": {
            "lat": null,
            "lng": null
        },
        "location": {
            "lat": null,
            "lng": null
        },
        "delivery_address": null,
        "working": false,
        "guest": false,
        "telegram_id": null,
        "picture": false
    }
}
```

> Success response header

```json
{
      "access-token": "Uq9TmrhxylU90bLQcfrMAw",
      "client": "7qlM_XwZIQihDuFvGIyTNA",
      "last_name": "Готовий",
      "expiry": 1675455256,
      "uid": "user@user.com"
}
```

`POST https://gotovo-api-staging.fly.dev/api/auth/sign_in`

### Query Parameters

Parameter | Required | Type
--------- | ------- | -----------
email | true | string
password | true | string

# Restaurants

> URL

```http
https://gotovo-api-staging.fly.dev/api/area_restaurants
```

> Success response body

```json
{
    "success": true,
    "restaurants": {
        "yurov-pub": {
            "id": 33,
            "name": "Yurov Pub",
            "slug": "yurov-pub",
            "description": "<p>Ми Yurov-Pub! Ми постійно розвиваємося, надихаємо та дивуємо! В нас затишна атмосфера, різноманітній бар, чудова кухня та завжди привітний персонал! Запрошуємо гарно провести час разом з нами! Також не забувайте про відгуки, адже ваша думка дуже важлива для нас! #korets_yurov_pubі</p>",
            "latitude": "50.619183",
            "longitude": "27.158462",
            "customer_phone": "380933523233",
            "rating": "2.4",
            "ratings_count": 5,
            "do_packing?": true,
            "instagram": "http://instagram.com/yurov.pub",
            "facebook": "http://facebook/yurov.pub",
            "website": "http://yurov.pub/ua/home",
            "package_price": 7,
            "main_photo_id": 37,
            "payment_provider": "liqpay",
            "terminal": true,
            "qr_pay": true,
            "allow_share_bill": true,
            "delivery_compensation": 0,
            "tips_url": null,
            "separate_delivery_pay": true,
            "photos": [
                {
                    "id": 37,
                    "description": null,
                    "photo": "https://res.cloudinary.com/dpukpixsc/image/upload/c_scale,w_400/q_80/gyxg31g91modls53bmorpd2lzunm"
                }
            ],
            "dishes_count": 25,
            "packable_dishes_count": 17
        }
    }
}
```
### Get local restaurants in radius

`GET https://gotovo-api-staging.fly.dev/api/area_restaurants`

#### Query Parameters

Parameter | Required | Type
--------- | ------- | -----------
location | false | array [latitude, longitude]
radius | false | integer (Default 10Km)

## Get restaurant

> URL

```http
https://gotovo-api-staging.fly.dev/api/restaurants/:slug
```

> Success response body

```json
{
    "success": true,
    "restaurant": {
        "id": 33,
        "name": "Yurov Pub",
        "slug": "yurov-pub",
        "description": "<p>Ми Yurov-Pub! Ми постійно розвиваємося, надихаємо та дивуємо! В нас затишна атмосфера, різноманітній бар, чудова кухня та завжди привітний персонал! Запрошуємо гарно провести час разом з нами! Також не забувайте про відгуки, адже ваша думка дуже важлива для нас! #korets_yurov_pubі</p>",
        "latitude": "50.619183",
        "longitude": "27.158462",
        "customer_phone": "380933523233",
        "rating": "2.4",
        "ratings_count": 5,
        "do_packing?": true,
        "instagram": "http://instagram.com/yurov.pub",
        "facebook": "http://facebook/yurov.pub",
        "website": "http://yurov.pub/ua/home",
        "package_price": 7,
        "main_photo_id": 37,
        "payment_provider": "liqpay",
        "terminal": true,
        "qr_pay": true,
        "allow_share_bill": true,
        "delivery_compensation": 0,
        "tips_url": null,
        "separate_delivery_pay": true,
        "photos": [
            {
                "id": 37,
                "description": null,
                "photo": "https://res.cloudinary.com/dpukpixsc/image/upload/c_scale,w_400/q_80/gyxg31g91modls53bmorpd2lzunm"
            }
        ],
        "dishes_count": 25,
        "packable_dishes_count": 17
    }
}
```

`GET https://gotovo-api-staging.fly.dev/api/restaurants/:slug`

#### Query Parameters

Parameter | Required | Type
--------- | ------- | -----------
menu | false | boolean (Get with menu categories included)
table_id | false | integer (Get with table included)

# Dishes

> URL

```http
https://gotovo-api-staging.fly.dev/api/dishes
```

> Success response body

```json
{
    "success": true,
    "dishes": {
        " 98": {
            "id": 98,
            "working_hours": {
                "default": true,
                "working_hours": {
                    "Fri": {
                        "end_time": "2000-01-01 22:00",
                        "start_time": "2000-01-01 09:00"
                    },
                    "Mon": {
                        "end_time": "2000-01-01 22:00",
                        "start_time": "2000-01-01 09:00"
                    },
                    "Sat": {
                        "end_time": "2000-01-01 22:00",
                        "start_time": "2000-01-01 09:00"
                    },
                    "Sun": {
                        "end_time": "2000-01-01 22:00",
                        "start_time": "2000-01-01 09:00"
                    },
                    "Thu": {
                        "end_time": "2000-01-01 22:00",
                        "start_time": "2000-01-01 09:00"
                    },
                    "Tue": {
                        "end_time": "2000-01-01 22:00",
                        "start_time": "2000-01-01 09:00"
                    },
                    "Wed": {
                        "end_time": "2000-01-01 22:00",
                        "start_time": "2000-01-01 09:00"
                    }
                }
            },
            "category_id": 1,
            "has_package": false,
            "content": "Перші страви",
            "available": true,
            "position": 0,
            "sub_categories": [
                {
                    "id": 127,
                    "name": "1",
                    "position": null
                },
                {
                    "id": 133,
                    "name": "2",
                    "position": null
                }
            ],
            "packable_dishes_count": 2
        }
    }
}
```
### Get restaurant dishes categories

`GET https://gotovo-api-staging.fly.dev/api/dishes`

#### Query Parameters

Parameter | Required | Type
--------- | ------- | -----------
restaurant_id | true | integer

## Get category dishes

> URL

```http
https://gotovo-api-staging.fly.dev/api/dishes/category_dishes
```

> Success response body

```json
{
    "success": true,
    "dishes": [
        {
            "id": 633,
            "description": "Опаньки",
            "price": "1.0",
            "available": true,
            "weight": "",
            "restaurant_id": 33,
            "position": 0,
            "packable": true,
            "sub_category_id": 127,
            "delivery_price": "0.0",
            "picture_url": null,
            "category_dish_id": 98,
            "package_capacity": 1,
            "box_id": null,
            "new_dish": false,
            "name": "Териякі",
            "box": false,
            "likes": 0,
            "dislikes": 0,
            "dish_variations": {}
        }
    ]
}
```

`GET https://gotovo-api-staging.fly.dev/api/dishes/category_dishes`

#### Query Parameters

Parameter | Required | Type
--------- | ------- | -----------
category_id | true | integer (id field from previous request)

## Get all dishes

> URL

```http
https://gotovo-api-staging.fly.dev/api/dishes/all
```

> Success response body

```json
{
    "success": true,
    "dishes": {
        " 98": {
            "id": 98,
            "working_hours": {
                "default": true,
                "working_hours": {
                    "Fri": {
                        "end_time": "2000-01-01 22:00",
                        "start_time": "2000-01-01 09:00"
                    },
                    "Mon": {
                        "end_time": "2000-01-01 22:00",
                        "start_time": "2000-01-01 09:00"
                    },
                    "Sat": {
                        "end_time": "2000-01-01 22:00",
                        "start_time": "2000-01-01 09:00"
                    },
                    "Sun": {
                        "end_time": "2000-01-01 22:00",
                        "start_time": "2000-01-01 09:00"
                    },
                    "Thu": {
                        "end_time": "2000-01-01 22:00",
                        "start_time": "2000-01-01 09:00"
                    },
                    "Tue": {
                        "end_time": "2000-01-01 22:00",
                        "start_time": "2000-01-01 09:00"
                    },
                    "Wed": {
                        "end_time": "2000-01-01 22:00",
                        "start_time": "2000-01-01 09:00"
                    }
                }
            },
            "has_package": false,
            "category_id": 1,
            "content": "Перші страви",
            "available": true,
            "position": 0,
            "sub_categories": [
                {
                    "id": 127,
                    "name": "1",
                    "position": null
                },
                {
                    "id": 133,
                    "name": "2",
                    "position": null
                }
            ],
            "subItems": [
                {
                    "id": 636,
                    "description": "З мощним хлібом та петрушкою, об'їститися можна. Лупашить не по дєтскі",
                    "price": "99.0",
                    "available": true,
                    "weight": "",
                    "restaurant_id": 33,
                    "position": 0,
                    "packable": false,
                    "sub_category_id": 127,
                    "delivery_price": "0.0",
                    "picture_url": null,
                    "category_dish_id": 98,
                    "package_capacity": 1,
                    "box_id": null,
                    "new_dish": false,
                    "name": "Солянка",
                    "box": false,
                    "likes": 0,
                    "dislikes": 0,
                    "dish_variations": {}
                }
            ]
        }
    }
}
```

`GET https://gotovo-api-staging.fly.dev/api/dishes/all`

#### Query Parameters

Parameter | Required | Type
--------- | ------- | -----------
restaurant_id | true | integer

# Kittens

## Get All Kittens

```http
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

