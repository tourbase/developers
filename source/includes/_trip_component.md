## Trip add-on object

```json
{
	"parenttype": "trip",
	"parentid": 439,
	"id": 1809,
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
```

The `component` object describes a trip add-on, which is either part of a trip type or a trip.

### Attributes

The response returns a trip type object. 

Attribute | Type | Description
--------- | ---- | -----------
parenttype | string | Either "triptype" or "trip", depending on whether the add-on is associated with a trip type or trip.
parentid | int | The ID of the trip type or trip.
id | int | A unique ID for the add-on.
name | string | The name of the add-on.
addto | string | Either "reservation" (available once per reservation) or "member" (available once per guest).
type | string | Either "required" (used for required inventory), "optional" (yes/no add-ons), or "set" (one of many choices).
setname | string | If an add-on is part of the set, this specifies the setname. Each reservation or guest (depending on addto) has to select one of the add-ons in the set.
description | string | An optional description of the add-on.
showonline | boolean | Whether or not the add-on is visible online.
onlinedescription | string | An additional description of the add-on to appear online.
orimageid | int | An image associated with the add-on to show online.
isdefault | bool | Whether this add-on is included with new reservations by default.
price | number | The price of the add-on.
accountid | int | The account ID used for revenue for this add-on.
openings | int or null | An optional limit of how many add-ons can be purchased per trip.
inventoryitemid | int | The ID of the inventory item used to enforce openings.
rentalitems | array | An array describing required inventory for this add-on.
order | int | Override the sorting of the add-ons.
createdon | datetime | The creation date.
modifiedon | datetime | The modified date.
deleted | bool | If the add-on was deleted.
