# Log

## Query log entries


```php
<?php

require 'init.i.php';

// not yet available via the PHP API
```

```shell
curl "https://outfitter.arcticres.com/api/rest/log?models=reservation,activity"
  -H "Authorization: Bearer token"
  -H "Content-Type: application/json"
```

> The above request might generate the following response:

```json
{
    "log": [
        {
        "id": "34468:6",
        "timestamp": "2019-01-18 14:36:44",
        "type": "update",
        "model": "reservation",
        "modelid": "1456",
        "delta": {
            "deleted": [
                false,
                true
            ],
            "allocations": [
                [
                    3264,
                    3265,
                    3266
                ],
                []
            ]
        }
    ],
    "next": "https://outfitter.arcticres.com/api/rest/log?models=reservation,activity&before_id=34468:6"
}
```

The `log` response contains an array of log entries describing edits that were made in Arctic Reservations, filtering the results based on the provided query parameters. Log entries allow replaying or analyzing a set of changes. Log entries are available for 14 days, and can be queried in either ascending or descending order. 

Because only a limited number of log entries are available via the API, pagination works differently than the standard implementation in other parts of the API. The API response includes the URL to receive the next page of results.

### URL Parameters

Parameter | Type | Default | Description
--------- | ---- | ------- | -----------
models | array or string | *required* | An array or comma separated string of model names desired.
before | datetime | *none* | If specified, will return log events that occurred on or before this time.
before_id | string | *none* | If specified, will return log events that occurred immediately before the log event ID.
after | datetime | *none* | If specified, will return log events that occurred on or after this time.
after_id | string | *none* | If specified, will return log events that occurred immediately after the log event ID.

If "before" or "before_id" are specified, the log entries are returned in descending order (newest to oldest). If "after" or "after_id" are specified, the log entries are returned in ascending order (oldest to newest). If neither are specified, the API returns the most recent entries in descending order.

### Attributes

The log entry object includes the following attributes.

Attribute | Type | Description
--------- | ---- | -----------
log | array | An array of [log entry objects](#log-entry-object)
next | string or null | If applicable, the API URL to generate the next page of log entries.


## Log entry object

```json
{
    "id": "34468:6",
    "timestamp": "2019-01-18 14:36:44",
    "type": "update",
    "model": "reservation",
    "modelid": "1456",
    "delta": {
        "deleted": [
            false,
            true
        ],
        "allocations": [
            [
                3264,
                3265,
                3266
            ],
            []
        ]
    }
}
```

The `log` object describes a set of changes to a model. 

### Attributes

The log entry object includes the following attributes.

Attribute | Type | Description
--------- | ---- | -----------
id | string | A unique ID for the log entry, composed of two numbers separated by a colon.
timestamp | datetime | The time when the event occurred.
type | string | Describes the type of changes made. Specifically: "create" if the model was created, "update" if an existing model was updated, "remove" if an existing model was deleted, or "note" for other events.
model | string | The type of model.
modelid | int | The unique ID of the model.
delta | object | (Optional.) For "update" events, this object describes the changes that were made to the model.
