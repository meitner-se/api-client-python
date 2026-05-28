# Units

## Overview

### Available Operations

* [list](#list) - List Units
* [create](#create) - Create a new Unit
* [search](#search) - Search Units
* [get](#get) - Get a Unit
* [update](#update) - Update a Unit

## list

Returns a paginated list of all `Units` in your organization.

### Example Usage

<!-- UsageSnippet language="python" operationID="UnitList" method="get" path="/unit" example="responseExample" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.units.list(limit=1, offset=0)

    while res is not None:
        # Handle items

        res = res.next()

```

### Parameters

| Parameter                                                                                     | Type                                                                                          | Required                                                                                      | Description                                                                                   | Example                                                                                       |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `limit`                                                                                       | *Optional[int]*                                                                               | :heavy_minus_sign:                                                                            | The maximum number of Units to return (default: 50) when listing Units                        | 1                                                                                             |
| `offset`                                                                                      | *Optional[int]*                                                                               | :heavy_minus_sign:                                                                            | The number of Units to skip before starting to return results (default: 0) when listing Units | 0                                                                                             |
| `retries`                                                                                     | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                              | :heavy_minus_sign:                                                                            | Configuration to override the default retry behavior of the client.                           |                                                                                               |

### Response

**[models.UnitListResponse](../../models/unitlistresponse.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.Error400ResponseBody | 400                         | application/json            |
| errors.Error401ResponseBody | 401                         | application/json            |
| errors.Error403ResponseBody | 403                         | application/json            |
| errors.Error404ResponseBody | 404                         | application/json            |
| errors.Error409ResponseBody | 409                         | application/json            |
| errors.Error429ResponseBody | 429                         | application/json            |
| errors.Error500ResponseBody | 500                         | application/json            |
| errors.MeitnerDefaultError  | 4XX, 5XX                    | \*/\*                       |

## create

Create a new Unit

### Example Usage: errorExample

<!-- UsageSnippet language="python" operationID="UnitCreate" method="post" path="/unit" example="errorExample" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.units.create(title="Norra distriktet", external={
        "source_id": "12345678",
    }, description="Norra grundskole- och förskoleenheten")

    # Handle response
    print(res)

```
### Example Usage: requestExample

<!-- UsageSnippet language="python" operationID="UnitCreate" method="post" path="/unit" example="requestExample" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.units.create(title="Norra distriktet", external={
        "source_id": "12345678",
    }, description="Norra grundskole- och förskoleenheten")

    # Handle response
    print(res)

```
### Example Usage: responseExample

<!-- UsageSnippet language="python" operationID="UnitCreate" method="post" path="/unit" example="responseExample" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.units.create(title="Norra distriktet", external={
        "source_id": "12345678",
    }, description="Norra grundskole- och förskoleenheten")

    # Handle response
    print(res)

```
### Example Usage: validationError

<!-- UsageSnippet language="python" operationID="UnitCreate" method="post" path="/unit" example="validationError" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.units.create(title="Norra distriktet", external={
        "source_id": "12345678",
    }, description="Norra grundskole- och förskoleenheten")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                             | Type                                                                                                                                                                  | Required                                                                                                                                                              | Description                                                                                                                                                           | Example                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `title`                                                                                                                                                               | *str*                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                    | The title of the unit                                                                                                                                                 | Norra distriktet                                                                                                                                                      |
| `external`                                                                                                                                                            | [Optional[models.UnitCreateExternal]](../../models/unitcreateexternal.md)                                                                                             | :heavy_minus_sign:                                                                                                                                                    | External is the External-object used on Update and Create operations, since it should only be allowed to set SourceID for the unit, the Source-field is not included. | {<br/>"sourceID": "12345678"<br/>}                                                                                                                                    |
| `description`                                                                                                                                                         | *OptionalNullable[str]*                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                    | The description of the unit                                                                                                                                           | **Example 1:** Norra grundskole- och förskoleenheten<br/>**Example 2:** null                                                                                          |
| `retries`                                                                                                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                      | :heavy_minus_sign:                                                                                                                                                    | Configuration to override the default retry behavior of the client.                                                                                                   |                                                                                                                                                                       |

### Response

**[models.UnitCreateResponse](../../models/unitcreateresponse.md)**

### Errors

| Error Type                            | Status Code                           | Content Type                          |
| ------------------------------------- | ------------------------------------- | ------------------------------------- |
| errors.Error400ResponseBody           | 400                                   | application/json                      |
| errors.Error401ResponseBody           | 401                                   | application/json                      |
| errors.Error403ResponseBody           | 403                                   | application/json                      |
| errors.Error404ResponseBody           | 404                                   | application/json                      |
| errors.Error409ResponseBody           | 409                                   | application/json                      |
| errors.UnitCreate422ResponseBodyError | 422                                   | application/json                      |
| errors.Error429ResponseBody           | 429                                   | application/json                      |
| errors.Error500ResponseBody           | 500                                   | application/json                      |
| errors.MeitnerDefaultError            | 4XX, 5XX                              | \*/\*                                 |

## search

Search for `Units` with filtering capabilities.

### Example Usage: errorExample

<!-- UsageSnippet language="python" operationID="UnitSearch" method="post" path="/unit/_search" example="errorExample" -->
```python
from meitner import Meitner, models
from meitner.utils import parse_datetime
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.units.search(filter_={
        "equals": {
            "id": "123e4567-e89b-12d3-a456-426614174000",
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "created_by": "123e4567-e89b-12d3-a456-426614174000",
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_by": "123e4567-e89b-12d3-a456-426614174000",
            },
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "title": "example",
            "description": "example",
        },
        "not_equals": {
            "id": "123e4567-e89b-12d3-a456-426614174000",
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "created_by": "123e4567-e89b-12d3-a456-426614174000",
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_by": "123e4567-e89b-12d3-a456-426614174000",
            },
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "title": "example",
            "description": "example",
        },
        "greater_than": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
        },
        "smaller_than": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
        },
        "greater_or_equal": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
        },
        "smaller_or_equal": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
        },
        "contains": {
            "id": [
                "123e4567-e89b-12d3-a456-426614174000",
            ],
            "meta": {
                "created_by": [
                    "123e4567-e89b-12d3-a456-426614174000",
                ],
                "updated_by": [
                    "123e4567-e89b-12d3-a456-426614174000",
                ],
            },
            "external": {
                "source_id": [
                    "example",
                ],
                "source": [
                    "example",
                ],
            },
            "title": [
                "example",
            ],
            "description": [
                "example",
            ],
        },
        "not_contains": {
            "id": [
                "123e4567-e89b-12d3-a456-426614174000",
            ],
            "meta": {
                "created_by": [
                    "123e4567-e89b-12d3-a456-426614174000",
                ],
                "updated_by": [
                    "123e4567-e89b-12d3-a456-426614174000",
                ],
            },
            "external": {
                "source_id": [
                    "example",
                ],
                "source": [
                    "example",
                ],
            },
            "title": [
                "example",
            ],
            "description": [
                "example",
            ],
        },
        "like": {
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "title": "example",
            "description": "example",
        },
        "not_like": {
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "title": "example",
            "description": "example",
        },
        "null": {
            "meta": {
                "created_by": True,
                "updated_at": True,
                "updated_by": True,
            },
            "external": {
                "source_id": True,
                "source": True,
            },
            "description": True,
        },
        "not_null": {
            "meta": {
                "created_by": True,
                "updated_at": True,
                "updated_by": True,
            },
            "external": {
                "source_id": True,
                "source": True,
            },
            "description": True,
        },
        "or_condition": True,
    }, limit=1, offset=0)

    while res is not None:
        # Handle items

        res = res.next()

```
### Example Usage: requestExample

<!-- UsageSnippet language="python" operationID="UnitSearch" method="post" path="/unit/_search" example="requestExample" -->
```python
from meitner import Meitner, models
from meitner.utils import parse_datetime
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.units.search(filter_={
        "equals": {
            "id": "123e4567-e89b-12d3-a456-426614174000",
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "created_by": "123e4567-e89b-12d3-a456-426614174000",
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_by": "123e4567-e89b-12d3-a456-426614174000",
            },
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "title": "example",
            "description": "example",
        },
        "not_equals": {
            "id": "123e4567-e89b-12d3-a456-426614174000",
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "created_by": "123e4567-e89b-12d3-a456-426614174000",
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_by": "123e4567-e89b-12d3-a456-426614174000",
            },
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "title": "example",
            "description": "example",
        },
        "greater_than": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
        },
        "smaller_than": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
        },
        "greater_or_equal": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
        },
        "smaller_or_equal": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
        },
        "contains": {
            "id": [
                "123e4567-e89b-12d3-a456-426614174000",
            ],
            "meta": {
                "created_by": [
                    "123e4567-e89b-12d3-a456-426614174000",
                ],
                "updated_by": [
                    "123e4567-e89b-12d3-a456-426614174000",
                ],
            },
            "external": {
                "source_id": [
                    "example",
                ],
                "source": [
                    "example",
                ],
            },
            "title": [
                "example",
            ],
            "description": [
                "example",
            ],
        },
        "not_contains": {
            "id": [
                "123e4567-e89b-12d3-a456-426614174000",
            ],
            "meta": {
                "created_by": [
                    "123e4567-e89b-12d3-a456-426614174000",
                ],
                "updated_by": [
                    "123e4567-e89b-12d3-a456-426614174000",
                ],
            },
            "external": {
                "source_id": [
                    "example",
                ],
                "source": [
                    "example",
                ],
            },
            "title": [
                "example",
            ],
            "description": [
                "example",
            ],
        },
        "like": {
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "title": "example",
            "description": "example",
        },
        "not_like": {
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "title": "example",
            "description": "example",
        },
        "null": {
            "meta": {
                "created_by": True,
                "updated_at": True,
                "updated_by": True,
            },
            "external": {
                "source_id": True,
                "source": True,
            },
            "description": True,
        },
        "not_null": {
            "meta": {
                "created_by": True,
                "updated_at": True,
                "updated_by": True,
            },
            "external": {
                "source_id": True,
                "source": True,
            },
            "description": True,
        },
        "or_condition": True,
    }, limit=1, offset=0)

    while res is not None:
        # Handle items

        res = res.next()

```
### Example Usage: responseExample

<!-- UsageSnippet language="python" operationID="UnitSearch" method="post" path="/unit/_search" example="responseExample" -->
```python
from meitner import Meitner, models
from meitner.utils import parse_datetime
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.units.search(filter_={
        "equals": {
            "id": "123e4567-e89b-12d3-a456-426614174000",
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "created_by": "123e4567-e89b-12d3-a456-426614174000",
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_by": "123e4567-e89b-12d3-a456-426614174000",
            },
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "title": "example",
            "description": "example",
        },
        "not_equals": {
            "id": "123e4567-e89b-12d3-a456-426614174000",
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "created_by": "123e4567-e89b-12d3-a456-426614174000",
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_by": "123e4567-e89b-12d3-a456-426614174000",
            },
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "title": "example",
            "description": "example",
        },
        "greater_than": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
        },
        "smaller_than": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
        },
        "greater_or_equal": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
        },
        "smaller_or_equal": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
        },
        "contains": {
            "id": [
                "123e4567-e89b-12d3-a456-426614174000",
            ],
            "meta": {
                "created_by": [
                    "123e4567-e89b-12d3-a456-426614174000",
                ],
                "updated_by": [
                    "123e4567-e89b-12d3-a456-426614174000",
                ],
            },
            "external": {
                "source_id": [
                    "example",
                ],
                "source": [
                    "example",
                ],
            },
            "title": [
                "example",
            ],
            "description": [
                "example",
            ],
        },
        "not_contains": {
            "id": [
                "123e4567-e89b-12d3-a456-426614174000",
            ],
            "meta": {
                "created_by": [
                    "123e4567-e89b-12d3-a456-426614174000",
                ],
                "updated_by": [
                    "123e4567-e89b-12d3-a456-426614174000",
                ],
            },
            "external": {
                "source_id": [
                    "example",
                ],
                "source": [
                    "example",
                ],
            },
            "title": [
                "example",
            ],
            "description": [
                "example",
            ],
        },
        "like": {
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "title": "example",
            "description": "example",
        },
        "not_like": {
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "title": "example",
            "description": "example",
        },
        "null": {
            "meta": {
                "created_by": True,
                "updated_at": True,
                "updated_by": True,
            },
            "external": {
                "source_id": True,
                "source": True,
            },
            "description": True,
        },
        "not_null": {
            "meta": {
                "created_by": True,
                "updated_at": True,
                "updated_by": True,
            },
            "external": {
                "source_id": True,
                "source": True,
            },
            "description": True,
        },
        "or_condition": True,
    }, limit=1, offset=0)

    while res is not None:
        # Handle items

        res = res.next()

```
### Example Usage: validationError

<!-- UsageSnippet language="python" operationID="UnitSearch" method="post" path="/unit/_search" example="validationError" -->
```python
from meitner import Meitner, models
from meitner.utils import parse_datetime
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.units.search(filter_={
        "equals": {
            "id": "123e4567-e89b-12d3-a456-426614174000",
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "created_by": "123e4567-e89b-12d3-a456-426614174000",
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_by": "123e4567-e89b-12d3-a456-426614174000",
            },
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "title": "example",
            "description": "example",
        },
        "not_equals": {
            "id": "123e4567-e89b-12d3-a456-426614174000",
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "created_by": "123e4567-e89b-12d3-a456-426614174000",
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_by": "123e4567-e89b-12d3-a456-426614174000",
            },
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "title": "example",
            "description": "example",
        },
        "greater_than": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
        },
        "smaller_than": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
        },
        "greater_or_equal": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
        },
        "smaller_or_equal": {
            "meta": {
                "created_at": parse_datetime("2024-01-15T10:30:00Z"),
                "updated_at": parse_datetime("2024-01-15T10:30:00Z"),
            },
        },
        "contains": {
            "id": [
                "123e4567-e89b-12d3-a456-426614174000",
            ],
            "meta": {
                "created_by": [
                    "123e4567-e89b-12d3-a456-426614174000",
                ],
                "updated_by": [
                    "123e4567-e89b-12d3-a456-426614174000",
                ],
            },
            "external": {
                "source_id": [
                    "example",
                ],
                "source": [
                    "example",
                ],
            },
            "title": [
                "example",
            ],
            "description": [
                "example",
            ],
        },
        "not_contains": {
            "id": [
                "123e4567-e89b-12d3-a456-426614174000",
            ],
            "meta": {
                "created_by": [
                    "123e4567-e89b-12d3-a456-426614174000",
                ],
                "updated_by": [
                    "123e4567-e89b-12d3-a456-426614174000",
                ],
            },
            "external": {
                "source_id": [
                    "example",
                ],
                "source": [
                    "example",
                ],
            },
            "title": [
                "example",
            ],
            "description": [
                "example",
            ],
        },
        "like": {
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "title": "example",
            "description": "example",
        },
        "not_like": {
            "external": {
                "source_id": "example",
                "source": "example",
            },
            "title": "example",
            "description": "example",
        },
        "null": {
            "meta": {
                "created_by": True,
                "updated_at": True,
                "updated_by": True,
            },
            "external": {
                "source_id": True,
                "source": True,
            },
            "description": True,
        },
        "not_null": {
            "meta": {
                "created_by": True,
                "updated_at": True,
                "updated_by": True,
            },
            "external": {
                "source_id": True,
                "source": True,
            },
            "description": True,
        },
        "or_condition": True,
    }, limit=1, offset=0)

    while res is not None:
        # Handle items

        res = res.next()

```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Type                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Required                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | Example                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `filter_`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | [models.UnitSearchFilter](../../models/unitsearchfilter.md)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Filter criteria to search for specific records                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | {<br/>"equals": {<br/>"id": "123e4567-e89b-12d3-a456-426614174000",<br/>"meta": {<br/>"createdAt": "2024-01-15T10:30:00Z",<br/>"createdBy": "123e4567-e89b-12d3-a456-426614174000",<br/>"updatedAt": "2024-01-15T10:30:00Z",<br/>"updatedBy": "123e4567-e89b-12d3-a456-426614174000"<br/>},<br/>"external": {<br/>"sourceID": "example",<br/>"source": "example"<br/>},<br/>"title": "example",<br/>"description": "example"<br/>},<br/>"notEquals": {<br/>"id": "123e4567-e89b-12d3-a456-426614174000",<br/>"meta": {<br/>"createdAt": "2024-01-15T10:30:00Z",<br/>"createdBy": "123e4567-e89b-12d3-a456-426614174000",<br/>"updatedAt": "2024-01-15T10:30:00Z",<br/>"updatedBy": "123e4567-e89b-12d3-a456-426614174000"<br/>},<br/>"external": {<br/>"sourceID": "example",<br/>"source": "example"<br/>},<br/>"title": "example",<br/>"description": "example"<br/>},<br/>"greaterThan": {<br/>"meta": {<br/>"createdAt": "2024-01-15T10:30:00Z",<br/>"updatedAt": "2024-01-15T10:30:00Z"<br/>}<br/>},<br/>"smallerThan": {<br/>"meta": {<br/>"createdAt": "2024-01-15T10:30:00Z",<br/>"updatedAt": "2024-01-15T10:30:00Z"<br/>}<br/>},<br/>"greaterOrEqual": {<br/>"meta": {<br/>"createdAt": "2024-01-15T10:30:00Z",<br/>"updatedAt": "2024-01-15T10:30:00Z"<br/>}<br/>},<br/>"smallerOrEqual": {<br/>"meta": {<br/>"createdAt": "2024-01-15T10:30:00Z",<br/>"updatedAt": "2024-01-15T10:30:00Z"<br/>}<br/>},<br/>"contains": {<br/>"id": [<br/>"123e4567-e89b-12d3-a456-426614174000"<br/>],<br/>"meta": {<br/>"createdBy": [<br/>"123e4567-e89b-12d3-a456-426614174000"<br/>],<br/>"updatedBy": [<br/>"123e4567-e89b-12d3-a456-426614174000"<br/>]<br/>},<br/>"external": {<br/>"sourceID": [<br/>"example"<br/>],<br/>"source": [<br/>"example"<br/>]<br/>},<br/>"title": [<br/>"example"<br/>],<br/>"description": [<br/>"example"<br/>]<br/>},<br/>"notContains": {<br/>"id": [<br/>"123e4567-e89b-12d3-a456-426614174000"<br/>],<br/>"meta": {<br/>"createdBy": [<br/>"123e4567-e89b-12d3-a456-426614174000"<br/>],<br/>"updatedBy": [<br/>"123e4567-e89b-12d3-a456-426614174000"<br/>]<br/>},<br/>"external": {<br/>"sourceID": [<br/>"example"<br/>],<br/>"source": [<br/>"example"<br/>]<br/>},<br/>"title": [<br/>"example"<br/>],<br/>"description": [<br/>"example"<br/>]<br/>},<br/>"like": {<br/>"external": {<br/>"sourceID": "example",<br/>"source": "example"<br/>},<br/>"title": "example",<br/>"description": "example"<br/>},<br/>"notLike": {<br/>"external": {<br/>"sourceID": "example",<br/>"source": "example"<br/>},<br/>"title": "example",<br/>"description": "example"<br/>},<br/>"null": {<br/>"meta": {<br/>"createdBy": true,<br/>"updatedAt": true,<br/>"updatedBy": true<br/>},<br/>"external": {<br/>"sourceID": true,<br/>"source": true<br/>},<br/>"description": true<br/>},<br/>"notNull": {<br/>"meta": {<br/>"createdBy": true,<br/>"updatedAt": true,<br/>"updatedBy": true<br/>},<br/>"external": {<br/>"sourceID": true,<br/>"source": true<br/>},<br/>"description": true<br/>},<br/>"orCondition": true<br/>} |
| `limit`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | *Optional[int]*                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | The maximum number of Units to return (default: 50) when searching Units                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | 1                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `offset`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | *Optional[int]*                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | The number of Units to skip before starting to return results (default: 0) when searching Units                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | 0                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `retries`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Configuration to override the default retry behavior of the client.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

### Response

**[models.UnitSearchResponseResponse](../../models/unitsearchresponseresponse.md)**

### Errors

| Error Type                            | Status Code                           | Content Type                          |
| ------------------------------------- | ------------------------------------- | ------------------------------------- |
| errors.Error400ResponseBody           | 400                                   | application/json                      |
| errors.Error401ResponseBody           | 401                                   | application/json                      |
| errors.Error403ResponseBody           | 403                                   | application/json                      |
| errors.Error404ResponseBody           | 404                                   | application/json                      |
| errors.Error409ResponseBody           | 409                                   | application/json                      |
| errors.UnitSearch422ResponseBodyError | 422                                   | application/json                      |
| errors.Error429ResponseBody           | 429                                   | application/json                      |
| errors.Error500ResponseBody           | 500                                   | application/json                      |
| errors.MeitnerDefaultError            | 4XX, 5XX                              | \*/\*                                 |

## get

Retrieves the `Unit` with the given ID.

### Example Usage

<!-- UsageSnippet language="python" operationID="UnitGet" method="get" path="/unit/{id}" example="responseExample" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.units.get(id="123e4567-e89b-12d3-a456-426614174000")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | The unique identifier of the Unit to retrieve                       | 123e4567-e89b-12d3-a456-426614174000                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.UnitGetResponse](../../models/unitgetresponse.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| errors.Error400ResponseBody | 400                         | application/json            |
| errors.Error401ResponseBody | 401                         | application/json            |
| errors.Error403ResponseBody | 403                         | application/json            |
| errors.Error404ResponseBody | 404                         | application/json            |
| errors.Error409ResponseBody | 409                         | application/json            |
| errors.Error429ResponseBody | 429                         | application/json            |
| errors.Error500ResponseBody | 500                         | application/json            |
| errors.MeitnerDefaultError  | 4XX, 5XX                    | \*/\*                       |

## update

Update a Unit

### Example Usage: errorExample

<!-- UsageSnippet language="python" operationID="UnitUpdate" method="patch" path="/unit/{id}" example="errorExample" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.units.update(id="123e4567-e89b-12d3-a456-426614174000", title="Norra distriktet", external={
        "source_id": "12345678",
    }, description="Norra grundskole- och förskoleenheten")

    # Handle response
    print(res)

```
### Example Usage: requestExample

<!-- UsageSnippet language="python" operationID="UnitUpdate" method="patch" path="/unit/{id}" example="requestExample" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.units.update(id="123e4567-e89b-12d3-a456-426614174000", title="Norra distriktet", external={
        "source_id": "12345678",
    }, description="Norra grundskole- och förskoleenheten")

    # Handle response
    print(res)

```
### Example Usage: responseExample

<!-- UsageSnippet language="python" operationID="UnitUpdate" method="patch" path="/unit/{id}" example="responseExample" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.units.update(id="123e4567-e89b-12d3-a456-426614174000", title="Norra distriktet", external={
        "source_id": "12345678",
    }, description="Norra grundskole- och förskoleenheten")

    # Handle response
    print(res)

```
### Example Usage: validationError

<!-- UsageSnippet language="python" operationID="UnitUpdate" method="patch" path="/unit/{id}" example="validationError" -->
```python
from meitner import Meitner, models
import os


with Meitner(
    security=models.Security(
        option1=models.SecurityOption1(
            client_credentials=os.getenv("MEITNER_CLIENT_CREDENTIALS", ""),
            client_secret=os.getenv("MEITNER_CLIENT_SECRET", ""),
        ),
    ),
) as m_client:

    res = m_client.units.update(id="123e4567-e89b-12d3-a456-426614174000", title="Norra distriktet", external={
        "source_id": "12345678",
    }, description="Norra grundskole- och förskoleenheten")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                             | Type                                                                                                                                                                  | Required                                                                                                                                                              | Description                                                                                                                                                           | Example                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                                                                                  | *str*                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                    | The unique identifier of the Unit to update                                                                                                                           | 123e4567-e89b-12d3-a456-426614174000                                                                                                                                  |
| `title`                                                                                                                                                               | *str*                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                    | The title of the unit                                                                                                                                                 | Norra distriktet                                                                                                                                                      |
| `external`                                                                                                                                                            | [Optional[models.UnitUpdateExternal]](../../models/unitupdateexternal.md)                                                                                             | :heavy_minus_sign:                                                                                                                                                    | External is the External-object used on Update and Create operations, since it should only be allowed to set SourceID for the unit, the Source-field is not included. | {<br/>"sourceID": "12345678"<br/>}                                                                                                                                    |
| `description`                                                                                                                                                         | *OptionalNullable[str]*                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                    | The description of the unit                                                                                                                                           | **Example 1:** Norra grundskole- och förskoleenheten<br/>**Example 2:** null                                                                                          |
| `retries`                                                                                                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                      | :heavy_minus_sign:                                                                                                                                                    | Configuration to override the default retry behavior of the client.                                                                                                   |                                                                                                                                                                       |

### Response

**[models.UnitUpdateResponse](../../models/unitupdateresponse.md)**

### Errors

| Error Type                            | Status Code                           | Content Type                          |
| ------------------------------------- | ------------------------------------- | ------------------------------------- |
| errors.Error400ResponseBody           | 400                                   | application/json                      |
| errors.Error401ResponseBody           | 401                                   | application/json                      |
| errors.Error403ResponseBody           | 403                                   | application/json                      |
| errors.Error404ResponseBody           | 404                                   | application/json                      |
| errors.Error409ResponseBody           | 409                                   | application/json                      |
| errors.UnitUpdate422ResponseBodyError | 422                                   | application/json                      |
| errors.Error429ResponseBody           | 429                                   | application/json                      |
| errors.Error500ResponseBody           | 500                                   | application/json                      |
| errors.MeitnerDefaultError            | 4XX, 5XX                              | \*/\*                                 |