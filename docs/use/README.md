---
description: Available APIs
---

# Use

## Get data from a database

All requests for data can be passed a parameters object to query over a time range :

```javascript
var params = {
    start: new Date(2015, 0, 1),
    end: new Date(2015, 2, 1)
};
```

### Get complete analytics

```javascript
// Full query
analytics.list(DBNAME)
.then(function(result) {
    // result.list is an array containing the whole DB
    ...
});

// Example with optional time range
// The same applies for all data requests
analytics.list(DBNAME, params)
.then(function(result) { ... });
```

A full description for `result` can be found [here](https://github.com/GitbookIO/micro-analytics#get-website).

### Get the count of analytics

```javascript
analytics.count(DBNAME)
.then(function(result) {
    // result looks like { total: 300, unique: 150 }
    ...
});
```

A full description for `result` can be found [here](https://github.com/GitbookIO/micro-analytics#get-websitecount).

### Get aggregated analytics by countries

```javascript
analytics.byCountries(DBNAME)
.then(function(countries) {
    // result.list is an array of aggregated analytics
    ...
});
```

A full description for `countries` can be found [here](https://github.com/GitbookIO/micro-analytics#get-websitecountries).

### Get aggregated analytics by platforms

```javascript
analytics.byPlatforms(DBNAME)
.then(function(platforms) { ... });
```

A full description for `platforms` can be found [here](https://github.com/GitbookIO/micro-analytics#get-websiteplatforms).

### Get aggregated analytics by domains

```javascript
analytics.byDomains(DBNAME)
.then(function(domains) { ... });
```

A full description for `domains` can be found [here](https://github.com/GitbookIO/micro-analytics#get-websitedomains).

### Get aggregated analytics by events

```javascript
analytics.byEvents(DBNAME)
.then(function(events) { ... });
```

A full description for `events` can be found [here](https://github.com/GitbookIO/micro-analytics#get-websiteevents).

### Get aggregated analytics as a time serie

With `overTime()`, the parameter object can take an `interval` key to specify the time serie interval in seconds. By default, the service sets the interval to `86400` \(which is equal to one day\).

```javascript
// Full query
analytics.overTime(DBNAME)
.then(function(timeSerie) { ... });

// With parameters
var params = {
    start: new Date(2015, 0, 1),
    end: new Date(2015, 2, 1),
    interval: 2592000 // one month
};

analytics.overTime(DBNAME, params)
.then(function(timeSerie) { ... });
```

A full description for `timeSerie` can be found [here](https://github.com/GitbookIO/micro-analytics#get-websitetime).

## Insert data in a database

### Simple insert

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

### Bulk insert

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

### Multi-website bulk insert

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
