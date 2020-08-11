# Reservation

## Reservation object

```json
{
    "activityid": 691,
    "tripid": 765,
    "allocations": [482],
    "components": [],
    "groupguests": 0,
    "registrationupdatedon": null,
    "registrationcomplete": true,
    "deleted": false,
    "guests": 3,
    "members": [...]
}
```

The `reservation` object describes an Arctic reservation. The reservation contains information about the trip and allocations, while the corresponding `activity` object contains billing and general details.

### Attributes

The response returns a reservation object. 

Attribute | Type | Description
--------- | ---- | -----------
activity | int | A unique ID for the reservation.
tripid | int | The trip that the reservation is on.
allocations | array | Allocations for the reservation.
components | array | List of reservation level components (add-ons).
groupguests | int | The number of guests in the group (if a group mode reservation).
registrationupdatedon | datetime or null | The date and time the registration details were updated.
registrationcomplete | bool | Whether or not reservation registration is complete.
deleted | bool | If the trip type was deleted.
guests | int | The number of guests in the reservations.
members | array | An array of [member (guest) objects](#reservation-member-object).
