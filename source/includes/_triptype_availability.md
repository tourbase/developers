## Update trip type availability

This endpoint allows you to batch update availability information for a trip type. The request includes an array of trip start dates and times. By default, Arctic will make the necessary changes so that the trip calendar in Arctic matches the provided list of start dates and times, including creating trips, updating openings and canceling trips.

```php
<?php

require 'init.i.php';

$trip_type = \Arctic\Model\Trip\TripType::load(1);
$response = $trip_type->updateAvailability([
	'range' => [
		'start' => '2019-03-15',
		'end' => '2019-12-15',
	],
	'trips' => [
		[
			'openings' => 16,
			'notes' => 'Testing'
		],
		[
			'start' => '2019-05-01',
			'openings' => 20
		],
		[
			'start' => '2019-06-01',
			'openings' => 20,
		]
	]
]);
```

```shell
curl "https://outfitter.arcticres.com/api/rest/triptype/1/availability"
  -H "Authorization: Bearer token"
  -H "Content-Type: application/json"
  -d @request.json
```

> The availability function takes a JSON payload. For example:

```json
{
	"range": {
		"start": "2019-03-15",
		"end": "2019-06-15"
	},
	"trips": [
		{
			"start": "2019-04-01 14:00:00",
			"openings": 16,
			"notes": "Testing"
		},
		{
			"start": "2019-05-01 14:00:00",
			"openings": 20
		},
		{
			"start": "2019-06-01 13:00:00",
			"openings": 20
		}
	]
}
```

> The above request might generate the following response:

```json
{
    "result": [
        {
            "action": "create",
            "id": 743
        },
        {
            "action": "update",
            "id": 745,
            "delta": {
                "openings": [22, 20]
            }
        },
        {
            "action": "update",
            "id": 747
        },
        {
            "action": "cancel",
            "id": 749,
            "start": "2019-07-23 00:00:00",
            "has_reservations": true
        }
    ]
}
```

### HTTP Request

`POST https://outfitter.arcticres.com/api/rest/triptype/<id>/availability`

### URL Parameters

Parameter | Type | Default | Description
--------- | ---- | ------- | -----------
id | int | *required* | The ID of the trip type.

### Body Attributes

Attribute | Type | Default | Description
--------- | ---- | ------- | -----------
create | boolean | `true` | Trip starts in "trips" that do not exist in Arctic should be created.
update | boolean | `true` | Trip starts in "trips" that have different availability or notes should be updated.
cancel | boolean | `true` | Trip starts in Arctic that do not exist in "trips" should be canceled. If any trips have reservations, an alert will appear on the dashboard to notify reservationists.
simulate | boolean | `false` | If true, the update will only be simulated. The result object will return the changes that are pending.
range | object | | By default, the availability update will effect all trips starting now indefinitely into the future.
trips | array | *required* | An array of "trip" objects.

#### Body: `range` Object

If you want to apply to the update to a specific time range, include a "start" and "end" date or date time, specifying the range to update.

Attribute | Type | Default | Description
--------- | ---- | ------- | -----------
start | date or datetime | *required* | Start of the range to update.
end | date or datetime | *required* | End of the range to update. If "end" is a date, it is inclusive. If "end" is a datetime, it is exclusive.

#### Body: `trip` Object

The `trips` array contains 0 or more trips. The trip object describes when the trip starts and how many openings it has.

Attribute | Type | Default | Description
--------- | ---- | ------- | -----------
start | date or datetime | *required* | The start date or the start date and time of the trip.
openings | int | | Number of openings the trip should have.
remainingopenings | int | | Number of openings the trip should have that are still available.
notes | string | | A note about the trip.

The `trip` object can either specifying `openings` or `remainingopenings`, but not both. If neither are specified, the openings will not be changed (the default openings will be used when creating trips).

### Response Attributes

The response has a result array where each entry specifies what action was taken for the provided list of trip start dates and times. Additional result entries will be added for trips that existed in Arctic, but were not in the provided list, and as a result were canceled.

Attribute | Type | Description
--------- | ---- | -----------
results | array | An array of "result" objects.

#### Response: `result` Object

Attribute | Type | Description
--------- | ---- | -----------
action | string | One of "create" (trip created), "update" (trip updated), "cancel" (trip canceled) or "nothing" (if the relevant action was disabled in the request).
id | int | The ID of the trip that was created, updated or canceled (not available when simulating creations).
delta | object | An object describing the changes when updating a trip.
start | date or datetime | The date or datetime of the trip (when canceling a trip).
has_reservations | boolean | Whether or not a trip had reservations (when canceling a trip).
