# Router

The most basic feature of any web application is the ability to interpret a request sent to a URL,
then send back a response. In order to do this, your application has to be able to distinguish one URL
from another.

Like most web frameworks, Strapi provides a router: a mechanism for mapping URLs to controllers.
Routes are rules that tell Strapi what to do when faced with an incoming request.

Routes can be found in `./config/routes.json`.

## Route format

Each route consists of an address (as a key) and a target (as an object value).
The address is a URL path and a specific HTTP method. The target is defined by an object with a
`controller` and an `action`. When the router receives an incoming request, it checks the address
of all routes for matches. If a matching route is found, the request is then passed to its target.

```js
  {
    "routes": {
      "VERB /endpoint/:param": {
        "controller": "controllerName",
        "action": "actionName"
      }
    }
  }
```

## Route parameters

Route paths will be translated to regular expressions used to match requests.
Query strings will not be considered when matching requests.

Route parameters are captured and added to `ctx.params`.

## Router prefix

Keep in mind routes can automatically be prefixed in `./config/global.json` with the `prefix` key.
Let an empty string if you don't want to prefix your API. The prefix must starts with a `/`, e.g. `/api`.

## Policies and route process

Just because a request matches a route address doesn't necessarily mean it will be passed to that
route's target directly. The request will need to pass through any configured policies first.
Policies are versatile tools for authorization and access control. They let you allow or deny
access to your controllers down to a fine level of granularity.

Policies are defined in the `./api/policies` directory of your application.
Each policy file should contain a single function. When it comes down to it, policies are
really just functions which run before your controllers. You can chain as many of them
together as you like. In fact they're designed to be used this way. Ideally, each middleware
function should really check just one thing.

For example to access `GET /admin`, the request will go through the `isAdmin` policy first.
If the policy allows the request, then the `show` action from the `Admin` controller is executed.

```js
  {
    "routes": {
      "GET /admin": {
        "controller": "Admin",
        "action": "show",
        "policies": ["isAdmin"]
      }
    }
  }
```

Do not forget to yield `next` when you need to move on.
