This is Paul's version of braintree-web, which includes the Javascript
source.  To update to the next version I pull in the tags from the
original repository and run a command like:

```
VERSION=2.6.2; git merge $VERSION && wget https://js.braintreegateway.com/js/braintree-$VERSION.js -O braintree.js && git commit --amend -am "added $VERSION javascript source"
```

braintree-web
=================

A suite of tools for integrating Braintree in the browser.

This is the repo to submit issues if you have any problems or questions about any v.zero JS integration.

Install
=======

```
npm install braintree-web
```

```
bower install braintree-web
```

Usage
=====

For more thorough documentation, visit [the JS SDK docs](https://developers.braintreepayments.com/javascript/sdk/client).

#### Drop-in integration

```html
<div id="payment-form"></div>
```

```javascript
braintree.setup('your-client-token', 'dropin', {
  container: 'payment-form'
});
```

#### Custom integration

```html
<form id="payment-form" action="/your/server/endpoint" method="post">
  <input data-braintree-name="number" value="4111111111111111" />
  <input data-braintree-name="expiration_date" value="10/20" />
  <input type="submit" value="Purchase" />
</form>
```

```javascript
braintree.setup('your-client-token', 'custom', {
  id: 'payment-form'
});
```

#### Advanced integration

```javascript
var client = new braintree.api.Client({
  clientToken: 'your-client-token'
});

client.tokenizeCard({
  number: '4111111111111111',
  expirationDate: '10/20'
}, function (err, nonce) {
  // Send nonce to your server
});
```

