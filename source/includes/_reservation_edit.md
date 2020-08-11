## Create reservation

This endpoint allows creating a new reservation. Only a subset of reservation and activity fields can be specified, and often only a smaller subset need to be specified.

```php
<?php

require 'init.i.php';

// build reservation
$reservation = new \Arctic\Model\Reservation\Reservation();
$reservation->activity->personid = 73;
$reservation->tripid = 765;
$reservation->membercounts = [
	'Adult' => 2,
	'Youth' => 1
];

// insert the reservation
$reservation->insert();
```

```shell
curl "https://outfitter.arcticres.com/api/rest/reservation"
  -H "Authorization: Bearer token"
  -H "Content-Type: application/json"
  -d @request.json
```

> The create function takes a JSON payload. For example:

```json
{
    "tripid": 765,
    "membercounts": {
        "Adult": 2,
        "Youth": 1
    },
    "activity": {
        "personid": 73
    }
}
```

> The above request will return the new reservation object object.

### HTTP Request

`POST https://outfitter.arcticres.com/api/rest/reservation`

### Body Attributes

The response body can include properties of the [reservation object](#reservation-object), as well as the following additional attributes:

Attribute | Type | Default | Description
--------- | ---- | ------- | -----------
activity | object | `{}` | The activity details. See the [activity object](#activity-object) for properties. Must include and specify `personid` property when creating a reservation.
members | array | | An array of members (guests). See the [reservation member object](#reservation-member-object) for properties.
membercounts | object | `{}` | Rather than specifying individual members (guests), you can specify an associative array where the keys are pricing levels (either pricing level name or unique name) and values are the guest counts.
componentcounts | object | `{}` | Rather than specifying individual members (guests), you can specify an associative array where the keys are components (add-ons, either component name or component unique name) and values are the guest counts (for per guest add-ons) or booleans (for per reservation add-ons).

Notes:

* You can either specify `members` OR `membercounts` and/or `componentcounts`. Using `membercounts` and `componentcounts` are the recommended approach, unless you need to specify individual guest details.
* When creating or moving a reservation to a new trip, you must specify either `members` OR `membercounts` to calculate pricing.
* When creating a reservation, you must specify the `tripid` and the activity `personid`.


## Update reservation

Once created, reservations can be updated in the same format. Updates can be used to update ancillary information, as well as move reservations to new trips or change group composition.

```php
<?php

require 'init.i.php';

// load reservation
$reservation = \Arctic\Model\Reservation\Reservation::load(690);

// change information
$reservation->activity->personid = 44;
$reservation->componentcounts = [
	'Camera Rental' => 2
];

// issue update command
$reservation->update();
```

```shell
curl "https://outfitter.arcticres.com/api/rest/reservation/690"
  -H "Authorization: Bearer token"
  -H "Content-Type: application/json"
  -X PUT
  -d @request.json
```

> The update function takes a JSON payload. For example:

```json
{
    "componentcounts": {
        "Camera Rental": 2
    },
    "activity": {
        "personid": 44
    }
}
```

> The above request will return the updated reservation object object.

### HTTP Request

`PUT https://outfitter.arcticres.com/api/rest/reservation/<id>`

### URL Parameters

Parameter | Type | Default | Description
--------- | ---- | ------- | -----------
id | int | *required* | The ID of the reservation.

### Body Attributes

See the above details for the body attributes when creating a reservation.

### Response Attributes

The response returns a [reservation object](#reservation-object).
