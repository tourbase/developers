# Activity

## Activity object

```json
{
    "businessgroupid": 1,
    "parentactivityid": 0,
    "id": 691,
    "type": "Packages\\Arctic\\Reservation\\Models_Reservation",
    "name": "",
    "start": "2020-04-01 14:00:00",
    "end": "2020-04-01 18:30:00",
    "personid": 73,
    "bookingagentid": 0,
    "invoiceid": 712,
    "invoiceitemgroupid": 917,
    "packageid": 0,
    "isgroup": false,
    "groupname": "",
    "groupmode": "burstable",
    "groupinvoice": "separate",
    "grouppricing": null,
    "groupholds": null,
    "groupholdsexpire": null,
    "madeonline": false,
    "source": "",
    "promocode": "",
    "status": "canceled",
    "createdon": "2019-12-24 15:19:53",
    "modifiedon": "2019-12-24 15:28:41",
    "createdbyuserid": 0,
    "deleted": false,
    "manageurl": "http:\/\/reservations.rafting\/g\/AEkAX-w-ljgKiYPu\/manage\/A691",
    "holduntil": null,
    "subactivities": []
}
```

The `activity` object describes an Arctic activity (reservation or rental). The activity contains generic information about the activity such as the customer, booking agent, group mode details, invoice details, etc.

### Attributes

The response returns an activity object. 

Attribute | Type | Description
--------- | ---- | -----------
businessgroupid | int | The business group that contains the activity.
parentactivityid | int | If this activity is part of a group, the ID of the group activity.
id | int | A unique ID for the activity.
type | string | A unique identifier for the type of activity.
name | string | Unused.
start | datetime | The date and time the activity begins.
end | datetime | The date and time the activity ends.
personid | int | The ID of the person who is the primary customer.
bookingagentid | int | The ID of the person who is the booking agent.
invoiceid | int | The ID of the invoice.
invoiceitemgroupid | int | The ID of the invoice section containing all relevant charges.
packageid | int | If this activity is part of a package, the ID of the type of package.
isgroup | bool | If the activity is a group mode activity.
groupname | string | The name of the group (used for searching).
groupmode | string | Either "burstable" or "fixed" depending on whether the group can grow to accomodate more guests.
groupinvoice | string | Either "separate" or "shared" depending on whether reservations within the group get separate or shared invoices.
grouppricing | array or null | Pricing overrides of the group.
groupholds | array or null | Allocations being held for the group.
groupholdsexpire | date or null | The date the group holds will be released.
madeonline | bool | Whether the reservation was made online.
source | string | The referral source for the activity.
promocode | string | The promocodes applied to the activity.
status | string | The activity status ("pending", "unfinished", "finished", "over", "canceled", "noshow").
createdon | datetime | The creation date.
modifiedon | datetime | The modified date.
createdbyuserid | int | The user ID who created the reservation.
deleted | bool | If the trip type was deleted.
manageurl | url | (Optional.) A personalized URL for the guest to manage the activity.
holduntil | date or null | The date at which the activity will expire if no payment has been received.
