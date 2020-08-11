## Update activity status

This endpoint allows updating the status for the activity, marking it as canceled, no-show, or active. When canceling or marking an activity as no-show, a cancellation fee and credit properties can also be specified.

```php
<?php

require 'init.i.php';

$activity = \Arctic\Model\Activity\Activity::load(601);
$activity->setStatus('canceled');
```

```shell
curl "https://outfitter.arcticres.com/api/rest/activity/601/status"
  -H "Authorization: Bearer token"
  -H "Content-Type: application/json"
  -d @request.json
```

> The status function takes a JSON payload. For example:

```json
{
  "status": "canceled",
  "cancellation_fee": null,
  "preserve_commissions": false
}
```

> The above request will return an updated activity object.

### HTTP Request

`POST https://outfitter.arcticres.com/api/rest/activity/<id>/status`

### URL Parameters

Parameter | Type | Default | Description
--------- | ---- | ------- | -----------
id | int | *required* | The ID of the activity.

### Body Attributes

Attribute | Type | Default | Description
--------- | ---- | ------- | -----------
status | boolean | *required* | The desired status: "active", "canceled", "noshow".
cancellation_fee | number | `null` | The cancellation fee to assess (when canceling or marking an activity as no-show).
preserve_commissions | bool | `false` | Whether or not booking agent commissions should apply to the cancellation fee (when canceling or marking an activity as no-show).

### Response

Upon success, the response is an updated activity object reflecting the change in status. If the status can not be changed, an HTTP error response will be returned along with a standard error object describing why the change could not be made.
