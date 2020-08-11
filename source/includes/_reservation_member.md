## Reservation member object

```json
{
  "activityid": 691,
  "id": 1150,
  "personid": 73,
  "pricingleveluniquename": "Adult",
  "pricinglevelname": "Adult",
  "pricinglevelcost": "85.00",
  "components": [],
  "registrationupdatedon": null,
  "registrationcomplete": true,
  "registrationby": "",
  "createdon": "2019-12-24 15:19:53",
  "modifiedon": "2019-12-24 15:19:53",
  "createdbyuserid": 0,
  "deleted": false
}
```

The `member` object describes one guest in a reservation.

### Attributes

The response returns a trip type object. 

Attribute | Type | Description
--------- | ---- | -----------
activityid | int | The ID of the activity / reservation.
id | int | A unique ID for the pricing level.
personid | int | The ID of the person, if specified.
pricingleveluniquename | string | The pricing level unique name. (See the [pricing level objects](#trip-pricing-level-object).)
pricinglevelname | string | The pricing level name.
pricinglevelcost | number | The pricing level price.
components | array | List of guest level components (add-ons).
registrationupdatedon | datetime or null | The date and time the registration details were updated.
registrationcomplete | bool | Whether or not guest registration is complete.
registrationby | string | Who completed the registration (determines who can see / edit it).
createdon | datetime | The creation date.
modifiedon | datetime | The modified date.
createdbyuserid | int | The user ID who created the reservation.
deleted | bool | If the pricing level was deleted.
