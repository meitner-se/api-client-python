# GroupFilterEqualsTypes

The types of the group. A group can have multiple types simultaneously. For preschools (FS), Class and Childcare types are automatically paired - adding Class will automatically include Childcare, and vice versa. Integration note for Mentor type - when importing groups from external systems, it can be difficult to determine whether a group should have the Mentor type. One recommended approach is to not include the Mentor type when creating or updating groups via the API, allowing school administrators to manually configure the Mentor type in Meitner as needed. When updating a group, you can preserve existing types by reading the current group state first and only modifying the specific types your integration manages (e.g., Class, Childcare). This ensures the Mentor type remains under administrator control.


## Values

| Name        | Value       |
| ----------- | ----------- |
| `CLASS`     | Class       |
| `CHILDCARE` | Childcare   |
| `MENTOR`    | Mentor      |