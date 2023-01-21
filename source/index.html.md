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

# Users

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

<aside class="notice">
  Response includes `access-token`, `client`, `uid` in headers. So save them for further using of authorized access
</aside>

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

<aside class="notice">
  Response includes `access-token`, `client`, `uid` in headers. So save them for further using of authorized access
</aside>

## Get user

> URL

```http
https://gotovo-api-staging.fly.dev/api/profile
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

`GET https://gotovo-api-staging.fly.dev/api/profile`

<aside class="warning">
  Request should be authorized. So `access-token`, `client`, `uid` must be included in request headers.
</aside>


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

# Orders

> URL

```http
https://gotovo-api-staging.fly.dev/api/orderings
```

> Success response body

```json
{
    "success": true,
    "order": {
        "id": 1625,
        "amount": "117.33",
        "status": "payed",
        "time": 1674304800000,
        "kind": "to_go",
        "restaurant_id": 33,
        "invoice_url": null,
        "when_ready": true,
        "payment_type": "after_pay",
        "persons": null,
        "description": null,
        "delivery_point": null,
        "delivery_user_id": null,
        "packing_price": "7.0",
        "delivery_price": "0.0",
        "delivery_address": null,
        "phone": null,
        "shared": null,
        "share_token": null,
        "separate_delivery_pay": false,
        "created_at": "21.01.2023 14:20",
        "updated_at": "21.01.2023 14:20",
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
            "instagram": "http://yurov.pub/ua/home",
            "facebook": "http://yurov.pub/ua/home",
            "website": "http://yurov.pub/ua/home",
            "package_price": 7,
            "main_photo_id": 37,
            "payment_provider": "liqpay",
            "terminal": true,
            "qr_pay": true,
            "allow_share_bill": true,
            "delivery_compensation": 0,
            "tips_url": null,
            "separate_delivery_pay": true
        },
        "dishes": [
            {
                "id": 105,
                "description": "",
                "price": "40.33",
                "available": true,
                "weight": null,
                "restaurant_id": 33,
                "position": 0,
                "packable": true,
                "sub_category_id": null,
                "delivery_price": "0.0",
                "picture_url": null,
                "category_dish_id": 39,
                "package_capacity": 1,
                "box_id": null,
                "new_dish": false,
                "name": "Лимонад",
                "box": false,
                "likes": 0,
                "dislikes": 0,
                "dish_variations": {},
                "photo": null,
                "quantity": 1,
                "dish_variation": false
            }
        ],
        "delivery_user": {},
        "ordered_user": {
            "name": "Гість",
            "phone": "380933332211"
        },
        "table": false,
        "versions": {},
        "pay_shares": {}
    },
    "user": 
        {
            "email": "guest_7289d982-fbf0-4168-b6cf-df82f3494138@example.com",
            "first_name": "Гість",
            "last_name": "Хоче їсти",
            "phone": "380633332211",
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
            "guest": true,
            "telegram_id": null,
            "picture": false
        }
}
```

> Success response header (If first time order)

```json
{
      "access-token": "Uq9TmrhxylU90bLQcfrMAw",
      "client": "7qlM_XwZIQihDuFvGIyTNA",
      "last_name": "Готовий",
      "expiry": 1675455256,
      "uid": "user@user.com"
}
```

### Create order

`POST https://gotovo-api-staging.fly.dev/api/orderings`

#### Query Parameters

Parameter | Required | Type
--------- | ------- | -----------
restaurant_id | true | integer
order_type | true | one of ['to_visit', 'to_go', 'delivery', 'on_table']
payment_type | true | one of ['pre_pay', 'after_pay']
orders | true | array [{id: 33 (dish_id), quantity: 2}, {...}]
when_ready | false | boolean
time | false | boolean (should be set if `when_ready = false`)
shared | false | boolean (is order divided by users for `pre_pay` payment_type)
delivery_point | false | array [latitude, longitude] (Required for `delivery` order_type)
delivery_address | false | string (for `delivery` order_type)
description | false | string (Special demands)
persons | false | integer (Number of users for `to_visit` order_type)
table_id | false | integer (Selected table for `to_visit` order_type)
phone | false | string (Required if is first time order)
first_name | false | string (User name)

<aside class="notice">
  If first time order. User will be automaticaly created with `phone` number and returned in response body `{user: {...}}`.
  Also in response header will be authorization `access-token`, `client`, `uid` which should be used along 
  with resquest in header for next authorized orders 
</aside>

## Get all user orders

> URL

```http
https://gotovo-api-staging.fly.dev/api/orderings
```

> Success response body

```json
{
    "success": true,
    "orders": [
        {
            "id": 1627,
            "amount": "117.33",
            "status": "payed",
            "time": 1674305250000,
            "kind": "to_go",
            "restaurant_id": 33,
            "invoice_url": null,
            "when_ready": true,
            "payment_type": "after_pay",
            "persons": null,
            "description": null,
            "delivery_point": null,
            "delivery_user_id": null,
            "packing_price": "7.0",
            "delivery_price": "0.0",
            "delivery_address": null,
            "phone": null,
            "shared": null,
            "share_token": null,
            "separate_delivery_pay": false,
            "created_at": "21.01.2023 14:27",
            "updated_at": "21.01.2023 14:27",
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
                "instagram": "http://yurov.pub/ua/home",
                "facebook": "http://yurov.pub/ua/home",
                "website": "http://yurov.pub/ua/home",
                "package_price": 7,
                "main_photo_id": 37,
                "payment_provider": "liqpay",
                "terminal": true,
                "qr_pay": true,
                "allow_share_bill": true,
                "delivery_compensation": 0,
                "tips_url": null,
                "separate_delivery_pay": true
            },
            "dishes": [
                {
                    "id": 105,
                    "description": "",
                    "price": "40.33",
                    "available": true,
                    "weight": null,
                    "restaurant_id": 33,
                    "position": 0,
                    "packable": true,
                    "sub_category_id": null,
                    "delivery_price": "0.0",
                    "picture_url": null,
                    "category_dish_id": 39,
                    "package_capacity": 1,
                    "box_id": null,
                    "new_dish": false,
                    "name": "Лимонад",
                    "box": false,
                    "likes": 0,
                    "dislikes": 0,
                    "dish_variations": {},
                    "photo": null,
                    "quantity": 1,
                    "dish_variation": false
                }
            ],
            "delivery_user": {},
            "ordered_user": {
                "name": "Гість",
                "phone": "380633332211"
            },
            "table": false,
            "versions": {},
            "pay_shares": {}
        }
    ],
    "total_pages": 1
}
```

`GET https://gotovo-api-staging.fly.dev/api/orderings`

#### Query Parameters

Parameter | Required | Type
--------- | ------- | -----------
page | false | integer (Page number)

<aside class="warning">
  Request should be authorized. So `access-token`, `client`, `uid` must be included in request headers.
</aside>

## Get user order

> URL

```http
https://gotovo-api-staging.fly.dev/api/orderings/:id
```

> Success response body

```json
{
    "success": true,
    "order": {
        "id": 1627,
        "amount": "117.33",
        "status": "payed",
        "time": 1674305250000,
        "kind": "to_go",
        "restaurant_id": 33,
        "invoice_url": null,
        "when_ready": true,
        "payment_type": "after_pay",
        "persons": null,
        "description": null,
        "delivery_point": null,
        "delivery_user_id": null,
        "packing_price": "7.0",
        "delivery_price": "0.0",
        "delivery_address": null,
        "phone": null,
        "shared": null,
        "share_token": null,
        "separate_delivery_pay": false,
        "created_at": "21.01.2023 14:27",
        "updated_at": "21.01.2023 14:27",
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
            "instagram": "http://yurov.pub/ua/home",
            "facebook": "http://yurov.pub/ua/home",
            "website": "http://yurov.pub/ua/home",
            "package_price": 7,
            "main_photo_id": 37,
            "payment_provider": "liqpay",
            "terminal": true,
            "qr_pay": true,
            "allow_share_bill": true,
            "delivery_compensation": 0,
            "tips_url": null,
            "separate_delivery_pay": true
        },
        "dishes": [
            {
                "id": 105,
                "description": "",
                "price": "40.33",
                "available": true,
                "weight": null,
                "restaurant_id": 33,
                "position": 0,
                "packable": true,
                "sub_category_id": null,
                "delivery_price": "0.0",
                "picture_url": null,
                "category_dish_id": 39,
                "package_capacity": 1,
                "box_id": null,
                "new_dish": false,
                "name": "Лимонад",
                "box": false,
                "likes": 0,
                "dislikes": 0,
                "dish_variations": {},
                "photo": null,
                "quantity": 1,
                "dish_variation": false
            }
        ],
        "delivery_user": {},
        "ordered_user": {
            "name": "Гість",
            "phone": "380633332211"
        },
        "table": false,
        "versions": {},
        "pay_shares": {}
    }
}
```

`GET https://gotovo-api-staging.fly.dev/api/orderings/:id`

#### Query Parameters

Parameter | Required | Type
--------- | ------- | -----------
share_token | false | string (Required for `shared` order)

<aside class="warning">
  Request should be authorized. So `access-token`, `client`, `uid` must be included in request headers.
</aside>

