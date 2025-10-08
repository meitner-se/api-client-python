# EmployeeSearchNotEqualsExternal

External is a reusable object that can be used to store external information about the employee placement from another system, used for third-party integration tracking.


## Fields

| Field                                  | Type                                   | Required                               | Description                            | Example                                |
| -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- |
| `source_id`                            | *OptionalNullable[str]*                | :heavy_minus_sign:                     | The ID of the external source          | example                                |
| `source`                               | *OptionalNullable[str]*                | :heavy_minus_sign:                     | The source of the external information | example                                |