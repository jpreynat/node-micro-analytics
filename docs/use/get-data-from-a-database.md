# Get data from a database

All requests for data can be passed a parameters object to query over a time range:

{% tabs %}
{% tab title="ES6" %}
```javascript
const params = [
    start: new Date(2015, 0, 1),
    end: new Date(2015, 2, 1)
};
```
{% endtab %}

{% tab title="ES5" %}
```javascript
var params = {
    start: new Date(2015, 0, 1),
    end: new Date(2015, 2, 1)
};
```
{% endtab %}
{% endtabs %}

## Get complete analytics

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

## Get the count of analytics

```javascript
analytics.count(DBNAME)
.then(function(result) {
    // result looks like { total: 300, unique: 150 }
    ...
});
```

A full description for `result` can be found [here](https://github.com/GitbookIO/micro-analytics#get-websitecount).

## Get aggregated analytics by countries

```javascript
analytics.byCountries(DBNAME)
.then(function(countries) {
    // result.list is an array of aggregated analytics
    ...
});
```

A full description for `countries` can be found [here](https://github.com/GitbookIO/micro-analytics#get-websitecountries).

## Get aggregated analytics by platforms

```javascript
analytics.byPlatforms(DBNAME)
.then(function(platforms) { ... });
```

A full description for `platforms` can be found [here](https://github.com/GitbookIO/micro-analytics#get-websiteplatforms).

## Get aggregated analytics by domains

```javascript
analytics.byDomains(DBNAME)
.then(function(domains) { ... });
```

A full description for `domains` can be found [here](https://github.com/GitbookIO/micro-analytics#get-websitedomains).

## Get aggregated analytics by events

```javascript
analytics.byEvents(DBNAME)
.then(function(events) { ... });
```

A full description for `events` can be found [here](https://github.com/GitbookIO/micro-analytics#get-websiteevents).

## Get aggregated analytics as a time series

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

