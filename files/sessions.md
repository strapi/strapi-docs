# Sessions

Since HTTP driven applications are stateless, sessions provide a way to store information
about the user across requests.

Strapi provides "guest" sessions, meaning any visitor will have a session,
authenticated or not. If a session is new a `Set-Cookie` will be produced regardless
of populating the session.

Strapi only supports cookie sessions, for now.

The current session is available in `this.session` inside a controller action.

```js
let count = this.session.views || 0;
this.session.views = ++count;
this.body = count + ' views';
```

To destroy an active session, simply set it to `null`:

```js
this.session = null;
```
