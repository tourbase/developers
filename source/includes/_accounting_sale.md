## Accounting sale object

```json
{
	"invoiceitemgroupid": 882,
	"id": 4235,
	"accountid": 4,
	"businessgroupid": 0,
	"amount": "0.14",
	"accrualdate": "2019-04-22",
	"time": "2019-04-22 21:10:20"
}
```

The `accountingsale` object describes a line item that was added / removed to an invoice, irrespective of whether any transactions have taken place. For example, positive amounts indicate a line item or charge were added to an invoice (e.g., a guest booked an activity), while negative amounts indicate a line item or charge was removed from an invoice (e.g., an activity was canceled or a discount was added).

**Note:** Accounting records do not change. After an entry is added, it will not change or be deleted. If subsequent accounting changes are made, new entries will be added to make the appropriate adjustments.

### Attributes

The response returns a trip type object. 

Attribute | Type | Description
--------- | ---- | -----------
invoiceitemgroupid | int | The invoice group (section) that produced the line item.
id | int | A unique ID for the accounting sale.
accountid | int | The account ID for the line item.
businessgroupid | int | The business group ID for the line item. Will correspond with activity business group in most cases.
amount | decimal | String representation of amount.
accrualdate | date | The accrual date for the charge. Will correspond with activity start date if associated with an activity.
time | datetime | The date and time when the adjustment was made.
