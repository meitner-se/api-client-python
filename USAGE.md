<!-- Start SDK Example Usage [usage] -->
```python
# Synchronous Example
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
        client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
    ),
) as m_client:

    res = m_client.schools.list(limit=1, offset=0)

    while res is not None:
        # Handle items

        res = res.next()
```

</br>

The same SDK client can also be used to make asynchronous requests by importing asyncio.

```python
# Asynchronous Example
import asyncio
from meitner import Meitner, models
import os

async def main():

    async with Meitner(
        security=models.Security(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ) as m_client:

        res = await m_client.schools.list_async(limit=1, offset=0)

        while res is not None:
            # Handle items

            res = res.next()

asyncio.run(main())
```
<!-- End SDK Example Usage [usage] -->