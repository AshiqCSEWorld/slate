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


# Authentication

## Register User

This endpoint stores user in database and User will recieve an email confiramtion to his email adderess. He need to to verify his email to activate account.

### HTTP Request

`POST http://example.com/api/users/register`

```javascript
user: {
  
    "_id": "5c1ae5ed2662482a7905ad73",
    "userName": "john",
    "firstName": "John",
    "lastName": "Doe",
    "email": "ashiquejava@gmail.com",
    "avatar": "//www.gravatar.com/avatar/8e50107ce9ade1f6a3d3e9f8e42d36bf?s=200&r=pg&d=mm",
    "password": "$2a$10$wMRYwGWnKRw/vQhUs2/3G.V8SOCjtXsYpweYNV.tcpn7i.nzSt236",
    "secretToken": "c3671ed5acb26871dca8",
    "resetTokenExpires": "2018-12-20T01:44:29.251Z",
    "isActive": false,
    "date": "2018-12-20T00:44:29.252Z",
    "__v": 0

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

`GET http://example.com/api/users/verifyUser/:secretToken`

```javascript
message: {
  'token is matched, user is verified now'
}
```
Method | Path | 
--------- | ------- | 
GET | api/users/verifyUser/:secretToken | 
<aside class="success">
Remember — If the token is matched, render the user into login page!
</aside>

## Login a User

### HTTP Request
`POST http://example.com/api/users/login`

```javascript
message: {
    "success": true,
    "token": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjVjMWFhN2VmZTVjNDEyNTk3MThhNDhjMSIsImF2YXRhciI6Ii8vd3d3LmdyYXZhdGFyLmNvbS9hdmF0YXIvMmQ1NDVhN2QyYzk4MDYwZDFiZmIzMThjZDFhMzMzMjM_cz0yMDAmcj1wZyZkPW1tIiwiaWF0IjoxNTQ1MjU0MDQwLCJleHAiOjE1NDUyNTc2NDB9.6oAzkpBo7E02bnl4PiIQLXNojJLdoHVMnaQCG2tTjZ0"
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
  'user with reset token is stored in db and an email has been sent including that reset token'
}
```
Method | Path | Body
--------- | ------- | -----------
POST | api/users/forget |  email

## Reset Password
This endpoint will check if the token (which comes from email url) is matched with the users token.

### HTTP Request
`GET http://example.com/api/users/reset/:token`

```javascript
message: {
  'token is matched, you should render confirm-password form now'
}
```

Method | Path | 
--------- | ------- | 
GET | api/users/reset/:token | 
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