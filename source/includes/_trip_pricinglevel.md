## Trip pricing level object

```json
{
	"parenttype": "trip",
	"parentid": 439,
	"id": 3024,
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
}
```

The `pricinglevel` object describes a pricing level, which is either part of a trip type or a trip.

### Attributes

The response returns a trip type object. 

Attribute | Type | Description
--------- | ---- | -----------
parenttype | string | Either "triptype" or "trip", depending on whether the pricing level is associated with a trip type or trip.
parentid | int | The ID of the trip type or trip.
id | int | A unique ID for the pricing level.
name | string | The name of the pricing level.
default | bool | Whether or not this is the default pricing level for the trip type or trip.
uniquename | string | An internally generated unique name.
description | string | An optional description of the pricing level.
amount | number | The price.
invoicesubitems | array or null | An array of associated charges for the pricing level.
showonline | boolean | Whether or not the pricing level is visible online.
createdon | datetime | The creation date.
modifiedon | datetime | The modified date.
deleted | bool | If the pricing level was deleted.
