---
weight: 15
title: Roles
---

# Roles

## [GET] - All Roles

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl "{{base_url}}/api/roles"
  -H "Authorization: Bearer your-api-key"
```

```php
# --- PHP ---

<?php
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/roles",
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

url = "{{base_url}}/api/roles"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}

response = requests.get(url, headers=headers)
data = response.json()
```

```javascript
// --- Fetch ---

fetch("{{base_url}}/api/roles", {
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
  url: "{{base_url}}/api/roles",
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
This endpoint retrieves all roles in the vHub system.
</aside>

### HTTP Request

`GET {{base_url}}/api/roles`

```
Response Outputs
```

```json
{
  "success": true,
  "data": [
    {
      "id": 1,
      "name": "admin"
    },
    {
      "id": 2,
      "name": "editor"
    },
    {
      "id": 3,
      "name": "volunteer"
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
Remember - proper role management ensures secure access control!
</aside>

## [GET] - Role by Id

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl "{{base_url}}/api/roles/id/1"
  -H "Authorization: Bearer your-api-key"
```

```php
# --- PHP ---

<?php
$id = 1;
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/roles/id/{$id}",
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

id = 1
url = f"{{base_url}}/api/roles/id/{id}"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}

response = requests.get(url, headers=headers)
data = response.json()
```

```javascript
// --- Fetch ---

const id = 1;
fetch(`{{base_url}}/api/roles/id/${id}`, {
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

const id = 1;
const config = {
  method: "get",
  url: `{{base_url}}/api/roles/id/${id}`,
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
This endpoint retrieves a specific role by its <strong>{ id }</strong>.
</aside>

### HTTP Request

`GET {{base_url}}/api/roles/id/{id}`

```
Response Outputs
```

```json
{
  "status": 200,
  "data": {
    "success": true,
    "data": {
      "id": 1,
      "name": "admin"
    }
  }
}
```

```json
{
  "status": 404,
  "data": {
    "success": false,
    "error": "Role not found"
  }
}
```

```json
{
  "status": 500,
  "data": {
    "success": false,
    "error": "Failed to fetch role"
  }
}
```

### URL Parameters

| Parameter | Type    | Description                                  |
| --------- | ------- | -------------------------------------------- |
| id        | integer | The ID of the role to retrieve (must be > 0) |

### Response Codes

| Status | Message        |
| ------ | -------------- |
| 200    | Success        |
| 404    | Role not found |
| 500    | Server error   |

<aside class="warning">
The ID parameter must be a positive integer. Invalid or non-existent IDs will return a 404 error.
</aside>

## [GET] - Role by Name

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl "{{base_url}}/api/roles/name/admin"
  -H "Authorization: Bearer your-api-key"
```

```php
# --- PHP ---

<?php
$name = 'admin';
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/roles/name/{$name}",
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

name = 'admin'
url = f"{{base_url}}/api/roles/name/{name}"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}

response = requests.get(url, headers=headers)
data = response.json()
```

```javascript
// --- Fetch ---

const name = "admin";
fetch(`{{base_url}}/api/roles/name/${name}`, {
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

const name = "admin";
const config = {
  method: "get",
  url: `{{base_url}}/api/roles/name/${name}`,
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
This endpoint retrieves a specific role by its <strong>{ name }</strong>.
</aside>

### HTTP Request

`GET {{base_url}}/api/roles/name/{name}`

```
Response Outputs
```

```json
{
  "status": 200,
  "data": {
    "success": true,
    "data": {
      "id": 1,
      "name": "admin"
    }
  }
}
```

```json
{
  "status": 404,
  "data": {
    "success": false,
    "error": "Role not found"
  }
}
```

```json
{
  "status": 500,
  "data": {
    "success": false,
    "error": "Failed to fetch role"
  }
}
```

### URL Parameters

| Parameter | Type   | Description                                         |
| --------- | ------ | --------------------------------------------------- |
| name      | string | The name of the role to retrieve (case-insensitive) |

### Response Codes

| Status | Message        |
| ------ | -------------- |
| 200    | Success        |
| 404    | Role not found |
| 500    | Server error   |

<aside class="warning">
The name parameter cannot be empty. Invalid or non-existent role names will return a 404 error.
</aside>

## [POST] - Create Role

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl -X POST "{{base_url}}/api/roles" \
  -H "Authorization: Bearer your-api-key" \
  -H "Content-Type: application/json" \
  -d '{"name": "moderator"}'

```

```php
// --- PHP ---

<?php
$data = json_encode(['name' => 'moderator']);
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/roles",
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

url = "{{base_url}}/api/roles"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}
data = {"name": "moderator"}

response = requests.post(url, headers=headers, json=data)
result = response.json()
```

```javascript
// --- Fetch ---

fetch("{{base_url}}/api/roles", {
  method: "POST",
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    name: "moderator",
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
  url: "{{base_url}}/api/roles",
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
  data: {
    name: "moderator",
  },
};

axios(config)
  .then((response) => console.log(response.data))
  .catch((error) => console.error(error));
```

<aside class="notice">
This endpoint creates a new role in the vHub system.
</aside>

### HTTP Request

`POST {{base_url}}/api/roles`

```
Response Outputs
```

```json
{
  "status": 201,
  "data": {
    "success": true,
    "message": "Role created successfully",
    "data": {
      "id": 4,
      "name": "moderator"
    }
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Missing name field"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Missing name field"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Name cannot be empty"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Failed to create role because special characters were used"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Role name already exists"
  }
}
```

```json
{
  "status": 500,
  "data": {
    "success": false,
    "error": "Failed to create role"
  }
}
```

### Request Body Parameters

| Parameter | Type   | Required | Description                                    |
| --------- | ------ | -------- | ---------------------------------------------- |
| name      | string | Yes      | The name of the role (letters only, lowercase) |

### Response Codes

| Status | Message                                                                                        |
| ------ | ---------------------------------------------------------------------------------------------- |
| 201    | Role created successfully                                                                      |
| 400    | Missing name field / Name cannot be empty / Special characters used / Role name already exists |
| 500    | Failed to create role                                                                          |

<aside class="warning">
Role names must contain only letters, will be converted to lowercase, and must be unique.
</aside>

## [DEL] - Role by Id

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl -X DELETE "{{base_url}}/api/roles/id/1" \
  -H "Authorization: Bearer your-api-key"
```

```php
// --- PHP ---

<?php
$id = 1;
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/roles/id/{$id}",
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
url = f"{{base_url}}/api/roles/id/{id}"
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
fetch(`{{base_url}}/api/roles/id/${id}`, {
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
  url: `{{base_url}}/api/roles/id/${id}`,
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
This endpoint deletes a specific role by its <strong>{ id }</strong>.
</aside>

### HTTP Request

`DELETE {{base_url}}/api/roles/id/{id}`

```
Response Outputs
```

```json
{
  "status": 200,
  "data": {
    "success": true,
    "message": "Role deleted successfully",
    "data": {
      "id": 1,
      "name": "admin"
    }
  }
}
```

```json
{
  "status": 404,
  "data": {
    "success": false,
    "error": "Role not found"
  }
}
```

```json
{
  "status": 403,
  "data": {
    "success": false,
    "error": "Role cannot be deleted"
  }
}
```

```json
{
  "status": 500,
  "data": {
    "success": false,
    "error": "Failed to delete role"
  }
}
```

### URL Parameters

| Parameter | Type    | Description                                |
| --------- | ------- | ------------------------------------------ |
| id        | integer | The ID of the role to delete (must be > 0) |

### Response Codes

| Status | Message                   |
| ------ | ------------------------- |
| 200    | Role deleted successfully |
| 403    | Role cannot be deleted    |
| 404    | Role not found            |
| 500    | Failed to delete role     |

<aside class="warning">
Some roles may be protected from deletion. The ID parameter must be a positive integer.
</aside>

## [DEL] - Role by Name

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl -X DELETE "{{base_url}}/api/roles/name/admin" \
  -H "Authorization: Bearer your-api-key"
```

```php
// --- PHP ---

<?php
$name = 'admin';
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/roles/name/{$name}",
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

name = 'admin'
url = f"{{base_url}}/api/roles/name/{name}"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}

response = requests.delete(url, headers=headers)
data = response.json()
```

```javascript
// --- Fetch ---

const name = "admin";
fetch(`{{base_url}}/api/roles/name/${name}`, {
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

const name = "admin";
const config = {
  method: "delete",
  url: `{{base_url}}/api/roles/name/${name}`,
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
This endpoint deletes a specific role by its <strong>{ name }</strong>.
</aside>

### HTTP Request

`DELETE {{base_url}}/api/roles/name/{name}`

```
Response Outputs
```

```json
{
  "status": 200,
  "data": {
    "success": true,
    "message": "Role deleted successfully",
    "data": {
      "id": 1,
      "name": "admin"
    }
  }
}
```

```json
{
  "status": 404,
  "data": {
    "success": false,
    "error": "Role not found"
  }
}
```

```json
{
  "status": 403,
  "data": {
    "success": false,
    "error": "Role cannot be deleted"
  }
}
```

```json
{
  "status": 500,
  "data": {
    "success": false,
    "error": "Failed to delete role"
  }
}
```

### URL Parameters

| Parameter | Type   | Description                                       |
| --------- | ------ | ------------------------------------------------- |
| name      | string | The name of the role to delete (case-insensitive) |

### Response Codes

| Status | Message                   |
| ------ | ------------------------- |
| 200    | Role deleted successfully |
| 403    | Role cannot be deleted    |
| 404    | Role not found            |
| 500    | Failed to delete role     |

<aside class="warning">
Some roles may be protected from deletion. The name parameter cannot be empty.
</aside>

## [PUT] - Update Role by Id

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl -X PUT "{{base_url}}/api/roles/id/1" \
  -H "Authorization: Bearer your-api-key" \
  -H "Content-Type: application/json" \
  -d '{"name": "moderator"}'
```

```php
// --- PHP ---

<?php
$id = 1;
$data = json_encode(['name' => 'moderator']);
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/roles/id/{$id}",
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
url = f"{{base_url}}/api/roles/id/{id}"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}
data = {"name": "moderator"}

response = requests.put(url, headers=headers, json=data)
result = response.json()
```

```javascript
// --- Fetch ---

const id = 1;
fetch(`{{base_url}}/api/roles/id/${id}`, {
  method: "PUT",
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    name: "moderator",
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
  url: `{{base_url}}/api/roles/id/${id}`,
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
  data: {
    name: "moderator",
  },
};

axios(config)
  .then((response) => console.log(response.data))
  .catch((error) => console.error(error));
```

<aside class="notice">
This endpoint updates a specific role by its <strong>{ id }</strong>.
</aside>

### HTTP Request

`PUT {{base_url}}/api/roles/id/{id}`

```
Response Outputs
```

```json
{
  "status": 200,
  "data": {
    "success": true,
    "message": "Role updated successfully",
    "data": {
      "id": 1,
      "name": "moderator"
    }
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Missing name field"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Name cannot be empty"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Failed to update role because special characters were used"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Role name already exists"
  }
}
```

```json
{
  "status": 404,
  "data": {
    "success": false,
    "error": "Role not found"
  }
}
```

```json
{
  "status": 500,
  "data": {
    "success": false,
    "error": "Failed to update role"
  }
}
```

### URL Parameters

| Parameter | Type    | Description                                |
| --------- | ------- | ------------------------------------------ |
| id        | integer | The ID of the role to update (must be > 0) |

### Request Body Parameters

| Parameter | Type   | Required | Description                                        |
| --------- | ------ | -------- | -------------------------------------------------- |
| name      | string | Yes      | The new name of the role (letters only, lowercase) |

### Response Codes

| Status | Message                                                                                        |
| ------ | ---------------------------------------------------------------------------------------------- |
| 200    | Role updated successfully                                                                      |
| 400    | Missing name field / Name cannot be empty / Special characters used / Role name already exists |
| 404    | Role not found                                                                                 |
| 500    | Failed to update role                                                                          |

<aside class="warning">
Role names must contain only letters, will be converted to lowercase, and must be unique. The ID parameter must be a positive integer.
</aside>

## [PUT] - Update Role by Name

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl -X PUT "{{base_url}}/api/roles/name/admin" \
  -H "Authorization: Bearer your-api-key" \
  -H "Content-Type: application/json" \
  -d '{"id": 5, "name": "moderator"}'
```

```php
// --- PHP ---

<?php
$currentName = 'admin';
$data = json_encode(['id' => 5, 'name' => 'moderator']);
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/roles/name/{$currentName}",
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

current_name = 'admin'
url = f"{{base_url}}/api/roles/name/{current_name}"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}
data = {"id": 5, "name": "moderator"}

response = requests.put(url, headers=headers, json=data)
result = response.json()
```

```javascript
// --- Fetch ---

const currentName = "admin";
fetch(`{{base_url}}/api/roles/name/${currentName}`, {
  method: "PUT",
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    id: 5,
    name: "moderator",
  }),
})
  .then((response) => response.json())
  .then((data) => console.log(data));
```

```js
// --- Axios ---

const axios = require("axios");

const currentName = "admin";
const config = {
  method: "put",
  url: `{{base_url}}/api/roles/name/${currentName}`,
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
  data: {
    id: 5,
    name: "moderator",
  },
};

axios(config)
  .then((response) => console.log(response.data))
  .catch((error) => console.error(error));
```

<aside class="notice">
This endpoint updates a specific role by its current <strong>{ name }</strong>.
</aside>

### HTTP Request

`PUT {{base_url}}/api/roles/name/{currentName}`

```
Response Outputs
```

```json
{
  "status": 200,
  "data": {
    "id": {
      "msg": "ID updated successfully",
      "status": 200,
      "data": 5
    },
    "name": {
      "msg": "Name updated successfully",
      "status": 200,
      "data": "moderator"
    }
  }
}
```

```json
{
  "status": 200,
  "data": {
    "id": {
      "msg": "Invalid ID format",
      "status": 400,
      "data": 1
    },
    "name": {
      "msg": "Name updated successfully",
      "status": 200,
      "data": "moderator"
    }
  }
}
```

```json
{
  "status": 200,
  "data": {
    "id": {
      "msg": "ID not changed due to existing ID",
      "status": 409,
      "data": 1
    },
    "name": {
      "msg": "Name not changed due to existing name",
      "status": 409,
      "data": "admin"
    }
  }
}
```

```json
{
  "status": 200,
  "data": {
    "name": {
      "msg": "Missing name field",
      "status": 400,
      "data": "admin"
    }
  }
}
```

```json
{
  "status": 200,
  "data": {
    "name": {
      "msg": "Name cannot be empty",
      "status": 400,
      "data": "admin"
    }
  }
}
```

```json
{
  "status": 200,
  "data": {
    "name": {
      "msg": "Failed to update name because special characters were used",
      "status": 400,
      "data": "admin"
    }
  }
}
```

```json
{
  "status": 404,
  "data": {
    "success": false,
    "error": "Role not found"
  }
}
```

```json
{
  "status": 500,
  "data": {
    "success": false,
    "error": "Failed to update role"
  }
}
```

### URL Parameters

| Parameter   | Type   | Description                                               |
| ----------- | ------ | --------------------------------------------------------- |
| currentName | string | The current name of the role to update (case-insensitive) |

### Request Body Parameters

| Parameter | Type    | Required | Description                                        |
| --------- | ------- | -------- | -------------------------------------------------- |
| id        | integer | No       | The new ID for the role (must be positive)         |
| name      | string  | Yes      | The new name of the role (letters only, lowercase) |

### Response Codes

| Status | Message                                                          |
| ------ | ---------------------------------------------------------------- |
| 200    | Partial or full update completed (check individual field status) |
| 404    | Role not found                                                   |
| 500    | Failed to update role                                            |

### Field-Specific Status Codes

| Field Status | Message                                                                              |
| ------------ | ------------------------------------------------------------------------------------ |
| 200          | Field updated successfully                                                           |
| 400          | Invalid format / Name cannot be empty / Special characters used / Missing name field |
| 409          | Field not changed due to existing value                                              |

<aside class="warning">
This endpoint returns individual status codes for each field update. Role names must contain only letters and will be converted to lowercase. The current name parameter cannot be empty.
</aside>
