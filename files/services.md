# Services

Services can be thought of as libraries which contain functions that you might want to use
in many places of your application. For example, you might have an `Email` service which
wraps some default email message boilerplate code that you would want to use in many parts
of your application.

Simply create a JavaScript file containing a function or an object into your
`./api/<apiName>/services` directory.

```js
module.exports = {
  functionName: function (options) {
    // ...
  }
};
```
