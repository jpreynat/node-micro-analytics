---
description: Test the client locally
---

# Test

To test the client, launch a local install of µAnalytics and set the host URL corresponding to your service instance in the `/test/config.json` file:

```javascript
{
    "HOST": "http://localhost:7070"
}
```

Then, simply run the tests:

{% tabs %}
{% tab title="npm" %}
```bash
$ npm test
```
{% endtab %}

{% tab title="yarn" %}
```bash
$ yarn run test
```
{% endtab %}
{% endtabs %}

