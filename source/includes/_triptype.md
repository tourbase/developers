# Trip type

## Trip type object

```json
{
    "businessgroupid": 1,
    "parenttripid": 0,
    "id": 1,
    "subtripstartoffset": null,
    "starttime": null,
    "name": "Rio Grande Float",
    "shortname": "RGF",
    "color": "#a7194b",
    "openings": 24,
    "duration": "72:00:00",
    "registrationformid": 2,
    "orenable": true,
    "orname": "",
    "ordescription": "",
    "ordetails": "",
    "orimageid": 0,
    "orcutoff": "168:00:00",
    "orminimumguests": 2,
    "registrationcutoffdays": 3,
    "attachsameasparent": true,
    "notes": "",
    "accountid": 39,
    "paymentplanid": 1,
    "cancellationpolicyid": 0,
    "createdon": "2013-10-29 12:22:00",
    "modifiedon": "2018-07-30 17:18:35",
    "createdbyuserid": 0,
    "deleted": false,
    "evaluationid": "3",
    "socialsite": "trip",
    "pricinglevels": [
        {
            "parenttype": "triptype",
            "parentid": 1,
            "id": 1,
            "name": "Adult",
            "default": true,
            "uniquename": "Adult",
            "description": "",
            "amount": "500.00",
            "invoicesubitems": null,
            "showonline": true,
            "createdon": "2013-10-29 12:22:01",
            "modifiedon": "2013-10-29 12:22:01",
            "deleted": false
        },
        {
            "parenttype": "triptype",
            "parentid": 1,
            "id": 2,
            "name": "Youth",
            "default": false,
            "uniquename": "Youth",
            "description": "18 and under",
            "amount": "390.00",
            "invoicesubitems": null,
            "showonline": true,
            "createdon": "2013-10-29 12:22:01",
            "modifiedon": "2013-10-29 12:22:01",
            "deleted": false
        }
    ],
    "components": [
        {
            "parenttype": "triptype",
            "parentid": 1,
            "id": 1,
            "name": "T-shirt",
            "uniquename": "T-shirt",
            "addto": "member",
            "type": "optional",
            "setname": "",
            "description": "",
            "showonline": true,
            "onlinedescription": "Arctic Reservations T-shirt",
            "orimageid": 14,
            "isdefault": false,
            "price": "25.00",
            "accountid": 50,
            "openings": null,
            "inventoryitemid": 0,
            "rentalitems": [],
            "order": 0,
            "createdon": "2013-10-29 12:22:01",
            "modifiedon": "2015-05-23 12:08:08",
            "deleted": false
        }
    ]
}
```

The `triptype` object describes an Arctic trip type. Trip types describe a standard itinerary, and are used to create individual trips on the calendar. The trip type defines standard pricing, add-ons and information, which can then be customized on a per-trip basis.

### Attributes

The response returns a trip type object. 

Attribute | Type | Description
--------- | ---- | -----------
businessgroupid | int | The business group that contains the trip type.
parenttripid | int | If this is a sub trip type, references the ID of the parent trip type. Used for selling portions of longer trips.
id | int | A unique ID for the trip type.
subtripstartoffset | time or null | For sub trip types, the start time offset for the sub trip.
starttime | time or null | For parent trips, the default start time.
name | string | The name of the trip type.
shortname | string | Optionally, a short name for the trip type.
color | string | The hex color associated with the trip type.
openings | int | The number of openings for the trip type.
duration | time | The duration of the trip.
registrationformid | int | The registration form associated with trip type.
orenable | boolean | Whether or not the trip accepts online reservations.
orname | string | An alternative name to use when showing the trip type online.
ordescription | string | An online description.
ordetails | string | Details to show during the online booking process.
orimageid | int | An image associated with the trip type to show online.
orcutoff | time | The time before the trip starts that online reservations should be disabled.
orminimumguests | int | The minimum number of guests required for booking an empty trip.
registrationcutoffdays | int | The number of days before the trip starts to cutoff online registration.
attachsameasparent | bool | For sub trip types, use the same attachments as the parent trip type.
notes | string | Trip type notes.
accountid | int | The account ID used for revenue for this trip type.
paymentplanid | int | The payment plan associated with the trip type.
socialsite | string | (Optional.) If present, when the social site becomes available. Either at "reservation" or after the "trip".
cancellationpolicyid | int | The cancellation policy associated with the trip type.
evaluationid | int | (Optional.) The evaluation associated with the trip type.
createdon | datetime | The creation date.
modifiedon | datetime | The modified date.
deleted | bool | If the trip type was deleted.
pricinglevels | array | An array of [pricing level objects](#trip-pricing-level-object).
components | array | An array of [add-on objects](#trip-add-on-object).
