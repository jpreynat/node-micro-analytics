# Delete a database

Deleting a whole database is as simple as:

{% tabs %}
{% tab title="ES6" %}
```javascript
await analytics.delete(DBNAME);
```
{% endtab %}

{% tab title="ES5" %}
```javascript
analytics.delete(DBNAME)
.then(function() { ... });
```
{% endtab %}
{% endtabs %}

