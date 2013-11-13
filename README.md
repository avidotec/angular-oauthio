# angular-oauth.io

https://oauth.io/ is a service that allows you to integrate in your app a lot of
OAuth providers, without much hassle and keeping the secret keys away from your
code.

However, it only handles the login until you get an access token, and then you
are on your own.

angular-oauth.io was born to go a step further, allowing the developer to attach
handlers that can exploit said token, by storing it, making api calls and
whatever they want.

## Getting Started

Download the [production version][min] or the [development version][max].

[min]: https://raw.github.com/matteosuppo/jquery-angular-oauth.io/master/dist/angular-angular-oauth.io.min.js
[max]: https://raw.github.com/matteosuppo/jquery-angular-oauth.io/master/dist/angular-angular-oauth.io.js

In your web page:

```html
<script src="angular.js"></script>
<script src="dist/angular-oauth.io.min.js"></script>
```

In your app.js file:

```javascript
var app = angular.module('yourApp', [
  ...
  'oauth.io',
  ...
]);
```

## Configuration

Oauth.io needs a public key to work, and you can set it like this:

```javascript
app.config(function (OAuthProvider) {
  OAuthProvider.setPublicKey('ABC');  // where instead of ABC you put your key
});
```

This is the bare minimum. Of course you may want to attach an handler for a
certain method:

```javascript
app.config(function(OAuthProvider) {
  OAuthProvider.setHandler('facebook', function (OAuthData, $http) {
    $http.get('https://graph.facebook.com/me?access_token=' + OAuthData.result.access_token)
      .then(function (resp) {
        console.log(resp);
      });
    });
});
```

Note that thanks to dependency injection you have access to other services inside
your handler, which allows you to do nearly everything.

## Documentation



## Examples
_(Coming soon)_

#License

    The MIT License
    Copyright (c) 2013 Matteo Suppo

    Permission is hereby granted, free of charge, to any person obtaining a
    copy of this software and associated documentation files (the "Software"),
    to deal in the Software without restriction, including without limitation
    the rights to use, copy, modify, merge, publish, distribute, sublicense,
    and/or sell copies of the Software, and to permit persons to whom the
    Software is furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in
    all copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL
    THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
    FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS
    IN THE SOFTWARE.
