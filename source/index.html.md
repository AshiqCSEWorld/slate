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

# Authentication related errors

## Errors might occur while registering
### if userName is empty
```javascript
{
    "userName": "userName is required"
}
```
### if userName is less than 2 or greater than 30 character
```javascript
{
    "userName": "userName must be between 2 and 30 characters"
}
```
### if firstName is empty
```javascript
{
    "firstName": "firstName is required"
}
```
### if firstName is less than 2 or greater than 30 character
```javascript
{
    "firstName": "firstName must be between 2 and 30 characters"
}
```
### if lastName is empty
```javascript
{
    "lastName": "lastName is required"
}
```
### if lastName is less than 2 or greater than 30 character
```javascript
{
    "lastName": "lastName must be between 2 and 30 characters"
}
```

### if password is empty
```javascript
{
    "password": "password is required"
}
```

### if password is less than 6 characters
```javascript
{
    "password": "password must be at least 6 characters"
}
```

## Errors might occur while logging

### if userName is empty
```javascript
{
    "userName": "userName is required"
}
```
### if userName is less than 2 or greater than 30 character
```javascript
{
    "userName": "userName must be between 2 and 30 characters"
}
```
### if password is empty
```javascript
{
    "password": "password is required"
}
```
### if password is less than 6 characters
```javascript
{
    "password": "password must be at least 6 characters"
}
```

## Errors might occur while reset password
### if email is empty
```javascript
{
    "email": "email is required"
}
```
### if email is invalid
```javascript
{
    "email": "email is invalid"
}
```
### if password is empty
```javascript
{
    "password": "password is required"
}
```
### if password is less than 6 characters
```javascript
{
    "password": "password must be at least 6 characters"
}
```

# POST-ROUTES

## POST-IT
we store data which comes from frontend, we save it, and give some response back.

### HTTP Request
`POST http://example.com/api/post-it`



```javascript
// Payload
{
    "desc": "hello asiq21",
    "filter": "filter-aden",
    "location": "Unnamed Road, Bangladesh",
    "group": "undefined",
    "type": "5c1e3a633d2b1f24b83822a6",
    
    "tags": [
      {
        "user": "5c1de3f2f047172d89afbb8f"
      }
    ]
}

// response
 {
  "firstname": "bayjid",
  "lastname": "hossain",
  "mesg": "Posted",
  "post_id": "5c2099ddbadffc56f7b9b81a",
  "success": true
}
```

```javascript
// If no post is found
{
  "noPost": "There is no post for this user"
}
```

Method | Path | Body
--------- | ------- | -----------
POST | api/post-it | desc, image, filter, location, type, group, tags

## Get following
NOTE: for now just return this data(hardcode)

### HTTP Request
`POST http://example.com/api/get-followings`

```javascript
 {
  [
  { "follow_to": 24, "follow_to_username": "takkar" },
  { "follow_to": 11, "follow_to_username": "nobita" },
  { "follow_to": 32, "follow_to_username": "iamrakib" },
  { "follow_to": 30, "follow_to_username": "doraemon" },
  { "follow_to": 28, "follow_to_username": "selena" },
  { "follow_to": 16, "follow_to_username": "zayn" }
]
}
```

Method | Path |
--------- | ------- | 
GET | api/get-followings |


## Edit Post

### HTTP Request
`POST http://example.com/api/edit-post`

```javascript
// payload
{ 
 "description":"hello world",
 "post_id": "5c2080d0be950643daada9a9"
}

// response
{"success":true,"mssg":"Post updated!!"}
```
Method | Path | Body
--------- | ------- | -----------
POST | api/edit-post | description, post_id

## Untag
### HTTP Request
`POST http://example.com/api/untag`

```javascript
// payload
{ 
	"post": "5c2081e27a8184452fbb1e51",
	"user": "5c1de3f2f047172d89afbb8f"
}

// response
{"success": true}
```
Method | Path | Body
--------- | ------- | -----------
POST | api/edit-post | post, user

## Delete Post

### HTTP Request
`POST http://example.com/api/delete-post`

```javascript
// payload
{ 
	"postId": "5c2081e27a8184457jihu8tg",
}
// response
{"success":true,"mssg":"Post deleted!!"}
```
```javascript
// If no post is found to be deleted
{
  "noPost": "Post Not found'"
}
```
Method | Path | Body
--------- | ------- | -----------
POST | api/delete-post | postId

## Like-Post

### HTTP Request
`POST http://example.com/api/likes/5c2593441f8d4c64a82a613a`

```javascript
// payload
{ 
	"postId": "5c2593441f8d4c64a82a613a",
}
// response
// If the post is already liked by the user 
{"alreadyLiked": 'User already liked this post'}

// otherwise
{
    "post_id": "5c25a4f8251d9c774589f982",
    "liked_by": [
        {
            "_id": "5c25a53a251d9c774589f985",
            "user": "5c231c5d8582ed1329809873",
            "like_time": "2018-12-28T04:23:22.551Z"
        },
        {
            "like_time": "2018-12-28T04:22:33.955Z",
            "_id": "5c25a509251d9c774589f984",
            "user": "5c258df9e037516132c2285a"
        }
    ]
}

// If no post is found by given id
{"postNotFound": 'no post found'}
```
Method | Path | Body/Params
--------- | ------- | -----------
POST | api/likes/:postId | postId