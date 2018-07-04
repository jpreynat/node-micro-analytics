# Create a Client

To create a new client, you need to specify the µAnalytics host as a _string_.

{% tabs %}
{% tab title="ES6" %}
```javascript
import Analytics from 'micro-analytics';

const HOST = 'http://localhost:7070';
const analytics = new Analytics(HOST);
```
{% endtab %}

{% tab title="ES5" %}
```javascript
var Analytics = require('micro-analytics');

var HOST = 'http://localhost:7070';
var analytics = new Analytics(HOST);
```
{% endtab %}
{% endtabs %}

You can specify your credentials for µAnalytics basic authentication in an optional object passed as a second argument :

{% tabs %}
{% tab title="ES6" %}
```javascript
import Analytics from 'micro-analytics';

const HOST = 'http://localhost:7070';
const opts = {
  username: 'johan',
  password: 'myPass'
};

const analytics = new Analytics(HOST, opts);
```
{% endtab %}

{% tab title="ES5" %}
```javascript
var Analytics = require('micro-analytics');

var HOST = 'http://localhost:7070';
var opts = {
  username: 'johan',
  password: 'myPass'
};

var analytics = new Analytics(HOST, opts);
```
{% endtab %}
{% endtabs %}

By default, the client will use a cache key renewed each hour. You can set the cache interval using the `cacheExpire` key of the optional second argument. The value is the interval in seconds.

{% tabs %}
{% tab title="ES6" %}
```javascript
const Analytics = require('micro-analytics');

const HOST = 'http://localhost:7070';
const opts = {
  cacheExpire: 86400 // One day
};

const analytics = new Analytics(HOST, opts);
```
{% endtab %}

{% tab title="ES5" %}
```javascript
var Analytics = require('micro-analytics');

var HOST = 'http://localhost:7070';
var opts = {
  cacheExpire: 86400 // One day
};

var analytics = new Analytics(HOST, opts);
```
{% endtab %}
{% endtabs %}

