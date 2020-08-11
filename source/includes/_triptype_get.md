## Get trip type object

You can fetch a specific trip type object by ID.

```php
<?php

require 'init.i.php';

$trip_type = \Tourbase\Model\Trip\TripType::load(1);
```

```shell
curl "https://outfitter.tourbase.com/api/rest/triptype/1"
  -H "Authorization: Bearer token"
```

> The above request returns a trip type object.

### HTTP Request

`GET https://outfitter.tourbase.com/api/rest/triptype/<id>`

### URL Parameters

Parameter | Type | Default | Description
--------- | ---- | ------- | -----------
id | int | *required* | The ID of the trip type.

### Response Attributes

The response returns a [trip type object](#trip-type-object).

