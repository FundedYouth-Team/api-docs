---
weight: 17
title: Users
---

# Users

## [GET] - All Users

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl "{{base_url}}/api/users"
  -H "Authorization: Bearer your-api-key"
```

```php
# --- PHP ---

<?php
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/users",
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

url = "{{base_url}}/api/users"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}

response = requests.get(url, headers=headers)
data = response.json()
```

```javascript
// --- Fetch ---

fetch("{{base_url}}/api/users", {
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
  url: "{{base_url}}/api/users",
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
This endpoint retrieves all users in the vHub system.
</aside>

### HTTP Request

`GET {{base_url}}/api/users`

```
Response Outputs
```

```json
{
  "success": true,
  "data": [
    {
      "id": 1,
      "first_name": "John",
      "last_name": "Smith",
      "user_role": 3,
      "email": "john.smith@gmail.com",
      "phone": "5551234567",
      "dob": "1995-06-15",
      "profile": "/media/vhub/profile/john_smith.jpg"
    },
    {
      "id": 2,
      "first_name": "Jane",
      "last_name": "Doe",
      "user_role": 3,
      "email": "jane.doe@gmail.com",
      "phone": "5559876543",
      "dob": "1992-03-22",
      "profile": null
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
Remember — proper user management ensures system security and organization!
</aside>

## [GET] - User by Id

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl "{{base_url}}/api/users/id/1"
  -H "Authorization: Bearer your-api-key"
```

```php
# --- PHP ---

<?php
$id = 1;
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/users/id/{$id}",
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
url = f"{{base_url}}/api/users/id/{id}"
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
fetch(`{{base_url}}/api/users/id/${id}`, {
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
  url: `{{base_url}}/api/users/id/${id}`,
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
This endpoint retrieves a specific user by their <strong>{ id }</strong>.
</aside>

### HTTP Request

`GET {{base_url}}/api/users/id/{id}`

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
      "first_name": "John",
      "last_name": "Smith",
      "user_role": 3,
      "email": "john.smith@gmail.com",
      "phone": "5551234567",
      "dob": "1995-06-15",
      "profile": "/media/vhub/profile/john_smith.jpg"
    }
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
    "error": "Failed to fetch user"
  }
}
```

### URL Parameters

| Parameter | Type    | Description                                  |
| --------- | ------- | -------------------------------------------- |
| id        | integer | The ID of the user to retrieve (must be > 0) |

### Response Codes

| Status | Message        |
| ------ | -------------- |
| 200    | Success        |
| 404    | User not found |
| 500    | Server error   |

<aside class="warning">
The ID parameter must be a positive integer. Invalid or non-existent IDs will return a 404 error.
</aside>

## [GET] - Users by First Name

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl "{{base_url}}/api/users/firstname/john"
  -H "Authorization: Bearer your-api-key"
```

```php
# --- PHP ---

<?php
$firstName = 'john';
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/users/firstname/{$firstName}",
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

first_name = 'john'
url = f"{{base_url}}/api/users/firstname/{first_name}"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}

response = requests.get(url, headers=headers)
data = response.json()
```

```javascript
// --- Fetch ---

const firstName = "john";
fetch(`{{base_url}}/api/users/firstname/${firstName}`, {
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

const firstName = "john";
const config = {
  method: "get",
  url: `{{base_url}}/api/users/firstname/${firstName}`,
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
This endpoint retrieves all users with a specific <strong>{ first_name }</strong>.
</aside>

### HTTP Request

`GET {{base_url}}/api/users/firstname/{firstName}`

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
        "first_name": "John",
        "last_name": "Smith",
        "user_role": 3,
        "email": "john.smith@gmail.com",
        "phone": "5551234567",
        "dob": "1995-06-15",
        "profile": "/media/vhub/profile/john_smith.jpg"
      },
      {
        "id": 5,
        "first_name": "John",
        "last_name": "Doe",
        "user_role": 3,
        "email": "john.doe@gmail.com",
        "phone": "5558765432",
        "dob": "1990-11-08",
        "profile": null
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
    "error": "Failed to fetch user"
  }
}
```

### URL Parameters

| Parameter | Type   | Description                                     |
| --------- | ------ | ----------------------------------------------- |
| firstName | string | The first name to search for (case-insensitive) |

### Response Codes

| Status | Message        |
| ------ | -------------- |
| 200    | Success        |
| 404    | User not found |
| 500    | Server error   |

<aside class="warning">
The firstName parameter cannot be empty. Search is case-insensitive and may return multiple users.
</aside>

## [GET] - Users by Last Name

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl "{{base_url}}/api/users/lastname/smith"
  -H "Authorization: Bearer your-api-key"
```

```php
# --- PHP ---

<?php
$lastName = 'smith';
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/users/lastname/{$lastName}",
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

last_name = 'smith'
url = f"{{base_url}}/api/users/lastname/{last_name}"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}

response = requests.get(url, headers=headers)
data = response.json()
```

```javascript
// --- Fetch ---

const lastName = "smith";
fetch(`{{base_url}}/api/users/lastname/${lastName}`, {
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

const lastName = "smith";
const config = {
  method: "get",
  url: `{{base_url}}/api/users/lastname/${lastName}`,
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
This endpoint retrieves all users with a specific <strong>{ last_name }</strong>.
</aside>

### HTTP Request

`GET {{base_url}}/api/users/lastname/{lastName}`

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
        "first_name": "John",
        "last_name": "Smith",
        "user_role": 3,
        "email": "john.smith@gmail.com",
        "phone": "5551234567",
        "dob": "1995-06-15",
        "profile": "/media/vhub/profile/john_smith.jpg"
      },
      {
        "id": 3,
        "first_name": "Sarah",
        "last_name": "Smith",
        "user_role": 3,
        "email": "sarah.smith@gmail.com",
        "phone": "5554567890",
        "dob": "1988-12-03",
        "profile": "/media/vhub/profile/sarah_smith.png"
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
    "error": "Failed to fetch user"
  }
}
```

### URL Parameters

| Parameter | Type   | Description                                    |
| --------- | ------ | ---------------------------------------------- |
| lastName  | string | The last name to search for (case-insensitive) |

### Response Codes

| Status | Message        |
| ------ | -------------- |
| 200    | Success        |
| 404    | User not found |
| 500    | Server error   |

<aside class="warning">
The lastName parameter cannot be empty. Search is case-insensitive and may return multiple users.
</aside>

## [GET] - User by Email

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl "{{base_url}}/api/users/email/john.smith@gmail.com"
  -H "Authorization: Bearer your-api-key"
```

```php
# --- PHP ---

<?php
$email = 'john.smith@gmail.com';
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/users/email/{$email}",
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

email = 'john.smith@gmail.com'
url = f"{{base_url}}/api/users/email/{email}"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}

response = requests.get(url, headers=headers)
data = response.json()
```

```javascript
// --- Fetch ---

const email = "john.smith@gmail.com";
fetch(`{{base_url}}/api/users/email/${email}`, {
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

const email = "john.smith@gmail.com";
const config = {
  method: "get",
  url: `{{base_url}}/api/users/email/${email}`,
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
This endpoint retrieves a specific user by their <strong>{ email }</strong>.
</aside>

### HTTP Request

`GET {{base_url}}/api/users/email/{email}`

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
      "first_name": "John",
      "last_name": "Smith",
      "user_role": 3,
      "email": "john.smith@gmail.com",
      "phone": "5551234567",
      "dob": "1995-06-15",
      "profile": "/media/vhub/profile/john_smith.jpg"
    }
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
    "error": "Failed to fetch user"
  }
}
```

### URL Parameters

| Parameter | Type   | Description                               |
| --------- | ------ | ----------------------------------------- |
| email     | string | The email address of the user to retrieve |

### Response Codes

| Status | Message        |
| ------ | -------------- |
| 200    | Success        |
| 404    | User not found |
| 500    | Server error   |

<aside class="warning">
The email parameter must be a valid email format. Invalid or non-existent emails will return a 404 error.
</aside>

## [GET] - User by Phone

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl "{{base_url}}/api/users/phone/5551234567"
  -H "Authorization: Bearer your-api-key"
```

```php
# --- PHP ---

<?php
$phone = '5551234567';
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/users/phone/{$phone}",
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

phone = '5551234567'
url = f"{{base_url}}/api/users/phone/{phone}"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}

response = requests.get(url, headers=headers)
data = response.json()
```

```javascript
// --- Fetch ---

const phone = "5551234567";
fetch(`{{base_url}}/api/users/phone/${phone}`, {
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

const phone = "5551234567";
const config = {
  method: "get",
  url: `{{base_url}}/api/users/phone/${phone}`,
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
This endpoint retrieves a specific user by their <strong>{ phone }</strong> number.
</aside>

### HTTP Request

`GET {{base_url}}/api/users/phone/{phone}`

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
      "first_name": "John",
      "last_name": "Smith",
      "user_role": 3,
      "email": "john.smith@gmail.com",
      "phone": "5551234567",
      "dob": "1995-06-15",
      "profile": "/media/vhub/profile/john_smith.jpg"
    }
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
    "error": "Failed to fetch user"
  }
}
```

### URL Parameters

| Parameter | Type   | Description                                      |
| --------- | ------ | ------------------------------------------------ |
| phone     | string | The phone number of the user (must be 10 digits) |

### Response Codes

| Status | Message        |
| ------ | -------------- |
| 200    | Success        |
| 404    | User not found |
| 500    | Server error   |

<aside class="warning">
The phone parameter must be exactly 10 digits. Invalid or non-existent phone numbers will return a 404 error.
</aside>

## [POST] - Create User

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl -X POST "{{base_url}}/api/users" \
  -H "Authorization: Bearer your-api-key" \
  -H "Content-Type: application/json" \
  -d '{
    "first_name": "John",
    "last_name": "Smith",
    "user_role": 3,
    "email": "john.smith@gmail.com",
    "phone": "5551234567",
    "dob": "1995-06-15",
    "profile": "/media/vhub/profile/john_smith.jpg",
    "password": "SecurePassword123"
  }'

```

```php
// --- PHP ---

<?php
$data = json_encode([
    'first_name' => 'John',
    'last_name' => 'Smith',
    'user_role' => 3,
    'email' => 'john.smith@gmail.com',
    'phone' => '5551234567',
    'dob' => '1995-06-15',
    'profile' => '/media/vhub/profile/john_smith.jpg',
    'password' => 'SecurePassword123'
]);
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/users",
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

url = "{{base_url}}/api/users"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}
data = {
    "first_name": "John",
    "last_name": "Smith",
    "user_role": 3,
    "email": "john.smith@gmail.com",
    "phone": "5551234567",
    "dob": "1995-06-15",
    "profile": "/media/vhub/profile/john_smith.jpg",
    "password": "SecurePassword123"
}

response = requests.post(url, headers=headers, json=data)
result = response.json()
```

```javascript
// --- Fetch ---

fetch("{{base_url}}/api/users", {
  method: "POST",
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    first_name: "John",
    last_name: "Smith",
    user_role: 3,
    email: "john.smith@gmail.com",
    phone: "5551234567",
    dob: "1995-06-15",
    profile: "/media/vhub/profile/john_smith.jpg",
    password: "SecurePassword123",
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
  url: "{{base_url}}/api/users",
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
  data: {
    first_name: "John",
    last_name: "Smith",
    user_role: 3,
    email: "john.smith@gmail.com",
    phone: "5551234567",
    dob: "1995-06-15",
    profile: "/media/vhub/profile/john_smith.jpg",
    password: "SecurePassword123",
  },
};

axios(config)
  .then((response) => console.log(response.data))
  .catch((error) => console.error(error));
```

<aside class="notice">
This endpoint creates a new user in the vHub system.
</aside>

### HTTP Request

`POST {{base_url}}/api/users`

```
Response Outputs
```

```json
{
  "status": 201,
  "data": {
    "success": true,
    "message": "User created successfully",
    "data": {
      "id": 4,
      "first_name": "John",
      "last_name": "Smith",
      "user_role": 3,
      "email": "john.smith@gmail.com",
      "phone": "5551234567",
      "dob": "1995-06-15",
      "profile": "/media/vhub/profile/john_smith.jpg"
    }
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Missing first_name field"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "First name and last name cannot be empty"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Invalid user_role format"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Role not found"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Invalid email format"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Email already exists"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Phone must be exactly 10 digits"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Invalid date format. Use YYYY-MM-DD"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Profile must be a .jpg, .png, or .svg file"
  }
}
```

```json
{
  "status": 500,
  "data": {
    "success": false,
    "error": "Failed to create user"
  }
}
```

### Request Body Parameters

| Parameter  | Type    | Required | Description                                         |
| ---------- | ------- | -------- | --------------------------------------------------- |
| first_name | string  | Yes      | User's first name                                   |
| last_name  | string  | Yes      | User's last name                                    |
| user_role  | integer | Yes      | Role ID (must exist in roles table)                 |
| email      | string  | Yes      | Valid email address (must be unique)                |
| phone      | string  | Yes      | Phone number (exactly 10 digits)                    |
| dob        | string  | Yes      | Date of birth in YYYY-MM-DD format                  |
| password   | string  | Yes      | User password (will be securely hashed)             |
| profile    | string  | No       | Profile image path (.jpg, .png, or .svg files only) |

### Response Codes

| Status | Message                                                                                      |
| ------ | -------------------------------------------------------------------------------------------- |
| 201    | User created successfully                                                                    |
| 400    | Missing required fields / Invalid format / Email exists / Role not found / Invalid file type |
| 500    | Failed to create user                                                                        |

<aside class="warning">
Email addresses must be unique. Phone numbers must be exactly 10 digits. Profile images must be .jpg, .png, or .svg files. Passwords are securely hashed before storage.
</aside>

## [PUT] - Update User by Id

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl -X PUT "{{base_url}}/api/users/id/1" \
  -H "Authorization: Bearer your-api-key" \
  -H "Content-Type: application/json" \
  -d '{
    "first_name": "Johnny",
    "email": "johnny.smith@gmail.com",
    "phone": "5559876543"
  }'
```

```php
// --- PHP ---

<?php
$id = 1;
$data = json_encode([
    'first_name' => 'Johnny',
    'email' => 'johnny.smith@gmail.com',
    'phone' => '5559876543'
]);
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/users/id/{$id}",
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
url = f"{{base_url}}/api/users/id/{id}"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}
data = {
    "first_name": "Johnny",
    "email": "johnny.smith@gmail.com",
    "phone": "5559876543"
}

response = requests.put(url, headers=headers, json=data)
result = response.json()
```

```javascript
// --- Fetch ---

const id = 1;
fetch(`{{base_url}}/api/users/id/${id}`, {
  method: "PUT",
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    first_name: "Johnny",
    email: "johnny.smith@gmail.com",
    phone: "5559876543",
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
  url: `{{base_url}}/api/users/id/${id}`,
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
  data: {
    first_name: "Johnny",
    email: "johnny.smith@gmail.com",
    phone: "5559876543",
  },
};

axios(config)
  .then((response) => console.log(response.data))
  .catch((error) => console.error(error));
```

<aside class="notice">
This endpoint updates a specific user by their <strong>{ id }</strong>.
</aside>

### HTTP Request

`PUT {{base_url}}/api/users/id/{id}`

```
Response Outputs
```

```json
{
  "status": 200,
  "data": {
    "success": true,
    "message": "User updated successfully",
    "data": {
      "id": 1,
      "first_name": "Johnny",
      "last_name": "Smith",
      "user_role": 3,
      "email": "johnny.smith@gmail.com",
      "phone": "5559876543",
      "dob": "1995-06-15",
      "profile": "/media/vhub/profile/john_smith.jpg"
    }
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "First name cannot be empty"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Invalid email format"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Email already exists"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Phone must be exactly 10 digits"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "No valid fields to update"
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
    "error": "Failed to update user"
  }
}
```

### URL Parameters

| Parameter | Type    | Description                                |
| --------- | ------- | ------------------------------------------ |
| id        | integer | The ID of the user to update (must be > 0) |

### Request Body Parameters

| Parameter  | Type   | Required | Description                            |
| ---------- | ------ | -------- | -------------------------------------- |
| first_name | string | No       | User's first name                      |
| last_name  | string | No       | User's last name                       |
| email      | string | No       | Valid email address (must be unique)   |
| phone      | string | No       | Phone number (exactly 10 digits)       |
| password   | string | No       | New password (will be securely hashed) |

### Response Codes

| Status | Message                                                                                 |
| ------ | --------------------------------------------------------------------------------------- |
| 200    | User updated successfully                                                               |
| 400    | Invalid format / Email exists / Phone format / Empty fields / No valid fields to update |
| 404    | User not found                                                                          |
| 500    | Failed to update user                                                                   |

<aside class="warning">
Only the specified fields will be updated. Email addresses must remain unique. Phone numbers must be exactly 10 digits. Passwords are securely hashed before storage.
</aside>

## [PUT] - Update User by Email

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl -X PUT "{{base_url}}/api/users/email/john.smith@gmail.com" \
  -H "Authorization: Bearer your-api-key" \
  -H "Content-Type: application/json" \
  -d '{
    "first_name": "Johnny",
    "last_name": "Johnson",
    "phone": "5559876543"
  }'
```

```php
// --- PHP ---

<?php
$email = 'john.smith@gmail.com';
$data = json_encode([
    'first_name' => 'Johnny',
    'last_name' => 'Johnson',
    'phone' => '5559876543'
]);
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/users/email/{$email}",
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

email = 'john.smith@gmail.com'
url = f"{{base_url}}/api/users/email/{email}"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}
data = {
    "first_name": "Johnny",
    "last_name": "Johnson",
    "phone": "5559876543"
}

response = requests.put(url, headers=headers, json=data)
result = response.json()
```

```javascript
// --- Fetch ---

const email = "john.smith@gmail.com";
fetch(`{{base_url}}/api/users/email/${email}`, {
  method: "PUT",
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    first_name: "Johnny",
    last_name: "Johnson",
    phone: "5559876543",
  }),
})
  .then((response) => response.json())
  .then((data) => console.log(data));
```

```js
// --- Axios ---

const axios = require("axios");

const email = "john.smith@gmail.com";
const config = {
  method: "put",
  url: `{{base_url}}/api/users/email/${email}`,
  headers: {
    Authorization: "Bearer your-api-key",
    "Content-Type": "application/json",
  },
  data: {
    first_name: "Johnny",
    last_name: "Johnson",
    phone: "5559876543",
  },
};

axios(config)
  .then((response) => console.log(response.data))
  .catch((error) => console.error(error));
```

<aside class="notice">
This endpoint updates a specific user by their <strong>{ email }</strong>.
</aside>

### HTTP Request

`PUT {{base_url}}/api/users/email/{email}`

```
Response Outputs
```

```json
{
  "status": 200,
  "data": {
    "success": true,
    "message": "User updated successfully",
    "data": {
      "id": 1,
      "first_name": "Johnny",
      "last_name": "Johnson",
      "user_role": 3,
      "email": "john.smith@gmail.com",
      "phone": "5559876543",
      "dob": "1995-06-15",
      "profile": "/media/vhub/profile/john_smith.jpg"
    }
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Invalid email format"
  }
}
```

```json
{
  "status": 400,
  "data": {
    "success": false,
    "error": "Email already exists"
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
    "error": "Failed to update user"
  }
}
```

### URL Parameters

| Parameter | Type   | Description                                     |
| --------- | ------ | ----------------------------------------------- |
| email     | string | The email of the user to update (must be valid) |

### Request Body Parameters

| Parameter  | Type   | Required | Description                            |
| ---------- | ------ | -------- | -------------------------------------- |
| first_name | string | No       | User's first name                      |
| last_name  | string | No       | User's last name                       |
| email      | string | No       | New email address (must be unique)     |
| phone      | string | No       | Phone number (exactly 10 digits)       |
| password   | string | No       | New password (will be securely hashed) |

### Response Codes

| Status | Message                                                                                 |
| ------ | --------------------------------------------------------------------------------------- |
| 200    | User updated successfully                                                               |
| 400    | Invalid format / Email exists / Phone format / Empty fields / No valid fields to update |
| 404    | User not found                                                                          |
| 500    | Failed to update user                                                                   |

<aside class="warning">
Only the specified fields will be updated. Email addresses must remain unique and in valid format. Phone numbers must be exactly 10 digits.
</aside>

## [DEL] - User by Id

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl -X DELETE "{{base_url}}/api/users/id/1" \
  -H "Authorization: Bearer your-api-key"
```

```php
// --- PHP ---

<?php
$id = 1;
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/users/id/{$id}",
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
url = f"{{base_url}}/api/users/id/{id}"
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
fetch(`{{base_url}}/api/users/id/${id}`, {
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
  url: `{{base_url}}/api/users/id/${id}`,
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
This endpoint deletes a specific user by their <strong>{ id }</strong>.
</aside>

### HTTP Request

`DELETE {{base_url}}/api/users/id/{id}`

```
Response Outputs
```

```json
{
  "status": 200,
  "data": {
    "success": true,
    "message": "User deleted successfully",
    "data": {
      "id": 1,
      "first_name": "John",
      "last_name": "Smith",
      "user_role": 3,
      "email": "john.smith@gmail.com",
      "phone": "5551234567",
      "dob": "1995-06-15",
      "profile": "/media/vhub/profile/john_smith.jpg"
    }
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
    "error": "Failed to delete user"
  }
}
```

### URL Parameters

| Parameter | Type    | Description                                |
| --------- | ------- | ------------------------------------------ |
| id        | integer | The ID of the user to delete (must be > 0) |

### Response Codes

| Status | Message                   |
| ------ | ------------------------- |
| 200    | User deleted successfully |
| 404    | User not found            |
| 500    | Failed to delete user     |

<aside class="warning">
The ID parameter must be a positive integer. Once deleted, the user record cannot be recovered.
</aside>

## [DEL] - User by Email

> The logic below is designed to return a JSON response

```shell
# --- cURL ---

curl -X DELETE "{{base_url}}/api/users/email/john.smith@gmail.com" \
  -H "Authorization: Bearer your-api-key"
```

```php
// --- PHP ---

<?php
$email = 'john.smith@gmail.com';
$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "{{base_url}}/api/users/email/{$email}",
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

email = 'john.smith@gmail.com'
url = f"{{base_url}}/api/users/email/{email}"
headers = {
    "Authorization": "Bearer your-api-key",
    "Content-Type": "application/json"
}

response = requests.delete(url, headers=headers)
data = response.json()
```

```javascript
// --- Fetch ---

const email = "john.smith@gmail.com";
fetch(`{{base_url}}/api/users/email/${email}`, {
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

const email = "john.smith@gmail.com";
const config = {
  method: "delete",
  url: `{{base_url}}/api/users/email/${email}`,
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
This endpoint deletes a specific user by their <strong>{ email }</strong>.
</aside>

### HTTP Request

`DELETE {{base_url}}/api/users/email/{email}`

```
Response Outputs
```

```json
{
  "status": 200,
  "data": {
    "success": true,
    "message": "User deleted successfully",
    "data": {
      "id": 1,
      "first_name": "John",
      "last_name": "Smith",
      "user_role": 3,
      "email": "john.smith@gmail.com",
      "phone": "5551234567",
      "dob": "1995-06-15",
      "profile": "/media/vhub/profile/john_smith.jpg"
    }
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
    "error": "Failed to delete user"
  }
}
```

### URL Parameters

| Parameter | Type   | Description                                     |
| --------- | ------ | ----------------------------------------------- |
| email     | string | The email of the user to delete (must be valid) |

### Response Codes

| Status | Message                   |
| ------ | ------------------------- |
| 200    | User deleted successfully |
| 404    | User not found            |
| 500    | Failed to delete user     |

<aside class="warning">
The email parameter must be a valid email format. Once deleted, the user record cannot be recovered.
</aside>
