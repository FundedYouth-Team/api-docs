---
weight: 16
title: Dates
---

# Dates

## [GET] - All Dates

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl "{{base_url}}/api/dates"
  -H "Authorization: Bearer your-api-key"
```

```php
# --- PHP ---

<?php
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/dates",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_HTTPHEADER => [
    "Authorization: Bearer your-api-key",
    "Content-Type: application/json"
  ],
]);

$response = curl_exec($curl);
curl_close($curl);
$data = json_decode($response, true);
?>
```

```python
# --- Python ---

import requests

url = "{{base_url}}/api/dates"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}

response = requests.get(url, headers=headers)
data = response.json()
```

```javascript
// --- Fetch ---

fetch("{{base_url}}/api/dates", {
  method: "GET",
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
})
  .then((response) => response.json())
  .then((data) => console.log(data));
```

```js
// --- Axios ---

const axios = require("axios");

const config = {
  method: "get",
  url: "{{base_url}}/api/dates",
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
};

axios(config)
  .then((response) => console.log(response.data))
  .catch((error) => console.error(error));
```

<aside class="notice">
This endpoint retrieves all dates in the vHub system.
</aside>

### HTTP Request

`GET {{base_url}}/api/dates`

```
Response Outputs
```

```json
{
  "success": true,
  "data": [
    {
      "id": 1,
      "user_id": 3,
      "dt_start": "2025-01-15T16:35:00",
      "dt_end": "2025-01-15T19:30:00"
    },
    {
      "id": 2,
      "user_id": 5,
      "dt_start": "2025-01-16T14:00:00",
      "dt_end": "2025-01-16T16:45:00"
    },
    {
      "id": 3,
      "user_id": 3,
      "dt_start": "2025-01-17T09:15:00",
      "dt_end": "2025-01-17T11:30:00"
    }
  ]
}
```

### Response Codes

| Status | Message                                            |
| ------ | -------------------------------------------------- |
| 200    | Success                                            |
| 201    | Authenticated. Success                             |
| 401    | Unauthorized access. Please provide a valid token. |

<aside class="success">
Remember proper date management ensures efficient scheduling!
</aside>

## [GET] - Dates by User Id

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl "{{base_url}}/api/dates/user/3"
  -H "Authorization: Bearer your-api-key"
```

```php
# --- PHP ---

<?php
$userId = 3;
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/dates/user/{$userId}",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_HTTPHEADER => [
    "Authorization: Bearer your-api-key",
    "Content-Type: application/json"
  ],
]);

$response = curl_exec($curl);
curl_close($curl);
$data = json_decode($response, true);
?>
```

```python
# --- Python ---

import requests

user_id = 3
url = f"{{base_url}}/api/dates/user/{user_id}"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}

response = requests.get(url, headers=headers)
data = response.json()
```

```javascript
// --- Fetch ---

const userId = 3;
fetch(`{{base_url}}/api/dates/user/${userId}`, {
  method: "GET",
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
})
  .then((response) => response.json())
  .then((data) => console.log(data));
```

```js
// --- Axios ---

const axios = require("axios");

const userId = 3;
const config = {
  method: "get",
  url: `{{base_url}}/api/dates/user/${userId}`,
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
};

axios(config)
  .then((response) => console.log(response.data))
  .catch((error) => console.error(error));
```

<aside class="notice">
This endpoint retrieves all dates for a specific user by their <strong>{ user_id }</strong>.
</aside>

### HTTP Request

`GET {{base_url}}/api/dates/user/{user_id}`

```
Response Outputs
```

```json
{
  "status": 200,
  "data": {
    "success": true,
    "data": [
      {
        "id": 1,
        "user_id": 3,
        "dt_start": "2025-01-15T16:35:00",
        "dt_end": "2025-01-15T19:30:00"
      },
      {
        "id": 3,
        "user_id": 3,
        "dt_start": "2025-01-17T09:15:00",
        "dt_end": "2025-01-17T11:30:00"
      }
    ]
  }
}
```

```json
{
  "status": 404,
  "data": {
    "success": false,
    "error": "User not found"
  }
}
```

```json
{
  "status": 500,
  "data": {
    "success": false,
    "error": "Failed to fetch dates"
  }
}
```

### URL Parameters

| Parameter | Type    | Description                                            |
| --------- | ------- | ------------------------------------------------------ |
| user_id   | integer | The ID of the user to retrieve dates for (must be > 0) |

### Response Codes

| Status | Message        |
| ------ | -------------- |
| 200    | Success        |
| 404    | User not found |
| 500    | Server error   |

<aside class="warning">
The user_id parameter must be a positive integer. Invalid or non-existent user IDs will return a 404 error.
</aside>

## [POST] - Create Date

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl -X POST "{{base_url}}/api/dates" \
  -H "Authorization: Bearer your-api-key" \
  -H "Content-Type: application/json" \
  -d '{"user_id": 3, "dt_start": "2025-01-15T16:35:00", "dt_end": "2025-01-15T19:30:00"}'

```

```php
// --- PHP ---

<?php
$data = json_encode([
    'user_id' => 3,
    'dt_start' => '2025-01-15T16:35:00',
    'dt_end' => '2025-01-15T19:30:00'
]);
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/dates",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_POST => true,
  CURLOPT_POSTFIELDS => $data,
  CURLOPT_HTTPHEADER => [
    "Authorization: Bearer your-api-key",
    "Content-Type: application/json"
  ],
]);

$response = curl_exec($curl);
curl_close($curl);
$data = json_decode($response, true);
?>
```

```python
# --- Python ---

import requests

url = "{{base_url}}/api/dates"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}
data = {
    "user_id": 3,
    "dt_start": "2025-01-15T16:35:00",
    "dt_end": "2025-01-15T19:30:00"
}

response = requests.post(url, headers=headers, json=data)
result = response.json()
```

```javascript
// --- Fetch ---

fetch("{{base_url}}/api/dates", {
  method: "POST",
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    user_id: 3,
    dt_start: "2025-01-15T16:35:00",
    dt_end: "2025-01-15T19:30:00",
  }),
})
  .then((response) => response.json())
  .then((data) => console.log(data));
```

```js
// --- Axios ---

const axios = require("axios");

const config = {
  method: "post",
  url: "{{base_url}}/api/dates",
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
  data: {
    user_id: 3,
    dt_start: "2025-01-15T16:35:00",
    dt_end: "2025-01-15T19:30:00",
  },
};

axios(config)
  .then((response) => console.log(response.data))
  .catch((error) => console.error(error));
```

<aside class="notice">
This endpoint creates a new date record in the vHub system.
</aside>

### HTTP Request

`POST {{base_url}}/api/dates`

```
Response Outputs
```

```json
{
  "status": 201,
  "data": {
    "success": true,
    "message": "Date created successfully",
    "data": {
      "id": 4,
      "user_id": 3,
      "dt_start": "2025-01-15T16:35:00",
      "dt_end": "2025-01-15T19:30:00"
    }
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Missing user_id field"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Missing dt_start field"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Missing dt_end field"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Invalid user_id format"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "User not found"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Invalid datetime format. Use YYYY-MM-DDTHH:MM:SS"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "End time must be after start time"
  }
}
```

```json
{
  "status": 500,
  "data": {
    "success": false,
    "error": "Failed to create date"
  }
}
```

### Request Body Parameters

| Parameter | Type    | Required | Description                                    |
| --------- | ------- | -------- | ---------------------------------------------- |
| user_id   | integer | Yes      | The ID of the user (must exist in users table) |
| dt_start  | string  | Yes      | Start datetime in YYYY-MM-DDTHH:MM:SS format   |
| dt_end    | string  | Yes      | End datetime in YYYY-MM-DDTHH:MM:SS format     |

### Response Codes

| Status | Message                                                                                       |
| ------ | --------------------------------------------------------------------------------------------- |
| 201    | Date created successfully                                                                     |
| 400    | Missing required fields / Invalid format / User not found / End time must be after start time |
| 500    | Failed to create date                                                                         |

<aside class="warning">
The user_id must exist in the users table. End time must be after start time. Use ISO datetime format with 'T' separator.
</aside>

## [PUT] - Update Date by Id

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl -X PUT "{{base_url}}/api/dates/id/1" \
  -H "Authorization: Bearer your-api-key" \
  -H "Content-Type: application/json" \
  -d '{"dt_start": "2025-01-15T18:00:00", "dt_end": "2025-01-15T20:15:00"}'
```

```php
// --- PHP ---

<?php
$id = 1;
$data = json_encode([
    'dt_start' => '2025-01-15T18:00:00',
    'dt_end' => '2025-01-15T20:15:00'
]);
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/dates/id/{$id}",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "PUT",
  CURLOPT_POSTFIELDS => $data,
  CURLOPT_HTTPHEADER => [
    "Authorization: Bearer your-api-key",
    "Content-Type: application/json"
  ],
]);

$response = curl_exec($curl);
curl_close($curl);
$data = json_decode($response, true);
?>
```

```python
# --- Python ---

import requests

id = 1
url = f"{{base_url}}/api/dates/id/{id}"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}
data = {
    "dt_start": "2025-01-15T18:00:00",
    "dt_end": "2025-01-15T20:15:00"
}

response = requests.put(url, headers=headers, json=data)
result = response.json()
```

```javascript
// --- Fetch ---

const id = 1;
fetch(`{{base_url}}/api/dates/id/${id}`, {
  method: "PUT",
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    dt_start: "2025-01-15T18:00:00",
    dt_end: "2025-01-15T20:15:00",
  }),
})
  .then((response) => response.json())
  .then((data) => console.log(data));
```

```js
// --- Axios ---

const axios = require("axios");

const id = 1;
const config = {
  method: "put",
  url: `{{base_url}}/api/dates/id/${id}`,
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
  data: {
    dt_start: "2025-01-15T18:00:00",
    dt_end: "2025-01-15T20:15:00",
  },
};

axios(config)
  .then((response) => console.log(response.data))
  .catch((error) => console.error(error));
```

<aside class="notice">
This endpoint updates a specific date record by its <strong>{ id }</strong>.
</aside>

### HTTP Request

`PUT {{base_url}}/api/dates/id/{id}`

```
Response Outputs
```

```json
{
  "status": 200,
  "data": {
    "success": true,
    "message": "Date updated successfully",
    "data": {
      "id": 1,
      "user_id": 3,
      "dt_start": "2025-01-15T18:00:00",
      "dt_end": "2025-01-15T20:15:00"
    }
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Missing dt_start field"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Missing dt_end field"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Invalid datetime format. Use YYYY-MM-DDTHH:MM:SS"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "End time must be after start time"
  }
}
```

```json
{
  "status": 404,
  "data": {
    "success": false,
    "error": "Date not found"
  }
}
```

```json
{
  "status": 500,
  "data": {
    "success": false,
    "error": "Failed to update date"
  }
}
```

### URL Parameters

| Parameter | Type    | Description                                |
| --------- | ------- | ------------------------------------------ |
| id        | integer | The ID of the date to update (must be > 0) |

### Request Body Parameters

| Parameter | Type   | Required | Description                                  |
| --------- | ------ | -------- | -------------------------------------------- |
| dt_start  | string | Yes      | Start datetime in YYYY-MM-DDTHH:MM:SS format |
| dt_end    | string | Yes      | End datetime in YYYY-MM-DDTHH:MM:SS format   |

### Response Codes

| Status | Message                                                                               |
| ------ | ------------------------------------------------------------------------------------- |
| 200    | Date updated successfully                                                             |
| 400    | Missing required fields / Invalid datetime format / End time must be after start time |
| 404    | Date not found                                                                        |
| 500    | Failed to update date                                                                 |

<aside class="warning">
Only dt_start and dt_end can be updated. End time must be after start time. The ID parameter must be a positive integer.
</aside>

## [DEL] - Date by Id

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl -X DELETE "{{base_url}}/api/dates/id/1" \
  -H "Authorization: Bearer your-api-key"
```

```php
// --- PHP ---

<?php
$id = 1;
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/dates/id/{$id}",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "DELETE",
  CURLOPT_HTTPHEADER => [
    "Authorization: Bearer your-api-key",
    "Content-Type: application/json"
  ],
]);

$response = curl_exec($curl);
curl_close($curl);
$data = json_decode($response, true);
?>
```

```python
# --- Python ---

import requests

id = 1
url = f"{{base_url}}/api/dates/id/{id}"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}

response = requests.delete(url, headers=headers)
data = response.json()
```

```javascript
// --- Fetch ---

const id = 1;
fetch(`{{base_url}}/api/dates/id/${id}`, {
  method: "DELETE",
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
})
  .then((response) => response.json())
  .then((data) => console.log(data));
```

```js
// --- Axios ---

const axios = require("axios");

const id = 1;
const config = {
  method: "delete",
  url: `{{base_url}}/api/dates/id/${id}`,
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
};

axios(config)
  .then((response) => console.log(response.data))
  .catch((error) => console.error(error));
```

<aside class="notice">
This endpoint deletes a specific date record by its <strong>{ id }</strong>.
</aside>

### HTTP Request

`DELETE {{base_url}}/api/dates/id/{id}`

```
Response Outputs
```

```json
{
  "status": 200,
  "data": {
    "success": true,
    "message": "Date deleted successfully",
    "data": {
      "id": 1,
      "user_id": 3,
      "dt_start": "2025-01-15T16:35:00",
      "dt_end": "2025-01-15T19:30:00"
    }
  }
}
```

```json
{
  "status": 404,
  "data": {
    "success": false,
    "error": "Date not found"
  }
}
```

```json
{
  "status": 500,
  "data": {
    "success": false,
    "error": "Failed to delete date"
  }
}
```

### URL Parameters

| Parameter | Type    | Description                                |
| --------- | ------- | ------------------------------------------ |
| id        | integer | The ID of the date to delete (must be > 0) |

### Response Codes

| Status | Message                   |
| ------ | ------------------------- |
| 200    | Date deleted successfully |
| 404    | Date not found            |
| 500    | Failed to delete date     |

<aside class="warning">
The ID parameter must be a positive integer. Once deleted, the date record cannot be recovered.
</aside>
