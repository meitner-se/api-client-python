# EmployeePlacementCreateExternal

External is the External-object used on Update and Create operations, since it should only be allowed to set SourceID for the guardian, the Source-field is not included.


## Fields

| Field                         | Type                          | Required                      | Description                   | Example                       |
| ----------------------------- | ----------------------------- | ----------------------------- | ----------------------------- | ----------------------------- |
| `source_id`                   | *str*                         | :heavy_check_mark:            | The ID of the external source | 12345678                      |