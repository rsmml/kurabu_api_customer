# API Integration Documentation

This documentation provides information on how to integrate our API endpoints to retrieve news articles, public events, and internal events. Please follow the instructions below to utilize the endpoints effectively.

## Index

- [Getting News Articles](#getting-news-articles)
  - [All Published News Articles](#1-all-published-news-articles)
  - [Published News Articles with Date Parameters](#2-published-news-articles-with-date-parameters)
- [Public Events](#public-events)
- [All Events](#all-events)
- [Getting Authorization Token](#getting-authorization-token)
  - [Admin LOGIN - TOKEN Copy](#admin-login---token-copy)

## Getting News Articles

### 1. All Published News Articles

**Endpoint:**

- Method: GET
- URL: `https://api.kurabu.com/v1/club-subdomain/[CLUB_SUBDOMAIN]/news`

**Request:**
```shell
curl https://api.kurabu.com/v1/club-subdomain/my_club_subdomain/news
```
**Response:**
```json
{
  "articles": [
    {
      "body": "",
      "categories": [],
      "cover_image_url": "",
      "featured": "",
      "id": "",
      "image_credit": "",
      "like_count": "",
      "preview_text": "",
      "publishing_date": "",
      "slug": "",
      "title": "",
      "updated_at": "",
    }
  ],
  "featured_articles": []
}
```
---

### 2. Published News Articles with Date Parameters

**Endpoint:**

- Method: GET
- URL: `https://api.kurabu.com/v1/club-subdomain/[CLUB_SUBDOMAIN]/news`

**Query Parameters:**

| Key    | Value (optional)       | Description |
| ------ | ------------ | ------------------------- |
| from   | 2023-04-01 / 2023-04-01T00:00:00   | Starting date (YYYY-MM-DD / YYYY-MM-DDTHH:MM:SS) |
| until  | 2023-12-01 / 2023-04-01T00:00:00   | Ending date (YYYY-MM-DD / YYYY-MM-DDTHH:MM:SS)  |

**Request:**
```shell
curl https://api.kurabu.com/v1/club-subdomain/my_club_subdomain/news?from=2023-04-01&until=2023-12-01
```
**Response:**
```json
{
  "articles": [],
  "featured_articles": []
}
```

---

## Public Events

**Endpoint:**

- Method: GET
- URL: `https://api.kurabu.com/v1/club-subdomain/[CLUB_SUBDOMAIN]/public_events`

**Query Parameters:**

| Key    | Value (required)       | Description            |
| ------ | ------------ | ------------------------- |
| from   | 2023-05-12 / 2023-05-12T00:00:00   | Starting date (YYYY-MM-DD / YYYY-MM-DDTHH:MM:SS) |
| until  | 2023-05-13 / 2023-05-13T00:00:00  | Ending date (YYYY-MM-DD / YYYY-MM-DDTHH:MM:SS)   |

**Request:**
```shell
curl https://api.kurabu.com/v1/club-subdomain/my_club_subdomain/public_events?from=2023-04-01&until=2023-12-01
```
**Response:**
```json
{
  "public_events": [
    {
      "description": "",
      "end_date": "",
      "end_time": "",
      "id": "",
      "image_url": "",
      "location": "",
      "location_info": "",
      "max_participants": "",
      "min_participants": "",
      "name": "",
      "start_date": "",
      "start_time": "",
    }
  ]
}
```

---

## All Events

**Endpoint:**

- Method: GET
- URL: `https://api.kurabu.com/v1/club-subdomain/[CLUB_SUBDOMAIN]/events`

**Headers:**

| Key            | Value  (required)           | Description                   |
| -------------- | ----------------- | ----------------------------- |
| Authorization | Bearer {{token}}  | Bearer token for authentication |

Please check [Getting Authorization Token](#getting-authorization-token) to get the Bearer tocken.

**Query Parameters:**

| Key    | Value (required)        | Description               |
| ------ | ------------ | ------------------------- |
| from   | 2023-05-01   | Starting date (YYYY-MM-DD) |
| until  | 2023-05-31   | Ending date (YYYY-MM-DD)   |

**Request:**
```shell
curl -X GET https://api.kurabu.com/v1/club-subdomain/my_club_subdomain/events?from=2023-04-01&until=2023-12-01 \
-H "Authorization: Bearer YOUR_TOKEN"
```
**Response:**
```json
{
  "internal_events": [
    {
      "description": "",
      "end_date": "",
      "end_time": "",
      "id": "",
      "image_url": "",
      "location": "",
      "location_info": "",
      "max_participants": "",
      "min_participants": "",
      "name": "",
      "start_date": "",
      "start_time": "",
    }
  ],
  "public_events": []
}
```

---

## Getting Authorization Token

### Admin LOGIN - TOKEN Copy

**Endpoint:**

- Method: POST
- Type: RAW
- URL: `https://api.kurabu.com/v1/token`

**Body:**

```json
{
    "admin": {
        "email": "your@admin.email",
        "password": "password",
        "club_subdomain": "club_subdomain"
    }
}
```

**Response:**

```json
{
    "token": "123ABCXYZ"
}
```

### Make sure to replace the following values in the above examples:

- [CLUB_SUBDOMAIN] with the appropriate club subdomain.
- {{token}} with the actual bearer token received from the authentication endpoint.
- "your@admin.email" with the admin email.
- "password" with the admin password.

Please refer to the API documentation for further details on the request/response formats and additional functionalities.

