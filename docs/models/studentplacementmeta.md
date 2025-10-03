# StudentPlacementMeta

Metadata information for the StudentPlacement


## Fields

| Field                                                                | Type                                                                 | Required                                                             | Description                                                          | Example                                                              |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `created_at`                                                         | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_check_mark:                                                   | Timestamp when the resource was created                              | 2024-01-15T10:30:00Z                                                 |
| `created_by`                                                         | *OptionalNullable[str]*                                              | :heavy_minus_sign:                                                   | User who created the resource                                        | 987fcdeb-51a2-43d1-b567-123456789abc                                 |
| `updated_at`                                                         | [date](https://docs.python.org/3/library/datetime.html#date-objects) | :heavy_minus_sign:                                                   | Timestamp when the resource was last updated                         | 2024-01-15T14:45:00Z                                                 |
| `updated_by`                                                         | *OptionalNullable[str]*                                              | :heavy_minus_sign:                                                   | User who last updated the resource                                   | 987fcdeb-51a2-43d1-b567-123456789abc                                 |