# GuardianExternal

External is a reusable object that can be used to store external information about the guardian from another system, used for third-party integration tracking.


## Fields

| Field                                  | Type                                   | Required                               | Description                            | Example                                |
| -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- |
| `source_id`                            | *OptionalNullable[str]*                | :heavy_minus_sign:                     | The ID of the external source          | 12345678                               |
| `source`                               | *OptionalNullable[str]*                | :heavy_minus_sign:                     | The source of the external information | ExternalIntegrationAPI                 |