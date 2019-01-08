# Delete a database

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

