# SchoolSearchNotNullExternal

External is a reusable object that can be used to store external information about the school from another system, used for third-party integration tracking.


## Fields

| Field                                        | Type                                         | Required                                     | Description                                  | Example                                      |
| -------------------------------------------- | -------------------------------------------- | -------------------------------------------- | -------------------------------------------- | -------------------------------------------- |
| `source_id`                                  | *OptionalNullable[bool]*                     | :heavy_minus_sign:                           | The ID of the external source                | **Example 1:** true<br/>**Example 2:** <nil> |
| `source`                                     | *OptionalNullable[bool]*                     | :heavy_minus_sign:                           | The source of the external information       | **Example 1:** true<br/>**Example 2:** <nil> |