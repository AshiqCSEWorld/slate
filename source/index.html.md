---
title: Instagram-Clone-API

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Instagram-clone API! You can use our API to access Instagram-clone API endpoints.

We have language bindings in JavaScript! You can view code examples in the dark area to the right.

This example API documentation page was created with [Slate](https://github.com/lord/slate). Feel free to edit it and use it as a base for your own API's documentation.

<!-- # Authentication -->

<!-- > To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside> -->


<!-- ```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript -->
<!-- const kittn = require('kittn'); -->

<!-- let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
``` -->

<!-- > The above command returns JSON structured like this:

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
``` -->

# Installation manual
1. run 'npm install' from terminal
2. run 'npm start' from terminal

# Authentication

## Register User

This endpoint stores user in database and User will recieve an email confiramtion to his email adderess. He need to to verify his email to activate account.

### HTTP Request

`POST http://example.com/api/users/register`

```javascript
user: {
    "userName": "ashik",
    "firstName": "Ashiqur",
    "lastName": "Rahman",
    "email": "ashikduit@gmail.com",
    "avatar": "//www.gravatar.com/avatar/2d545a7d2c98060d1bfb318cd1a33323?s=200&r=pg&d=mm"
}
```

Method | Path | Body
--------- | ------- | -----------
POST | api/users/register | userName, firstName, lastName, email, password



<aside class="success">
Remember — User has to visit the url (which was emailed to him), to verify his account!
</aside>

## Verify a User

This endpoint will check if the token (which comes from email url) is matched with the users token.

### HTTP Request

`POST http://example.com/api/users/verifyUser/:secretToken`

```javascript
message: {
    "success": true
}
```
Method | Path | 
--------- | ------- | 
POST | api/users/verifyUser/:secretToken | 
<aside class="success">
Remember — If the token is matched, render the user into login page!
</aside>

## Login a User

### HTTP Request
`POST http://example.com/api/users/login`

```javascript
message: {
    "success": true,
    "token": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjVjMWJhNDhiN2Q4NjliMjk1MTE1MmQ0YSIsImF2YXRhciI6Ii8vd3d3LmdyYXZhdGFyLmNvbS9hdmF0YXIvMmQ1NDVhN2QyYzk4MDYwZDFiZmIzMThjZDFhMzMzMjM_cz0yMDAmcj1wZyZkPW1tIiwiaWF0IjoxNTQ1MzE1OTU0LCJleHAiOjE1NDUzMTk1NTR9.czRENM6nVL8BkBwyGoLKmprh2K-V5_Q0qe-ExFufH8o",
    "userName": "ashik",
    "firstName": "Ashiqur",
    "lastName": "Rahman",
    "email": "ashikduit@gmail.com",
    "avatar": "//www.gravatar.com/avatar/2d545a7d2c98060d1bfb318cd1a33323?s=200&r=pg&d=mm"
}
```
Method | Path | Body
--------- | ------- | -----------
POST | api/users/login |  email, password

## Forget Password
User will recieve an email confiramtion to his email adderess. He has to visit the link from his mail (which included token) to reset his password.

### HTTP Request
`POST http://example.com/api/users/forget`

```javascript
message: {
    "success": true
}
```
Method | Path | Body
--------- | ------- | -----------
POST | api/users/forget |  email

## Reset Password
This endpoint will check if the token (which comes from email url) is matched with the users token.

### HTTP Request
`POST http://example.com/api/users/resetpass/:token`

```javascript
message: {
    "success": true
}
```

Method | Path | 
--------- | ------- | 
POST | api/users/resetpass/:token | 
<aside class="success">
Remember — If the token is matched, render the user into reset-password page!
</aside>

## Update user with new password
This endpoint will update the user with newly created password

### HTTP Request
`POST http://example.com/api/users/reset/:token`

```javascript
message: {
  "users password has been reset. redirect him/her to login page..."
}
```
Method | Path | Body
--------- | ------- | -----------
POST | api/users/reset/:token |  password, password2
<aside class="success">
Remember — If two input field has been matched, render the user into login page!
</aside>

# POST-ROUTES

## POST-IT
we store data which comes from frontend, we save it, and give some response back.

### HTTP Request
`POST http://example.com/api/post-it`
```javascript
 {
  "firstname": "bayjid",
  "lastname": "hossain",
  "mesg": "Posted",
  "post_id": "5c2099ddbadffc56f7b9b81a",
  "success": true
}
```

Method | Path | Body
--------- | ------- | -----------
POST | api/post-it | desc, image, filter, location, type, group, tags