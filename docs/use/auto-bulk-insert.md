# Auto Bulk Insert

This module provides a small utility to easily bulk insert from multiple calls:

{% tabs %}
{% tab title="ES6" %}
```javascript
const bulk = new Analytics.BulkInsert(analytics, {
    // Flush after N elements
    flushAt: 100,

    // Max duration to wait (in ms)
    flushAfter: 10000
});

bulk.push('MYDB', data);
...
bulk.push('MYDB', data);
```
{% endtab %}

{% tab title="ES5" %}
```javascript
var bulk = new Analytics.BulkInsert(analytics, {
    // Flush after N elements
    flushAt: 100,

    // Max duration to wait (in ms)
    flushAfter: 10000
});

bulk.push('MYDB', data);
...
bulk.push('MYDB', data);
```
{% endtab %}
{% endtabs %}

