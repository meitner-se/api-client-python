# EmployeeFilterNotContainsExternal

External is a reusable object that can be used to store external information about the employee placement from another system, used for third-party integration tracking.


## Fields

| Field                                  | Type                                   | Required                               | Description                            | Example                                |
| -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- | -------------------------------------- |
| `source_id`                            | List[*str*]                            | :heavy_minus_sign:                     | The ID of the external source          | [<br/>"example"<br/>]                  |
| `source`                               | List[*str*]                            | :heavy_minus_sign:                     | The source of the external information | [<br/>"example"<br/>]                  |