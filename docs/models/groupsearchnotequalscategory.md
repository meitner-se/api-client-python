# GroupSearchNotEqualsCategory

If the category is Education, the ModeratorIDs have to be employees and the MemberIDs have to be students of the school. If the category is Other, it will not be possible to use the IsClass, IsChildcare and IsMentor fields.


## Example Usage

```python
from meitner.models import GroupSearchNotEqualsCategory
value: GroupSearchNotEqualsCategory = "Education"
```


## Values

- `"Education"`
- `"Other"`
