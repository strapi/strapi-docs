# Users

Most of the web applications require a user management system: registration, login,
reset password, etc.

To avoid you to reinvent the wheel, Strapi embedded a full featured user management
system powered by [Passport](http://passportjs.org/) and JSON Web Token (JWT).

## Local Registration

Route used to register a user to your application: `POST /auth/local/register`.

Request payload:

```js
{
  "username": "John DOE"
  "email": "contact@company.com",
  "password": "123456"
}
```

Response payload:

```js
{
  "user": {},
  "jwt": ""
}
```

## Local Login

Route used to login a user to your application: `POST /auth/local`.

Request payload:

```js
{
  "identifier": "contact@company.com",
  "password": "123456"
}
```

Response payload:

```js
{
  "user": {},
  "jwt": ""
}
```

## Providers

Thanks to [Passport](http://passportjs.org/), you can easily use OAuth and OAuth2
providers to enable authentication in your application. By default,
Strapi comes with five providers:
- Facebook
- Twitter
- Google
- GitHub
- LinkedIn

To use the providers authentication, set your credentials in
`./config/environments/development/passport.json`.

Redirect your user to: `GET /auth/:provider`.

After his approval, he will be redirected to `/auth/:provider/callback`.

Response payload:

```js
{
  "user": {},
  "jwt": ""
}
```

## Forgot password

Send an email to the user with an activation code: `GET /auth/forgot-password`.

Request payload:

```js
{
  "email": "contact@company.com"
}
```

## Change password

Route used to update the password of a user after he asked for a
"forgot-password" email: `GET /auth/change-password`.

Request payload:

```js
{
  "code": "",
  "password": "123456",
  "passwordConfirmation": "123456"
}
```

Response payload:

```js
{
  "user": {},
  "jwt": ""
}
```
