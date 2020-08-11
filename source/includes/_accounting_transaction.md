## Accounting transaction object

```json
{
	"transactionid": 398,
	"id": 630,
	"accountid": 2,
	"businessgroupid": 0,
	"transactiondate": "2019-03-05 16:30:57",
	"accrualdate": "2019-03-05",
	"amount": "7.25",
	"exported": false,
	"reportid": 0,
	"createdon": "2019-04-18 19:25:24"
}
```

The `accountingtransaction` object describes how income was allocate towards previous line item charges (see [line item API details](#accounting-sale-object) for more details). That is, when a transaction occurs (payment or refund), the income will be applied to or credited from the line items on the invoice, generating new accounting transaction records.

**Note:** Accounting records do not change. After an entry is added, it will not change or be deleted. If subsequent accounting changes are made, new entries will be added to make the appropriate adjustments.

### Attributes

The response returns a trip type object. 

Attribute | Type | Description
--------- | ---- | -----------
transactionid | int | The transaction ID that is being applied.
id | int | A unique ID for the accounting transaction.
accountid | int | The account ID that the income is being applied to / credited from.
businessgroupid | int | The business group ID the income is being applied to / credited from. Will correspond with activity business group in most cases.
transactiondate | datetime | The date and time that the transaction was processed.
accrualdate | date | The accrual date for the charge. Will correspond with activity start date if associated with an activity.
amount | decimal | String representation of amount.
exported | boolean | Whether or not the entry has been exported via the end of day balance report.
reportid | int | The ID of the end of day balance report where this allocation appeared.
createdon | datetime | The date and time when the allocation was made.
