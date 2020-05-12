# Test

To test the client, set the client host in the `/test/config.json` file:

{% code title="/test/config.json" %}
```javascript
{
    "HOST": "http://localhost:7070"
}
```
{% endcode %}

Then simply run the tests:

{% tabs %}
{% tab title="node" %}
```bash
$ npm test
```
{% endtab %}

{% tab title="yarn" %}
```bash
$ yarn test
```
{% endtab %}
{% endtabs %}

