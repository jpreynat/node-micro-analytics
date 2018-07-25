# Insert data in a database

## Simple insert

{% tabs %}
{% tab title="ES6" %}
```javascript
await analytics.push(DBNAME, {
    "time": new Date(), // optional
    "ip": "127.0.0.1",
    "event": "download",
    "path": "/somewhere",
    "headers": {
        "referer": "http://gitbook.com",
        "user-agent": "...",
        ...
    }
});
```
{% endtab %}

{% tab title="ES5" %}
```javascript
var data = {
    "time": new Date(), // optional
    "ip": "127.0.0.1",
    "event": "download",
    "path": "/somewhere",
    "headers": {
        "referer": "http://gitbook.com",
        "user-agent": "...",
        ...
    }
};

analytics.push(DBNAME, data)
.then(function() { ... });
```
{% endtab %}
{% endtabs %}

## Bulk insert

If you need to push a list of existing analytics, use this method:

```javascript
var data = {
    "list": [
        {
            "time": 1450098642,
            "ip": "127.0.0.1",
            "event": "download",
            "path": "/somewhere",
            "platform": "Apple Mac",
            "refererDomain": "www.gitbook.com",
            "countryCode": "fr"
        },
        {
            "time": 0,
            "ip": "127.0.0.1",
            "event": "login",
            "path": "/someplace",
            "platform": "Linux",
            "refererDomain": "www.gitbook.com",
            "countryCode": "us"
        }
    ]
};

analytics.bulk(DBNAME, data)
.then(function() { ... });
```

The passed `time` value must be a Unix timestamp in sec. The `countryCode` will be reprocessed by the service based on the `ip`.

## Multi-website bulk insert

If you need to push analytics for different websites, you can use:

```javascript
var data = {
    "list": [
        {
            "website": "website-1.com",
            "time": 1450098642,
            "ip": "127.0.0.1",
            "event": "download",
            "path": "/somewhere",
            "platform": "Apple Mac",
            "refererDomain": "www.gitbook.com",
            "countryCode": "fr"
        },
        {
            "website": "website-2.com",
            "time": 0,
            "ip": "127.0.0.1",
            "event": "login",
            "path": "/someplace",
            "platform": "Linux",
            "refererDomain": "www.gitbook.com",
            "countryCode": "us"
        }
    ]
};

analytics.bulkMulti(DBNAME, data)
.then(function() { ... });
```

