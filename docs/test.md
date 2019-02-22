# Test

To test the client, set the host corresponding to your service instance in the `/test/config.json` file :

```javascript
{
    "HOST": "http://localhost:7070"
}
```

Then, simply run the tests:

{% tabs %}
{% tab title="node" %}
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

